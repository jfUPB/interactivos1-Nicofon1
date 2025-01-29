function setup() {
  createCanvas(400, 400);
  y = 150;
  x = 200;
  z = 1;
  w = 1;
  g=1;
  f=0;
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
  
  
  
  fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - 100 + (100*g), y + mouseY - 300 + (100*g), 10, 10);
  
  fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - 300 - (100*g), y + mouseY - 100 - (100*g), 10, 10);
  
  f = 0;
  while (f<20){
    
    
    p = 0;
    while (p<20){
      
    fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - (100 + (f*35) ) -200 , y + mouseY - (300 + (p*35) ) , 10, 10);
  
  fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - (300 - (f*35) ) -400 , y + mouseY - (100 - (p*35) ) , 10, 10);
      p++;
      
      
      fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - (100 + (f*35) ) +200 , y + mouseY + (300 - (p*35) ) , 10, 10);
  
  fill(random(0,250),random(0,250),random(0,250));
  ellipse(x + mouseX - (300 - (f*35) ) +200 , y + mouseY - (100 - (p*35) ) , 10, 10);
      p++;
      
      
      
    }
    f++
  }
  
}
