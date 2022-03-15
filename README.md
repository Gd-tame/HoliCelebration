# HoliCelebration
// C++ code


float error = 0;
float old = -99;
int count = 0;
void setup()
{
  Serial.begin(9600);
  pinMode(3,OUTPUT);
}
long readDistance(int trigPin, int echoPin){
	pinMode(trigPin,OUTPUT);
  	delay(2);
  digitalWrite(trigPin,HIGH);
  delay(10);
  digitalWrite(trigPin,LOW);
  pinMode(echoPin,INPUT);
  return pulseIn(echoPin,HIGH);
}
void loop()
{
	float new1 = 0.01723*readDistance(7,6);
  // Serial.print(new1);
//  Serial.println();
  float err = (new1 - old)/new1 * 100;
  if(err > 0.25 or err < -0.25){
    digitalWrite(3,HIGH);
    old = new1;
    count+=1;
    Serial.print(count);
    Serial.println();
  }
  else digitalWrite(3,LOW);
  delay(2000);
  

 
	
  
    
  //Serial.print(cm);
  //Serial.print("   ");
  //Serial.print(inches);
  //Serial.println();

  	
}
![image](https://user-images.githubusercontent.com/73153061/158345865-0bd69f39-9b86-44be-8dac-05898feb7a1f.png)
