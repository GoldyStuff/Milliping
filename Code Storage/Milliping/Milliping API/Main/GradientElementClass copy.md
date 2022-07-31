//I would recommend you put this in a seperate file of your project called "GradientElementClass" instead of putting it in your main file.
//https://editor.p5js.org/Ragoffical/sketches/_LoWuDlpb

const Y_AXIS = 1;
const X_AXIS = 2;
const XY_AXIS = 3;
function setup() {
  createCanvas(windowWidth,windowHeight);
  Sidebar = new UiElement("Sidebar",100,0,100,300,235,61,131,80,207,189,XY_AXIS,true,20)
  fill(255)
  stroke(0)
  strokeWeight(1)
  rect(20,20,100,100)
}

function draw() {
  background(62);
  w=windowWidth
  h=windowHeight
  Sidebar.render()
  //debug(Sidebar)
}
function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
function debug(element){
  if(element.axis===1){
  this.axisTranslation = "Y"
  }
  if(element.axis===2){
  this.axisTranslation = "X"
  }
  if(element.axis===3){
  this.axisTranslation = "XY"
  }
  print(element.name+"(x:"+element.x+"|y:"+element.y+"|w:"+element.w+"|h:"+element.h+" | Gradient:(R:"+element.PrimaryFadeAR+"|G:"+element.PrimaryFadeAG+"|B:"+element.PrimaryFadeAB+" to "+"R:"+element.PrimaryFadeBR+"|G:"+element.PrimaryFadeBG+"|B:"+element.PrimaryFadeBB+") Axis:"+this.axisTranslation+"("+element.axis+") Hover:"+element.hover+"(MaxHover:"+element.maxhover+")) Called Debug Function")
}
class UiElement{
  constructor(name,x,y,w,h,PrimaryFadeAR,PrimaryFadeAG,PrimaryFadeAB,PrimaryFadeBR,PrimaryFadeBG,PrimaryFadeBB,axis,hover,maxhover){
    this.name=name
    this.x=x
    this.y=y
    this.w=w
    this.h=h
    this.axis=axis
    this.hover=hover
    this.maxhover=maxhover
    this.hovervar=0
    this.PrimaryFadeAR=PrimaryFadeAR
    this.PrimaryFadeAG=PrimaryFadeAG
    this.PrimaryFadeAB=PrimaryFadeAB
    this.PrimaryFadeBR=PrimaryFadeBR
    this.PrimaryFadeBG=PrimaryFadeBG
    this.PrimaryFadeBB=PrimaryFadeBB
    this.SecondaryFadeAR=PrimaryFadeAR
    this.SecondaryFadeAG=PrimaryFadeAG
    this.SecondaryFadeAB=PrimaryFadeAB
    this.SecondaryFadeAA=255
    this.SecondaryFadeBR=PrimaryFadeBR
    this.SecondaryFadeBG=PrimaryFadeBG
    this.SecondaryFadeBB=PrimaryFadeBB
    this.SecondaryFadeBA=127.5
  }
  render(){
    if(this.hover===true){
    if(mouseX>this.x){
      if(mouseX<this.x+this.w){
        if(mouseY>this.y){
          if(mouseY<this.y+this.h){
        if(this.hovervar<this.maxhover){
      this.hovervar=this.hovervar+1
        }
      } else{
        if(this.hovervar>1){
      this.hovervar=this.hovervar-1
      }
        }
      } else{
        if(this.hovervar>1){
      this.hovervar=this.hovervar-1
      }
    }
  } else{
        if(this.hovervar>1){
      this.hovervar=this.hovervar-1
      }
    }
  } else{
        if(this.hovervar>1){
      this.hovervar=this.hovervar-1
      }
  }
    }
 this.PrimaryFadeA=color(this.PrimaryFadeAR,this.PrimaryFadeAG,this.PrimaryFadeAB+this.hovervar,255)
  this.PrimaryFadeB=color(this.PrimaryFadeBR,this.PrimaryFadeBG,this.PrimaryFadeBB+this.hovervar,255)
this.SecondaryFadeA=color(this.SecondaryFadeAR,this.SecondaryFadeAG,this.SecondaryFadeAB+this.hovervar,this.SecondaryFadeAA)
this.SecondaryFadeB=color(this.SecondaryFadeBR,this.SecondaryFadeBG,this.SecondaryFadeBB+this.hovervar,this.SecondaryFadeBA)
  strokeWeight(1)
    if(this.axis===3){
setGradient(this.x,this.y,this.w,this.h-1,this.PrimaryFadeA,this.PrimaryFadeB,Y_AXIS);
      setGradient(this.x,this.y,this.w,this.h-1,this.SecondaryFadeA,this.SecondaryFadeB,X_AXIS);
    } 
    if(this.axis===1){
      setGradient(this.x,this.y,this.w,this.h-1,this.SecondaryFadeA,this.SecondaryFadeB,Y_AXIS);
    } 
    if(this.axis===2){
      setGradient(this.x,this.y,this.w,this.h-1,this.SecondaryFadeA,this.SecondaryFadeB,X_AXIS);
    }
  }
}
function setGradient(x, y, w, h, c1, c2, axis) {
  noFill();

  if (axis === Y_AXIS) {
    // Top to bottom gradient
    for (let i = y; i <= y + h; i++) {
      let inter = map(i, y, y + h, 0, 1);
      let c = lerpColor(c1, c2, inter);
      stroke(c);
      line(x, i, x + w, i);
    }
  } else if (axis === X_AXIS) {
    // Left to right gradient
    for (let i = x; i <= x + w; i++) {
      let inter = map(i, x, x + w, 0, 1);
      let c = lerpColor(c1, c2, inter);
      stroke(c);
      line(i, y, i, y + h);
    }
  }
}