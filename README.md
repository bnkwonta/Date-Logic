# Date-Logic
prints and counts set date and times, resolves times



class Date {
  final String [] days = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"};
  int today; 
  int hour;
  int minute;
  boolean before_noon;
  Date(int d, int h, int m, boolean beforeNoon) {
    if (d>6)
      d = d%7;
    if (h>12)
      h = h%12;
    if (m>59)
      m = m%60;
    today = d;
    hour = h;
    minute = m;
    before_noon = beforeNoon;
  }

  Date(Date mydate) {
    today = mydate.today;
    hour = mydate.hour;
    minute = mydate.minute;
    before_noon =  mydate.before_noon;
  }


  void addHour() {
    hour++;
    if(hour>12)
      hour = hour%12;
  }

  void addMinute() {
    minute++;
      if(minute>59){
        minute = minute%59;
        addHour();
  }
  }
  
  boolean equal(Date date) {
    if (today == date.today && hour == date.hour && minute == date.minute && before_noon == date.before_noon)
      return true;
    else
    return false;
  }
  String toString() {
    String date = days[today];
    if (hour <= 10)
      date += " 0" + hour;
    else
      date += " " + hour;

    if (minute  <= 10)
      date+= ":0" + minute;
    else
      date+= ":" + minute;

    if (before_noon)
      date+= "AM ";
    else 
    date+= "PM ";
    return date;
  }
}


void setup() {
    Date mydate;
    mydate = new Date (5, 12, 56, false);
    for (int i = 0; i<5; i++) {
      mydate.addMinute();
      println(mydate);
    }

    mydate = new Date (11, 12, 56, true);
    for (int i = 0; i<5; i++) {
      mydate.addHour();
      println(mydate);
    }

    Date d1 = new Date(3, 4, 5, true);
    Date d2 = new Date (d1);

    if (d1.equal(d2))
      println(d1 + " and " + d2 + " are equal...");
    else
      println( d1 + " and " + d2 + " are NOT equal...");

    d2.addHour();

    if (d1.equal(d2))
      println(d1 + " and " + d2 + " are equal...");
    else
      println(d1 + " and " + d2 + " are NOT equal...");
  }
