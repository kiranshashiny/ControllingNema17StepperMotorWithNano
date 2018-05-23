# Controlling Stepper Motor and direction of movement using an Arduino Nano

This blog is about how to control the Stepper Motor ( In this case it is a Nema17 12V DC class of a motor) 

The code is simple and so is the connections to the Motor.

## Prerequisites :

Arduino Nano -1
Nema 17 Class of Stepper Motor -1
A4988 Motor driver -1
Arduino IDE to compile and Upload the code.
12V DC Wall adapter -1 
5V DC Wall adapter -1 


To avoid any accidental burnouts- I used 2 separate wall adapter power supplies 
The 12V powered the Stepper Motor and the 5V controlled the A4988 Motor Driver.


## Basics 

Any motor cannot be connnected directly to the Nano as one might fear it will damage the Microcontroller.

To avoid a burnout a motor driver is required that will get inputs from the Nano on one end and output the direction and the speed at which the motor will turn on the other side.

The Nema stepper motor is a 4 wire bipolar motor.


More on this can be got from this link.

https://howtomechatronics.com/tutorials/arduino/how-to-control-stepper-motor-with-a4988-driver-and-arduino/



		
		const int stepPin = 3; 
		const int dirPin = 4; 
		 
		void setup() {
		  // Sets the two pins as Outputs
		  pinMode(stepPin,OUTPUT); 
		  pinMode(dirPin,OUTPUT);
		}
		void loop() {
		  digitalWrite(dirPin,HIGH); // Enables the motor to move in a particular direction
		  // Makes 200 pulses for making one full cycle rotation
		  for(int x = 0; x < 200; x++) {
		    digitalWrite(stepPin,HIGH); 
		    delayMicroseconds(500); 
		    digitalWrite(stepPin,LOW); 
		    delayMicroseconds(500); 
		  }
		  delay(1000); // One second delay
		  
		  
		  digitalWrite(dirPin,LOW); //Changes the rotations direction
		  for(int x = 0; x < 200; x++) {
		    digitalWrite(stepPin,HIGH); 
		    delayMicroseconds(500); 
		    digitalWrite(stepPin,LOW); 
		    delayMicroseconds(500); 
		  }
		  delay(1000); // One second delay
		
		}



![img_20180523_115842](https://user-images.githubusercontent.com/14288989/40407324-ab803250-5e81-11e8-8f04-627a55501c20.jpg)

![img_20180523_115913](https://user-images.githubusercontent.com/14288989/40407325-abab4940-5e81-11e8-8132-d1121b88573f.jpg)

![img_20180523_115935](https://user-images.githubusercontent.com/14288989/40407326-abd41104-5e81-11e8-85b7-e12b74cd328d.jpg)



A4988 Motor Driver

![screen shot 2018-05-23 at 12 08 44 pm](https://user-images.githubusercontent.com/14288989/40407437-137d08ce-5e82-11e8-8994-b049cae6347b.png)

Wiring Diagram:
![screen shot 2018-05-23 at 12 09 29 pm](https://user-images.githubusercontent.com/14288989/40407458-3269a9ae-5e82-11e8-803d-d4cb748399e7.png)



### Additional information :

https://howtomechatronics.com/tutorials/arduino/how-to-control-stepper-motor-with-a4988-driver-and-arduino/

### Things I learnt:

The pot on the A4988 can be adjusted to make the motor run smoother, or to reduce the jitters.

It is better to source the 5V power supply to the Motor Driver from an external source than the Nano ! as it might burn the Nano.
