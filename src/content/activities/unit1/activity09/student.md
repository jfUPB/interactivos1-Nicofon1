```
function setup() {
  createCanvas(400, 400);
  y = 150;
  x = 200;
  z = 1;
  w = 1;
  g=1;
  f=0;
  q=2;
  b=1;
}

function draw() {
  
  if(x >=250){z=-5;}
  else if(x <=150){z=+5; }
              
  x=x+z;
              
  if(y <=150){w=+5;}
  else if(y >=250){w=-5;}
  y=y+w;
  print(x,y);
  
  g=g*-1;
  
  background(220);
  fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - 200, y + mouseY - 250, 10, 10);
  
   fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - 200, y + mouseY - 150, 10, 10);
  
   fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - 250, y + mouseY - 200, 10, 10);
  
   fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - 150, y + mouseY - 200, 10, 10);
  
  fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - 150 + (50*g), y + mouseY - 250 + (50*g), 10, 10);
  
  fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - 250 - (50*g), y + mouseY - 150 - (50*g), 10, 10);
  
  
  
  
  
  if(q >=90){b=-0.1;}
  else if(q <=0){b=+0.1; }
              
  q=q+b;
  print(q);
  fill(random(0,250),random(0,250),random(0,250));
  ellipse((sin(q)*200)+200,(cos(q)*200)+200, 10, 10);
  
  
}
```


https://github.com/user-attachments/assets/299ac662-4b6e-46fe-92f0-3b65c3de630a


