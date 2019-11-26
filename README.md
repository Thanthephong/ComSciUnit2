# ComSciUnit2

Binomial and morse
===================



Contents
-----
  1. [Planning](#planning)
  1. [Design](#design)
  1. [Development](#development)
  1. [Evaluation](#evaluation)
  
  
 
Planning
----------
The topic is called Martian Decoder. The year is 2050. Planet exploration is a thing, however, communication is still precarious. The station in the Earth can only communicate using Morse code, the station in the Moon can only communicate in Binary code. Communication with the station in Mars must be provided. Basically what we have to do is work with binary and morse programming: provide a communication system that allow stations to communicate seamlessly using English, but the Keyboard input on each station is limited to 2 push buttons.

This is a very new topic for us. Working with binary and morse code, using a different programming language, and working the with arduino set. At first, we were quite anxious but also very excited about getting to build and program a system. And the first thing I did was to get to know how to build the system, get familiar with arduino programming language, and also how too assemble, connect the lights, buttons, resistors to the arduino Uno3 board.


Design
---------
There is not much for designing in this topic, as we already got use to the loops and also we don't really use them that much in the chapter, so no flow chart needed. Theres a very helpful website for preparing the curcuit, design the system and also programming the code before actually building it using the arduino set: Tinkercad.com
![Tinkercad](Tinkercad.png)

As you can see, we can add the arduino board, add different parts and engines to it. Not only that, we can also code and basically set up for the whole system before actually using the physical arduino set. The purpose of this is to see if the program is working correctly, if it needs fixing. Before building on the school's arduino set, we always use tinkercad as it is a lot easier to debugg programs, to check if we plugged in something wrong right. For example: if we forget to plug the resistors for the LED lights, the light will burn; but on tinkercad, it reminds you that you should plug it in, which is very helpful. Usually, after getting everything set up, and run several tests that shows expected results, I start working on the 
arduino set, and it is even easier because we can refer to the tinkercad circuit and do everything the same. In the end, it is a very useful and convenient program.

**Usability and HCD***
Usability is according to Techopedia [1] the degree of ease with which a product can be used to achieve their goals. Elegance, clarity, intuitive.

Human-centered design [also Human-centred design, as used in ISO standards] is an approach to problem solving, commonly used in design and management frameworks that develops solutions to problems by involving the human perspective in all steps of the problem-solving process [2]

[1] “Usability retrieved from https://www.techopedia.com/definition/4919/usability ( 25 Nov 2019 )
[2] POSMER J, MARS R. “ It’s not you, bad doors are everywhere” 2016. Retrieved ( 25 Nov 2019 )



Development
--------

### 1. Practice with traffic light
  This is the first thing we did that is related to arduino. We had to watch a video on youtube on how to build a traffic light for homework, and start building it and coding it by ourselves.
  ![Traffic](Traffic.png)
 ````.c
 int red = 10;
int yellow = 9;
int green = 8;

  // put your setup code here, to run once:
  void setup(){
    pinMode(red, OUTPUT); 
    pinMode(yellow, OUTPUT);
    pinMode(green, OUTPUT);
digitalWrite(green, HIGH);
}


void loop() {
 // green off, yellow on for 3 seconds
    digitalWrite(green, LOW);
    digitalWrite(yellow, HIGH);
    delay(3000);

    // turn off yellow, then turn red on for 5 seconds
    digitalWrite(yellow, LOW);
    digitalWrite(red, HIGH);
    delay(5000);

    // red and yellow on for 2 seconds (red is already on though)
    digitalWrite(yellow, HIGH);
    delay(2000);

    // turn off red and yellow, then turn on green
    digitalWrite(yellow, LOW);
    digitalWrite(red, LOW);
    digitalWrite(green, HIGH);
    delay(3000);
    
}
````
  We program and set up mostly everything on Tinkercad.com first before actually using the arduino set to make it. Tinkercad is an online arduino simulation, both setting up the board and coding. This helps us to make sure everything is working perfectly, and also debugging problems if needed. And then when we are done with tinker cad, we use the school's arduino set to set up the actual traffic light ( as we know that it is working normally on tinker cad, we will know that if we do the same thing with the set it should be working normally ). 
  
  The code itself works very easily, what digitalWrite LOW and HIGH is is to turn on and off the lights, delay is to wait for a specific amount of miliseconds before performing the next task. As we learned bash language, modern C ( arduino ) coding seems to be much easier as we already know the concept, how to do things, it is just the code that is written in a different way. This is the traffic light with the actual arduino set:
 
 ![TrafficLight](TrafficLight.gif)
  
### 2. Bash and Arduino comparison

  Using the For loops practices that we were given to do on bash, no we are doing it again but with the arduino code. It turns out that there is actually no major differences between the 2 programming language. Here is a coding excersise but it's programming on both of the languages: print out the first 1000 numbers that is divisible by 7.
  
  **For bash:**
````.sh
#!/bin/bash
i=0
for ((n=1;n<=1000;n++))
do
  echo -n $i
  ((i=i+1))
  if [ $i -eq 7 ]; then
    i=0
  fi
done
````
  **For arduino:**
````.c
void setup()
{
  Serial.begin(9600);
  int i=0;
  for (int n=1; n<=1000; n++) {
    Serial.print(i);
     i = i + 1;
    if ( i == 7 ) i=0;
  }
}

void loop()
{
}
````

As you can see, the 2 programs are very similar to each other. The For loop, the If commands works the same way, just some changes in how you write it down. For bash, you don't need to define the variable before start using it, but in Arduino, you have to. Another advantage of bash is we don't need to use ";" ( semicolons ) in our program. In arduino, you have to use it at the end of every command, which can be very annoying for debugging sometimes as you might forget to put it there. Arduino programming language is specialized to program for the board for it to do work, so if we want to use the terminal, we have to have a command to start it first. The terminal is a very helpful function of arduino, especially for finding mistakes in the program or checking what the output sent to the Uno3 board is. 

````.c
void setup() {
}

void loop() {
}
````

This is probably where arduino and bash differs the most. So what is void? Void is basically a type of function that only perform the task inside but doesn't return any value. 
A very interesting and super useful function is the void loop() function. With the void setup command, every code that is put inside of it, when we start the program, only run once, just like the bash program itself. But using the loop, all the codes are repeated forevery unless we press the stop program button. That is why in the traffic light program above, once we press start, all the code in the loop will run, making the traffic lights to consistently turning on and off without having to pressing start again. This is very helpful and significant what arduino gives us

### 3. Binary counting 

After getting familiar with how arduino programming and boarding works, we moved on to some harder tasks: Binary counting using Arduino language. But before that, we learned out to change from decimal to binary. 

**Mathematically, how we convert from decimal to binary is:**

- Write down the decimal number.
- Divide the number by 2.
- Write the result underneath.
- Write the remainder on the right hand side. This will be 0 or 1.
- Divide the result of the division by 2 and again write down the remainder.
- Continue dividing and writing down remainders until the result of the division is 0.
- The most significant bit (MSB) is at the bottom of the column of remainders and the least significant bit (LSB) is at the top.
- Read the series of 1s and 0s on the right from the bottom up. This is the binary equivalent of the decimal number. Here is an outline flow chart for a program to do it:
 
 ![FlowChart](FlowChart.png)
 
 **This the arduino program that gives output from 0 to 15 in binary**
  
 ![Arduinodecimaltobinary](Arduinodecimaltobinary.png)
 
 ````.c
 int i=0;
void setup()
{
  pinMode(9, OUTPUT);
  pinMode(10,OUTPUT);
  pinMode(11,OUTPUT);
  pinMode(12,OUTPUT);
  for (i=0; i<=15; i++) {
    if ( i % 2 > 0 ) {
      digitalWrite(9,HIGH);
    }
    if ( i % 4 > 1 ) {
       digitalWrite(10,HIGH);
    }
    if ( i % 8 > 3 ) {
       digitalWrite(11,HIGH);
    }
    if ( i % 16 > 7 ) {
      digitalWrite(12,HIGH);
    }
    delay(1000);
     digitalWrite(9,LOW);
     digitalWrite(10,LOW);
     digitalWrite(11,LOW);
     digitalWrite(12,LOW);
    delay(200);
        
  }
    
}

void loop()
{
}
````
This program gives the output of the first 16 decimals in binary. To understand how this works, first we should look at the decimal to binary table:
![Table](Table.png)

We can actually see a pattern from the binary side of the table:
- 4th column: 0 and 1 switches every time ( 0 1 0 1 )
- 3rd column: 0 and 1 switches every 2 times ( 0 0 1 1 0 0 )
- 2nd column: 0 and 1 switches every 4 times ( 0 0 0 0 1 1 1 1 )
- 1st column: 0 and 1 switches every 8 times ( 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 )

From that, we can easily write the code as we have found the pattern between those binary numbers, just like the code above.
This is the actual system using the arduino set:

![DecimalToBinary](DecimalToBinary.gif)

### 4. Different types of variables in Arduino
 In Arduino, there are various types of variables that can store different valus. That is why we have to define that variable type before start working with it, unlike bash. 
 
 ![ArduinoVariables]( ArduinoVariables.jpg)
 
 The reason we should assign the variables is to increase the efficiency for the computer's RAM. Because for example, if we want a variable that can store only 1 or 0 to display binary, there is no need to use float or word for it, we can just use boolean, which is more efficient for the computer.
 
 ### 5. Binary gates
  Binary gates is a quite complicated topic. It is basically an idealized or physical device implementing a Boolean function; that is, it performs a logical operation on one or more binary inputs and produces a single binary output. These mostly all the commands and equation of logic gates: 

![logic-gates](logic-gates.png)

This is the example for the output that each of the gates give

![2-Figure1-1](2-Figure1-1.png)

This is very helpful because for instance we work with a list of inputs 2 buttons or more, instead of having to use several lines of IF commands, we can summarize it on 1 line using only one equaion. It is very hard to fully understand and get use to doing it, it involves:
* Putting the input and output into a specific type of table
* Work out the equation for individual terms
* Putting those terms together to create the complete equation
* Transform the equation from math language into programming language

For example, I used one coding exercise and try to use it 2 ways: manually and uing binary gates, the question is to create the output with the following inputs:
![Homework](Homework.png)

**The normal way of doing it:**
````.c
int decimal;
void loop()
{
 decimal = digitalRead(butA)*pow(2,1);
 decimal += digitalRead(butB)*pow(2,0);
  
 if (decimal == 0) {
    digitalWrite(led1, HIGH);
   	digitalWrite(led2, LOW);
  }
  if (decimal == 1 || decimal == 2) {
    digitalWrite(led1, LOW);
    digitalWrite(led2, HIGH);
  }
  if (decimal == 3) {
    digitalWrite(led1, HIGH);
    digitalWrite(led2, HIGH);
  }
  
}
````
What I did here was at first I convert the binary into decimal so that it is easier to work with, and then from then use if as a condition to get specific outcomes.

**Using binary gates:**
````.c
void loop()
{
	bool A = digitalRead(butA);
  	bool B = digitalRead(butB);
  	bool eq1 = (!A & !B) | (A & B);
  	bool eq2 = B | A;
  	digitalWrite(led1, eq1);
  	digitalWrite(led2, eq2);
}
````
As you can see, it is a lot shorter. It can actually be written in 2 lines of code only, but because I want to keep it organized, I assigned name for each value and equation so it is easier to understand. The symbols "!", "&","|"... are the logic gates, it represents NOT, AND, OR,... So basically, it works the same as all the if commands but put into a very simplified line, thats what makes binary gates so convenient when utilized.

### 6. Presenting numbers using LEDs
We are currently working on how to show a number by pressing buttons. Like the number you see in calculators, timers,... are all programmed this way, and we will find out how it works.

![UntidyTerrificKarakul-small](UntidyTerrificKarakul-small.gif)

We have made an input and output table for the inputs and outputs. Basically, the buttons will display number from 1 to 7. This is the table:



### 7. Designing input system for 2 buttons



 

 
 


  

Evaluation
-----------
