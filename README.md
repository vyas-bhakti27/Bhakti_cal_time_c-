// c++ code of calculating the time

#include<iostream>
#include<ctime>
#include<cstdlib>
#include<unistd.h>
using namespace std;
class Time
{
public:
 int hour,mint,sec;

void setTime(){
time_t tt;
// reading current time as per IST
 struct tm *ti;
 time(&tt);
 ti=localtime(&tt);
 hour=(5+ti->tm_hour)%24;
 mint=30+ti->tm_min;
 sec=ti->tm_sec;
}

Time getTime(){
 Time temp;
 temp.hour=hour;
 temp.mint=mint;
 temp.sec=sec; 
 return temp;
}

Time sleepTime(Time napTime, Time wakeup){
 Time temp;
 temp.hour=wakeup.hour - napTime.hour;
 temp.mint=wakeup.mint - napTime.mint;
 temp.sec=wakeup.sec - napTime.sec;
 return temp;
}
};

int main(){
 Time t1,t3;
 Time timeatSleep, timeatWake;
 t1.setTime();
 t3.getTime();
 cout << "Values return from getTime\n";
 cout << "Hour: " << t3.hour << "Mint: " << t3.mint <<"sec: "<< t3.sec << endl;
 cout << "Calculating sleep time" << endl;

// read the time before sleep
 t1.setTime();
 timeatSleep=t1.getTime();
// goto sleep
 sleep(5);
// read the time after waking up
 t1.setTime();
 timeatWake= t1.getTime();
// find the diffrence

return 0;
}
