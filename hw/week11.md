### Homework 11 (for Wednesday, April 15, 2015)

This homework has two parts: first, a programming assignment, and second, to acquire any materials you need for your project (to bring to class next Wednesday, April 15).

Make the following changes to the code we wrote in class (see below) and **[send it to me](mailto:jzamfirescupereira@cca.edu) by Tuesday night, 11pm**:
- Increase the spacing between the balls in the grid to `30` pixels.
- Make it so new balls are added to the list when the mouse is moved rather than pressed. (Hint: you may find helpful the `mouseMoved()` function...)
- Modify the `draw` function inside the `Ball` class so that the balls are black if the mouse is pressed. (Hint: you may find helpful the `mousePressed` variable that's built in to Processing...) Don't change anything outside the `draw` function in the `Ball` class!
  
        class Ball {
          float x, y;
          float vx, vy;
          float size = 10;
          color c;
  
          Ball(float x, float y, color c) {
            this.x = x;
            this.y = y;
            this.c = c;
            vx = random(1);
            vy = random(1);
          }
  
          void draw() {
            noStroke();
            fill(c);
            ellipse(x, y, size*2, size*2);
          }
  
          void move() {
            x += vx;
            y += vy;
            if (x < size || x > width-size) {
              vx = -vx;
            }
            if (y < size || y > height-size) {
              vy = -vy;
            }
          }
        }

        ArrayList<Ball> list;

        void setup() {
          size(500, 500);
          colorMode(HSB);
          list = new ArrayList<Ball>();

          for (int x = 20; x < width - 20; x += 20) {      
            for (int y = 20; y < height - 20; y += 20) {
              list.add(new Ball(x, y, color(random(255), 255, 255)));
            }    
          }
        }

        void draw() {
          background(255);
  
          for (int i = 0; i < list.size(); i += 1) {
            list.get(i).draw();
            list.get(i).move();    
          }
        }

        void mousePressed() {
          list.add(new Ball(mouseX, mouseY, color(random(255), 255, 255)));
        }

For your project:
- Draft a "Bill of Materials" for your project: this is a list of the components you'll need to build your project. Each entry in the list should include a description, and a "source": where you'll get the part -- a link if you plan to buy it, or "Hybrid Lab" if the lab has one you plan to use, but please confirm in the lab that the part is available! 
  
  **[Send me your Bill of Materials](mailto:jzamfirescupereira@cca.edu) by Monday night, 11pm**.

- **Acquire all the parts on your Bill of Materials and bring them with you to the next class!** (In addition to your laptop, Arduino, etc.)