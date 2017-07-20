# Peanut-Game
This is the code for a educational game I am working on to teach children about peanut allergies. I intend to make several different levels and to make it for different types of allergies, too! 

import ddf.minim.*;
import ddf.minim.analysis.*;
import ddf.minim.effects.*;

float currentScene = 3;
boolean homeScreenDone = false;
boolean introScreenDone = false; 
boolean intro2ScreenDone = false; 
boolean thirdScreenDone = false; 
boolean factScreenDone = false;
boolean factScreen2Done = false;



void mouseClicked() {
  # System.out.println("mouse clicked current scene:" + currentScene);
  
    if (currentScene == 1) {
        homeScreenDone = true;
        //introScreen();
    } else if (currentScene == 2) {
        factScreenDone = true; 
    } else if (currentScene == 3) {
        factScreen2Done = true; 
    } else if (currentScene == 4) {
        introScreenDone = true; 
    } else if (currentScene == 5) {
        intro2ScreenDone = true; 
    } else if (currentScene == 6) {
        thirdScreenDone = true;
    } else if (currentScene == 7) {
        homeScreen();
    }
    
}


void homeScreen () {
    currentScene = 1;
    # delay(5000);
    background(bgg);
    textSize(39);
    text("           do NUT eat", 100, 90);
    text("Click the screen to continue", 50, 550);
    
}
void factScreen () {
    currentScene = 2;
    background(bg2);
    textSize(39);
    text("Your friend has a severe", 60, 180);
    text("peanut allergy. A peanut", 60, 255);
    text("allergy occurs when your", 60, 330);
    text("immune system mistakes a", 60, 405);
    text("peanut for something harmful. ", 60, 480);
    
}

void factScreen2 () {
    currentScene = 3;
    background(bg3);
    textSize(39);
    text("However, peanut allergies", 60, 150);
    text("are very common. More than ", 60, 225);
    text("3.3 million Americans have a", 60, 300);
    text("peanut allergy. That's about 1%", 60, 375);
    text(" of the U.S. population!", 60, 450);

    
}

void introScreen () {
    currentScene = 4;
    background(bg4);
    textSize(39);
    text("YOUR MISSION:", 250, 100);
    text("Deliver the cupcake to your", 50, 175);
    text("friend who has a severe peanut", 50, 240);
    text("allergy. You have 3 Epi-Pens", 50, 315);
    text("(lives) which is a 'shot-like'", 50, 390);
    text("object used to save someone", 50, 465);
    text("having an allergic reaction.", 50, 540);
}
void intro2Screen () {
    currentScene = 5;
    background(bg2);
    textSize(39);
    text("Make sure to avoid the evil", 70, 140);
    text("peanuts! Even if the cupcake", 70, 200);
    text("slightly touches a peanut, ", 70, 260);
    text("the whole cupcake is at risk", 70, 320);
    text("of something called ", 70, 380);
    text("'cross-contamination'.", 70, 440);
}

void thirdScreen () {
    currentScene = 6;
    background(bg4);
    textSize(39);
    text("Instructions:", 250, 100);
    text("Press the right arrow to move.", 50, 200);
    text("Press the up arrow to jump.", 50, 300);
    text("Press the spacebar to shoot ", 50, 400);
    text("jelly at the evil peanuts!", 50, 500);
}


# declare globals
PImage Peanut;
PImage EpiPen;
PImage friend1;
PImage bg; 
PImage bgg;
PImage bg2;
PImage bg3;
PImage bg4;
PImage cafe;

Jelly jelly1;
# Jelly jelly2;

Platform plat1;
Platform plat2;
Platform plat3;
Platform plat4;
Platform plat5;
Platform plat6;
SideJumper hero1;
Peanut p1;
Peanut p2;

# Lives l1;
Peanut p3; 
Peanut p4;
Lives e1;
Lives e2;
Lives e3;

Minim minim;
AudioPlayer acoolsong;

float ground = 700;
float left;
float right;
float up;
float down;
float xFriend1 = 640;
float pxposition;
float pyposition;
float pheight;


float xPlat = 0;
float yPlat = 0;
float wPlat = 160;
float hPlat = 12;
int life = 3;

boolean girlright = false;
boolean girlleft = false;
boolean girlup = false;
boolean platf1 = false;
boolean die;
boolean jellyRight = false;
boolean jellyLeft = false;
boolean peanutHide = false;
boolean ammo = false;

void setup()
{
  size(700, 600);
  
  minim = new Minim(this);
  acoolsong = minim.loadFile("acoolsong-2.mp3");
  acoolsong.loop();
    
  plat1 = new Platform((color(0,123,132)), xPlat + 50, yPlat + 460, wPlat, 0); 
  plat2 = new Platform((color(0,123,132)), xPlat + 280, yPlat + 410, wPlat, 0); 
  plat3 = new Platform((color(0,123, 132)), xPlat + 500, yPlat + 100, wPlat, 0);
  plat4 = new Platform((color(0,123, 132)), xPlat + 120, yPlat + 295, wPlat, 0);
  plat5 = new Platform((color(0,123, 132)), xPlat + 380, yPlat + 195, wPlat, 0);
  plat6 = new Platform((color(0, 123, 132)), xPlat + 450, yPlat + 510, wPlat, 0);
  
  # Sets up the peanuts
  PImage myimage = loadImage("evilPeanut1.png");
  p1 = new Peanut(myimage, pheight + 60, 40, pxposition + 70, pyposition + 430, 1, 50, wPlat + 50, peanutHide); 
  p2 = new Peanut(myimage, pheight + 70, 40, pxposition + 300, pyposition + 375, 1, 280, wPlat + 280, peanutHide);  
  p3 = new Peanut(myimage, pheight + 60, 40, pxposition + 140, pyposition + 265, 1, 120, wPlat + 120, peanutHide); 
  p4 = new Peanut(myimage, pheight + 70, 40, pxposition + 400, pyposition + 160, 1, 380, wPlat + 380, peanutHide); 
  
  PImage myimages = loadImage("epipen.png"); 
  e1 = new Lives(life, myimages, 20, 40, 20, 20);
  e2 = new Lives(life, myimages, 40, 40, 20, 20);
  e3 = new Lives(life, myimages, 60, 40, 20, 20);
  
 
  friend1= loadImage("friend96.png");
  bg = loadImage("classroom.png"); 
  bgg = loadImage("homescreen2.png"); 
  bg2 = loadImage("peanutBorder.png"); 
  bg3 = loadImage("pbBorder2.png"); 
  bg4 = loadImage("cupcakeBorder2.png"); 
  cafe = loadImage("cafeteria2.png"); 
  
  hero1 = new SideJumper();
  hero1.direction = 1;
  hero1.image = loadImage("hero96.png");
  hero1.girlwidth = hero1.image.width / 2;
  # System.out.println(hero1.girlwidth);
  hero1.girlheight = hero1.image.height / 2;
  hero1.xPos = 50;
  hero1.yPos = 550;  
  hero1.velocity = 0;
  hero1.jumpSpeed = 10;
  hero1.walkSpeed = 4;
  
  
  jelly1 = new Jelly(hero1.xPos, hero1.yPos, 8, 7);
 # jelly2 = new Jelly(hero1.xPos, hero1.yPos + 9, 30, 0);
  
}


void draw()
{
  
    homeScreen();
  
  if(homeScreenDone == true){
    factScreen();
  }
  if(factScreenDone == true){
    factScreen2();
  }
  
  if(factScreen2Done == true){
    introScreen();
  }
   if(introScreenDone == true){
    intro2Screen();
  }
   if(intro2ScreenDone == true){
    thirdScreen();
  }
  
  if(thirdScreenDone == true){
  
  background(bg);
  
  # you only need a width and a heigth input if you want to adjust if from whatever the filesize is
 
  
  image(friend1, xFriend1, 55);
  # peanut stuff
   if(ammo == true) {
    jelly1.checkDirection();
    jelly1.shift();
    jelly1.display();
    jelly1.ammoCheck();
 
  

   
   

    
 }
  p1.display();
  p1.walk();
  p1.jellyPeanut(jelly1);

  
  p2.display();
  p2.walk();
  p2.jellyPeanut(jelly1);
  
  
  p3.display();
  p3.walk(); 
  p3.jellyPeanut(jelly1);
 
  p4.display();
  p4.walk(); 
  p4.jellyPeanut(jelly1);
 
  
  
  
  e1.display();
  e1.showlife();
  e2.display();
  e2.showlife();
  e3.display();
  e3.showlife();
  

  plat1.display();
  plat2.display();
  plat2.shift();
  plat3.display();
  plat4.display();
  plat5.display();
  plat6.display();
  
# every frame, you simply move and then 'redraw' your hero
  movehero();
  updatehero1();
  
  
  }
}


class Platform
{
  color c;
  float xpos;
  float ypos;
  float pWidth;
  float xspeed;
  
  Platform(color tempC, float tempXpos, float tempYpos, float pWid, float tempXspeed) { 
    c = tempC;
    xpos = tempXpos;
    ypos = tempYpos;
    pWidth = pWid;
    xspeed = tempXspeed;
  }
  void display() {
    stroke(0);
    fill(c);
    rect(xpos,ypos, pWidth, hPlat);
  }
   void shift() {
    xpos = xpos + xspeed;
    if (xpos > width) {
      xpos = 0;
    }
  }
}

# the lives class. remember to set up an instance before and in setup and run it in draw

# the lives class. remember to set up an instance before and in setup and run it in draw
class Lives {
  
  int life; 
  PImage myimages;
  float epiHeight;
  float epiWidth;
  float epiXpos;
  float epiYpos; 
  
  Lives(int numlife, PImage myPic, float eXpos, float eYpos, float eHeight, float eWid) {
  
    life = numlife;
    myimages = myPic;
    epiHeight = eHeight;
    epiXpos = eXpos;
    epiYpos = eYpos;
    epiWidth = eWid;
  }
  
  void display() {
    image(myimages, epiXpos, epiYpos, epiHeight, epiWidth);
  }
  void showlife() {
  
  if ( die == true && life == 3) {
    e3.epiXpos = -20;
    life = 2;
    die = false;
  }
  if ( die == true && life == 2) {
    e2.epiXpos = -20;
    life = 1;
    die = false;
  }
  if ( die == true && life == 1) {
    e1.epiXpos = 0; 
    life = 0;
    die = false;
    
  }
   
  if (life == 0) {
    textSize(75);
    fill(255, 0, 0);
    text("THE CUPCAKE", 30, 300);
    text("HAS BEEN", 30, 400);
    text("CONTAMINATED!", 30, 500);
    delay(1000);
    stop();
  } 
  
   if (hero1.yPos <= 65 && hero1.xPos >= 610) {
    textSize(90);
    background(cafe);
    text("YOU WIN!", 30, 200);
    text("NOW LEVEL 2!", 30, 400);
    delay(1000);
    stop();
  } 
  
  
 }
} 




class Jelly {
  float xJelly;
  float yJelly;
  float Jellysize;
  float jellySpeed; 
  
  Jelly(float tempxJelly, float tempyJelly, float tempJellysize, float tempjellySpeed) {
  
  xJelly = tempxJelly;
  yJelly = tempyJelly;
  Jellysize = tempJellysize;
  jellySpeed = tempjellySpeed;
  }
  
  void display(){
    stroke(0);
    fill(255, 102, 177);
    ellipse(xJelly, yJelly, 8, 8);
  }
  void shift(){
    yJelly = hero1.yPos;
    # Jellysize = 3;
    # System.out.println(xJelly);
    if(jellyRight == true){
       xJelly += jellySpeed;
    }
    else if(jellyLeft == true){
       xJelly -= jellySpeed;
    }
  }
  
  
  void checkDirection(){
    if(hero1.direction == 1){
        jellyRight = true;
    }
    else{
        jellyLeft = true;
    }
  }
  
  void ammoCheck(){
    if(xJelly > 700 || xJelly < 0){
      jellyRight = false;
      jellyLeft = false;
      xJelly = hero1.xPos; 
        ammo = false;
  }
}

  }



class SideJumper
{
  PImage image;
  float xPos;
  float yPos;
  
  float girlwidth;
  float girlheight; 
  
  boolean girlright;
  boolean girlleft;
  boolean girlup;
  
  float direction;
  float velocity;
  float jumpSpeed;
  float walkSpeed;
}


boolean checkPlatform(Platform plat) {
if(hero1.yPos + hero1.girlheight < plat.ypos && hero1.yPos + hero1.girlheight > 491){
  if(hero1.xPos < plat.xpos + plat.pWidth){
    if(hero1.xPos > plat.xpos){
      return true;
         }
     }
}
return false;
}

boolean checkPlatform2(Platform plat) {
  if(hero1.yPos + hero1.girlheight < plat.ypos && hero1.yPos + hero1.girlheight >400){
    if(hero1.xPos < plat.xpos + plat.pWidth){
      if(hero1.xPos > plat.xpos){
        return true;
         }
     }
}
return false;
}

boolean checkPlatform4(Platform plat) {
  if(hero1.yPos + hero1.girlheight < plat.ypos && hero1.yPos + hero1.girlheight > 286){
    if(hero1.xPos < plat.xpos + plat.pWidth){
      if(hero1.xPos > plat.xpos){
        return true;
         }
     }
}
return false;
}

boolean checkPlatform5(Platform plat) {
  if(hero1.yPos + hero1.girlheight < plat.ypos && hero1.yPos + hero1.girlheight > 186){
    if(hero1.xPos < plat.xpos + plat.pWidth){
      if(hero1.xPos > plat.xpos){
        return true;
         }
     }
}
return false;
}

boolean checkPlatform3(Platform plat) {
  if(hero1.yPos + hero1.girlheight < plat.ypos && hero1.yPos + hero1.girlheight > 91){
    if(hero1.xPos < plat.xpos + plat.pWidth){
      if(hero1.xPos > plat.xpos){
        return true;
         }
     }
}
return false;
}

boolean checkPlatform6(Platform plat) {
  if(hero1.yPos + hero1.girlheight < plat.ypos && hero1.yPos + hero1.girlheight > 501){
    if(hero1.xPos < plat.xpos + plat.pWidth){
      if(hero1.xPos > plat.xpos){
        return true;
         }
     }
}
return false;
}


void updatehero1(){
  # Technically you don't need the matrix operations, but they don't hurt you either
  # these would be helpful if you were drawing a lot of layers, and you 
  # we're sure the girl would draw on top. 
  
  # pushMatrix(); //creates a temporary "matrix" to draw your girl onto
  imageMode(CENTER);
  translate(hero1.xPos, hero1.yPos); 
# System.out.println(hero1.direction);
  scale(hero1.direction, 1);
  image(hero1.image, 0, 0); 
 # popMatrix(); //get rid of the temporary matrix
}

void movehero(){
  if (hero1.xPos == pxposition && pxposition == hero1.xPos){
# System.out.println("meow");  
}
  # System.out.println("Move Hero");
  if(girlright == true && isRightAllowed()){
   # move the hero right at her walking speed
  # System.out.println("walk to the right");
   hero1.xPos  += hero1.walkSpeed;
  }
  
  if(girlleft == true && isLeftAllowed()){
   # move the hero left at her walking speed
 #  System.out.println("walk to the left");
   hero1.xPos  -= hero1.walkSpeed;
  }
  
  if(girlright == true && girlleft == true){
   # dont move the hero since you're hitting both
 #  System.out.println("right and left?");
   hero1.xPos  += 0;
  }
  
# up
  if(girlup == true && isUpAllowed()){
    heroJump();

  
  # 2: verify your 
  # -- your velocity is negative <-- this is because we defined negative as down and positive 
  # velocity as up as in phyics. (might seem backwards because of how we draw the frame in processing with all positive numbers)
  # -- you are on the ground
  
 if( hero1.velocity < 0 &&  isonGround()){
   hero1.velocity = 0; //stop falling
 }
 
 # apply velocity to position
 
 hero1.yPos -= hero1.velocity;
  
}


boolean isLeftAllowed(){
  # check for collision against left side of screen
  float left = hero1.xPos;
  if( left <= 0){
   # System.out.println("LEFT SIDE COLLISION"); 
    return false;
      
  }
  return true;
}
boolean isRightAllowed(){
  # check for collision against right side of screen
  float right = hero1.xPos;
  if( right >= 700){
     # System.out.println("RIGHT SIDE COLLISION");  
    return false; 
  }
  return true;
} 

boolean isUpAllowed(){
  # she can only jump if she is on the ground
  return isonGround();
}

boolean isonGround(){
 float girlfeet = hero1.yPos + hero1.girlheight;
 # System.out.println("ypos:" + hero1.yPos + " feet " + girlfeet);  




if(checkPlatform(plat1) == true){
  # you arre on the platform, so you can jump
 return true; 
}
if(checkPlatform2(plat2) == true){
 return true; 
}
if(checkPlatform4(plat4) == true){
 return true; 
}
if(checkPlatform5(plat5) == true){
 return true; 
}
if(checkPlatform3(plat3) == true){
 return true; 
}
if(checkPlatform6(plat6) == true){
 return true; 
}

if( girlfeet >= 590){
    return true; 
 }
# System.out.println("falling through floor"); 
  return false;
}

void heroJump(){
  hero1.velocity = 9; # random guess, change this to change how fast she jumps
  
}



void keyPressed()
{
  if (keyCode == RIGHT)
  {
    right = 1;
    hero1.direction = 1;
    girlright = true;
    # System.out.println(girlright);

  }
  if (keyCode == LEFT)
  {
    left = -1;
    hero1.direction = -1;
    girlleft = true;
  }
  if (keyCode == UP )
  {
    up = -1;
    girlup = true;
   }
  if (key == ' ' )
  {
    # System.out.println("down");
    jelly1.shift();
    jelly1.display();
    ammo = true;
   }
 }
 
void keyReleased()
{
  if (keyCode == RIGHT)
  {
    right = 0;
    girlright = false;
  }
  if (keyCode == LEFT)
  {
    left = 0;
    girlleft = false;
  }
  if (keyCode == UP)
  {
    up = 0;
    girlup = false; 
   }
#  if (keyCode == DOWN)
#  {
#    down = 0;
#    ammo = false; 
#   }
}


class Peanut 
{
  PImage myimage;
  float pheight;
  float pwidth;
  float pxposition;
  float pyposition;
  float pspeed;
  float lrange;
  float rrange;
  boolean peanutHide;
  
  
  Peanut(PImage myPic, float ph, float pw, float px, float py, float speedP, float lr, float rr, boolean phide) { 
     myimage = myPic;    
    pheight = ph;
    pwidth = pw;
    pxposition = px;
    pyposition = py;
    pspeed = speedP;
     lrange = lr;
     rrange = rr; 
    peanutHide = phide; 
  }

  void display() {
    image(myimage, pxposition, pyposition, pwidth, pheight);
    
  }
  
  void jellyPeanut(Jelly jelly1){

   if (jelly1.xJelly >= pxposition - 50 && jelly1.xJelly <= pxposition + 50){
     if((jelly1.yJelly <= pyposition + pheight) && (jelly1.yJelly >= pyposition - pheight)){
       
          # System.out.println("ruff");  
          background(255, 255, 255);
          peanutHide = true; 
        }
        
     }
       if(peanutHide == true){
        # System.out.println("peanut hide if");
        pyposition = -1000;
        peanutHide = false;
      
   }

     


 
  }
    

  
  void walk() {
   # System.out.println("peanut walk");
    if (pxposition == lrange || pxposition == rrange)
    {
    pspeed = pspeed * -1;
    }
    pxposition += pspeed;
   
  
    
    
   if (hero1.xPos == pxposition && pxposition == hero1.xPos){
     if((hero1.yPos + hero1.girlheight >= pyposition - pheight) || (hero1.yPos - hero1.girlheight >= pyposition - pheight)){
       if((hero1.yPos + hero1.girlheight <= pyposition + pheight) || (hero1.yPos - hero1.girlheight <= pyposition + pheight)){ 
 # System.out.println("meow");  
background(0, 0, 0);
die = true; 
        }
     }
  }

  }

}


void gameScreen () {
    currentScene = 7;

setup();
 draw();
 
}
