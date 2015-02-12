### Homework 3 (due Wednesday February 11, 2015)

1. Prepare for our Arduino and electronics sessions by:
  - **Assignment: Read these tutorials:**
    - https://learn.sparkfun.com/tutorials/what-is-electricity
    - https://learn.sparkfun.com/tutorials/voltage-current-resistance-and-ohms-law
    - http://www.allaboutcircuits.com/vol_1/chpt_1/index.html
    - http://www.allaboutcircuits.com/vol_1/chpt_2/index.html 
  - Watch these videos:
    - https://www.youtube.com/watch?v=exlRjDKHGRg
    - https://www.youtube.com/watch?v=mzSnz6ZDkFE

2. Programming Practice:
  - Pick two additional sketches from [last week's list of 15](#homework-2-due-wednesday-february-4-2015) and create them in Processing.
  - In the Pulsed Lines sketch below, try the following changes:
      - Change the phase increase (currently 0.17) so that each pulse takes up the full width of the canvas.
      
      - Color the lines rainbow-style, like in [homework 2](hw2.md), exercise 4; have the color start over from red when you click; have the color fade to white as the pulse height drops to 0.

      - Use `rect` instead of `line`.
    ```
    /**
     * Pulsed Lines
     *
     * Click to pulse.
     */ 
    float amplitude, phase;

    void setup() {
      size(500, 500);
      background(0);
      amplitude = height * .9;
      phase = PI/8;
    }

    float x = 0;

    void draw() {
      stroke(0);
      strokeWeight(3);
      line(x, 0, x, height);
  
      float magnitude = amplitude/2 * sin(phase);
      stroke(255);
      strokeWeight(2);
      line (x, height/2-magnitude, x, height/2+magnitude);
  
      x = x + 5;
      amplitude = amplitude * 0.97;
      phase = phase + 0.17;
  
      if (x > width) {
        x = 0;
      } 
    }

    void mousePressed() {
      amplitude = height * .9;
      phase = PI/8;
    }
    ```
    
  - Load the PolygonPShape example, and modify it to draw a 7-pointed star instead of a 5-pointed one: 
    ```
    /**
     * PolygonPShape. 
     * 
     * Using a PShape to display a custom polygon. 
     */

    // The PShape object
    PShape star;

    void setup() {
      size(640, 360, P2D);
      smooth();
      // First create the shape
      star = createShape();
      star.beginShape();
      // You can set fill and stroke
      star.fill(102);
      star.stroke(255);
      star.strokeWeight(2);
      // Here, we are hardcoding a series of vertices
      star.vertex(0, -50);
      star.vertex(14, -20);
      star.vertex(47, -15);
      star.vertex(23, 7);
      star.vertex(29, 40);
      star.vertex(0, 25);
      star.vertex(-29, 40);
      star.vertex(-23, 7);
      star.vertex(-47, -15);
      star.vertex(-14, -20);
      star.endShape(CLOSE);
    }

    void draw() {
      background(51);
      // We can use translate to move the PShape
      translate(mouseX, mouseY);
      // Display the shape
      shape(star);
    }
    ```
