## Processing Pi


![Screen Shot 2020-10-12 at 11.11.20 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1602533405732/Fsk_Q0QUr.png)

Some of the first programs I wrote on the Apple II (in other words, some of the first programs I ever wrote), were different visualizable ways to calculate  [pi](https://en.wikipedia.org/wiki/Pi) , courtesy of a book on the history of pi that I found in the public library (between readings of scifi novels and Agatha Christie mysteries, my tastes were eclectic).

Recreating those programs hardly seemed worth all the setup that a simple Hello World requires these days, but I started playing with  [Processing](https://processing.org/)  the other day (another longstanding item on the checklist) and it seemed like the perfect platform for this type of thing.

There are many methods to choose from but probably the  [simplest]( https://academo.org/demos/estimating-pi-monte-carlo/ )  is to essentially throw darts at a square enclosing a circle. The number of darts in the circle divided by the total number of darts in the square approximates the circle area by the square area and that all should converge toward pi/4.

In Processing, I just typed in this code, hit Play to run and display the window above, and hit Export to deploy it on  [itch.io]( https://technicat.itch.io/processing-pi ) . Maybe I'll try  [Buffon's Needle](https://en.wikipedia.org/wiki/Buffon%27s_needle_problem) , next!

```
float total = 0.0;
float inside = 0.0;
float radius = 640.0;

PFont f;

float pi() {
  if (total == 0) {
    return 0;
  } else {
  return inside/total *4;
  }
}
  

void setup() {
  size(640,640);
  background(0);
  ellipse(radius/2,radius/2,radius,radius);
  f = createFont("Arial",16,true);
}

void draw() {
  float x = random(-radius,radius);
  float y = random(-radius,radius);
  total = total +1;
  if (x*x+y*y < radius*radius) {
    inside = inside+1;
  }
  fill(0);
  rect(0,0,100,40);
  fill(0,255,255);
  ellipse(x,y,5,5);
  fill(255,255,0);
  textFont(f,24);
  text(pi(),10,25);
}
``` 
