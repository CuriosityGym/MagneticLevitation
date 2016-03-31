#include <PID_v1.h>

double Setpoint, Input, Output;
//int sensorvalue= 0;
//int pwmvalue = 80;

//int mag_max_on = 530;
//int mag_max_off = 500;

//int mag_min_on = 500;
//int mag_min_off = 480;

PID myPID(&Input, &Output, &Setpoint,8,2,5, REVERSE);

void setup() {
  // put your setup code here, to run once:
  pinMode(A5, INPUT);
  pinMode(9, OUTPUT);
  //Serial.begin(115200);
  analogWrite(9, 60);
  Setpoint = 450;
  myPID.SetMode(AUTOMATIC);
  myPID.SetOutputLimits(0, 150);
  myPID.SetSampleTime(10);
}

void loop() {
  // put your main code here, to run repeatedly:
  Input=analogRead(A5);
  //Serial.println(sensorvalue);
  //if( sensorvalue<720 || sensorvalue>=770 )
  //{
    //pwmvalue=10;
  //}
  //else
  //{
    /*if( sensorvalue>=mag_max_off && sensorvalue<mag_max_on )
    {
      pwmvalue=200;
    }
    else
    {
      if( sensorvalue>=mag_min_off && sensorvalue<mag_min_on )
      {
        pwmvalue=0;
      }
      else
      {
        pwmvalue=80;
      }
    }*/
  //}
  //Serial.print("Pwm");
  myPID.Compute();
  analogWrite(9, Output);
  //Serial.println(Output);
  //Serial.print("Input");
  Serial.println(Input);
}
