### Homework 10 (for Wednesday, April 8, 2015)

This homework has two parts: a programming assignment and a project proposal.

- Modify the code we wrote in class (see below) to add a second ball object, called `b2`. Then modify the code to use a random initial `vx` and `vy`. [Email me](mailto:jzamfirescupereira@cca.edu) this code **by Tuesday night at 11pm.**
  
        class Ball {
          float x, y;
          float vx, vy;
          float radius;
    
          Ball() {
            x = random(width);
            y = random(height);
            radius = 10;
            vx = 3;
            vy = 2;
          }
    
          void draw() {
            ellipse(x, y, radius*2, radius*2);
          }
    
          void move() {
            x = x + vx;
            y = y + vy;
            if (x < radius || x > width-radius) {
              vx = -vx;
            }
            if (y < radius || y > height-radius) {
              vy = -vy;
            }
          }
        }
    
        Ball b;
    
        void setup() {
          size(500, 500);
    
          b = new Ball();
        }
    
        void draw() {
          background(255);
    
          b.draw();
          b.move();
        }

- Write a proposal for your final project, and **[send it to me](mailto:jzamfirescupereira@cca.edu) by Monday night, 11pm** It should include at least these four sections: 
  - **Summary**: A few paragraphs (half a page?) or so describing the goals of your project. Include what types of inputs/outputs/data it will use, and how it will be interactive or responsive to the environment.
  - **Component Parts**: From what pieces will you build your project? Will you build or buy those pieces?
  - **Challenges**: What do you anticipate will be the hardest and most time-consuming parts?
  - **Project Timeline**: What parts of the project do you anticipate you will complete in each of the next 5 weeks?