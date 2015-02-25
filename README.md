# CCA Programming & Electronics, Spring 2015

This course repository contains homework assignments, useful guides, and code for "Programming & Electronics" at CCA, Spring 2015.

### Week 1: Wednesday, January 21, 2015

Lecture:
- Inspirational Videos
- Introductions
- Goals & course details

Hands-on:
- Human Embodiment of Programmer & Robot
  - Programs generally run line-by-line.
  - While loops, if statements, and functions break that up.
- A quick look at the Remote Control Robot code

Videos:
- Basic robots
  - [Coffee-can robot](http://www.youtube.com/watch?v=b0mIshBIbvI#t=24)
  - [Tree-climbing robot](http://www.youtube.com/watch?v=zkpH1BjD6Wc)
  - [Self-balancing robot](http://www.youtube.com/watch?v=Tw9Jr-SPL0Y)
  - [Insect robot](http://www.youtube.com/watch?v=tOsNXg2vAd4#t=120)
  - [Treadbot](http://www.youtube.com/watch?v=YblSltHDbIU)
  - [Velociraptor robot](http://www.youtube.com/watch?v=lPEg83vF_Tw)
- Drink-makers
  - [Textspresso](http://www.youtube.com/watch?v=kx9D74t7GD8#t=89)
  - [The Inebriator](http://www.youtube.com/watch?v=WqY7fchs7H0)
- Art bots
  - [Floating Couch](http://vimeo.com/72826106)
  - [Wooden Segment Mirror](https://www.youtube.com/watch?v=BZysu9QcceM#t=36)
  - [Cubli: Floating Cube](https://www.youtube.com/watch?v=n_6p-1J551Y)
  - [Arc-o-matic](http://vimeo.com/57082262#at=130)
  - [Robo Faber](http://vimeo.com/78771257)
  - [Eggbot](https://www.youtube.com/watch?v=w4cdbV2oaEc)
- Computer Numerical Control (CNC)
  - [Shapoko / tinyg](http://www.youtube.com/watch?v=pCC1GXnYfFI#t=11)
  - [Makerbot Replicator](http://www.youtube.com/watch?v=NAbiAzYhTOQ)
- Music
  - [Laser harp](http://www.youtube.com/watch?v=sLVXmsbVwUs#t=20)
- Vacuuming
  - [Roomba](https://www.youtube.com/watch?v=0DNkbZvVYvc)

[Homework for Week 1](hw/week1.md)

### Week 2: Wednesday, January 28, 2015

Lecture:
- Homework Review

Lab:
- Creating sketches. Write code to create the following sketches in Processing:

1. ![one](img/one.png)

2. ![two](img/two.png)

3. ![three](img/three.png)

4. [![four](img/four.png)](http://www.youtube.com/watch?v=jWNXFlGHuPA)

5. ![five](img/five.png)

6. Look through the [Processing reference](http://processing.org/reference). Pick a function, and use it in a new sketch of your own choosing.

[Homework for Week 2](hw/week2.md)
   
### Week 3: Wednesday, February 4, 2015

Lecture:
- Homework Review

Lab:
- Arrays
- More Processing sketches

[Homework for Week 3](hw/week3.md)

### Week 4: Wednesday, February 11, 2015

Lecture:
- Arduino! 
- Electronics!

Lab:
- Working with electronics

[Homework for Week 4](hw/week4.md)

### Week 5: Wednesday, February 18, 2015

Lecture:
- Schematic how-to.
  - See [Make's guide to building a breadboard from a schematic](http://makezine.com/2012/04/02/going-from-schematic-to-breadboard/)
  - Also see [Paul Spinrad's guide to reading schematics](http://blog.makezine.com/archive/2011/01/reading-circuit-diagrams.html) and [Collin's video version](http://makezine.com/2011/11/15/collins-lab-schematics/)

Lab:
-   Start with example AnalogInOutSerial (File > Examples > Analog > AnalogInOutSerial). Here's a simplified version of that code:
    ```arduino
    const int analogInPin = A0;  // Analog input pin that the potentiometer is attached to
    const int analogOutPin = 9; // Analog output pin that the LED is attached to

    int sensorValue = 0;        // value read from the pot
    int outputValue = 0;        // value output to the PWM (analog out)

    void setup() {
      // initialize serial communications at 9600 bps:
      Serial.begin(9600);
      pinMode(analogOutPin, OUTPUT);
    }

    void loop() {
      // read the analog in value:
      sensorValue = analogRead(analogInPin);            
      // map it to the range of the analog out:
      outputValue = map(sensorValue, 0, 1023, 0, 255);  
      // change the analog out value:
      analogWrite(analogOutPin, outputValue);           

      // print the results to the serial monitor:
      Serial.print("sensor = " );                       
      Serial.print(sensorValue);      
      Serial.print("\t output = ");      
      Serial.println(outputValue);   

      // wait 2 milliseconds before the next loop
      // for the analog-to-digital converter to settle
      // after the last reading:
      delay(2);                     
    }
    ```
    Make sure you understand what this code does. If not, ask! Here's a schematic of what your circuit should look like:
    
    ![potentiometer and LED on pin 9](img/pot-led-pin-9.png)
    
    Open the serial monitor and see what numbers are printed when you rotate the potentiometer. What's the lowest number you see? Highest?
    
    1. Modify the code so that instead of changing the brightness of the LED, the Arduino turns on or off the LED (using `digitalWrite` instead of `analogWrite`) depending on whether `outputValue` is greater or less than `127`. (Hint: You'll need an `if` statement. What's the `if` statement's condition?)

    2. Add 3 more LEDs (4 total) on pins 10, 11, and 12. (Create new variables for the pins they're connected to.) Here's a new schematic:
       ![potentiometer and LEDs on pins 9, 10, 11, and 12](img/pot-led-pins-9-10-11-12.png)
    
    3. Add new `if` statements so that the 4 LEDs make a "level meter": as you turn the potentiometer from left to right, the LEDs turn on one by one until they're all on when you've turned the potentiometer all the way.
    
    4. Replace the potentiometer in this circuit with a light-dependent resistor (LDR) in a voltage divider circuit. Here's what you should have:
    
       ![LDR and LEDs on pins 9, 10, 11, and 12](img/ldr-led-pins-9-10-11-12.png)
      
       What happens when you cover the LDR?
       
       Open the serial monitor and see what numbers are printed when you cover and uncover the LDR. What's the lowest number you see? Highest?
    
    5. *Show me your breadboard before moving on.*
    
    6. Replace your LDR with a button. Here's what you should have:
    
       ![Button and LEDs on pins 9, 10, 11, and 12](img/switch-led-pins-9-10-11-12.png)
    
       What happens?
       
       Open the serial monitor and see what numbers are printed when you push and release the button. What's the lowest number you see? Highest?
    
-   Use Arduino and Procesing function to create a digital [Etch-a-Sketch](https://www.youtube.com/watch?v=CAGcFy6CYnM#t=120s). 
    
    1. Connect two potentiometers to analog pins `A0` and `A1`. Here's a schematic:
    
       ![two potentiometers](img/two-pots.png)
    
    2. Write an Arduino sketch, using the `Serial` library, that reads the two analog inputs (using `analogRead`) and prints those values to serial port, two per line, separated by commas. The outputs should look like this in the serial monitor:

       ```
       253,124
       253,176
       253,182
       ...
       ```
    
       You will likely need both `Serial.print` and `Serial.println`. The first number should correspond to the value from pin `A0`, and the second from pin `A1`.
    
    3. Here's a Processing sketch that reads these pairs of numbers from the serial port, and then draws a line from the old coordinate to the new coordinate. But it has a bug! So it doesn't quite work. Fix the bug. (Hint: the bug isn't with the `readSerial` function!)
    
       ```processing
       // Etch-a-Sketch
       // based on a sketch by Trevor Shannon

       import processing.serial.*;

       Serial port;
       int oldX = -1;
       int oldY = -1;

       void setup() {
         size(512, 512);
         background(255);
         port = new Serial(this, Serial.list()[Serial.list().length-1], 9600);  
       }

       void drawNextLine(int x, int y) {
         if (oldX >= 0 && oldY >= 0) {
           // draw a line from the old x,y coordinates to the new x,y coordinates
           line(x, y, oldX, oldY);
         }

         // update the "old" x,y coordinates for the next frame
         oldX = x;
         oldY = x;
       }  

       void draw() {
         int[] values = readSerial(2);
         if (values != null) {
           drawNextLine(values[0], values[1]);
         }
       }

       void mouseClicked() {
         background(255);
       }

       int[] readSerial(int minValues) {  
         int x; int y;
         String s = port.readStringUntil('\n');
         if (s != null) {
           String[] parts = s.substring(0, s.length()-2).split(",");
           int[] values = new int[parts.length];
           for (int i = 0; i < parts.length; i++) {
             values[i] = int(parts[i]);
           }
           if (values.length < minValues) {
             return null;
           } else {
             return values;
           } 
         } else {
           return null;
         }
       }
       ```
    
    4. Modify the Processing code so that it draws a graph of the value of the second coordinate only (that is, the number that changes when you rotate the potentiometer that you've connected to pin `A1`).
       
       You'll need to modify the `drawNextLine` function so that it doesn't draw a line from `x`,`y` to `oldX`,`oldY` anymore. Instead, it will use a slowly-increasing `x` coordinate. Create a new variable called `columnPosition` and use that instead of `x` in the `line` function. Then increase `columnPosition` a little bit on every frame.
    
    5. **Challenge**: Also graph the value of the first coordinate!
  
  Homework: Practice programming and finish homework 4 if you haven't yet! (Especially the code tracing exercise.)