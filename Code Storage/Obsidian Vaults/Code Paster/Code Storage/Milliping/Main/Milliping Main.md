// Constants
//https://editor.p5js.org/Ragoffical/sketches/HeC8Itli-
const Y_AXIS = 1;
const X_AXIS = 2;
let b1, b2, c1, c2;
let SearchTimeHovered = 0
let FollowingDashTimeHovered = 0
let FollowingAmount = 37
function setup() {
  createCanvas(windowWidth,windowHeight);
}

function draw() {
  w=windowWidth
  h=windowHeight
  SideBarWidth=w/10
  SideBarHeight=h
  TopBarHeight=h/18
  background(62);
  
  SideBarFadePrimary = color(235,61,131,127.5);
  SideBarFadeSecondary = color(80,207,189,127.5);
  SideBarFadePrimaryB = color(80,207,189);
  SideBarFadeSecondaryB = color(235,61,131);
  SideBarFadePrimaryC = color(235,61,131,127.5);
  SideBarFadeSecondaryC = color(80,207,189,127.5);
/*
    SideBarFadePrimary = color(254,159,53,127.5);
  SideBarFadeSecondary = color(202,76,33,127.5);
  SideBarFadePrimaryB = color(202,76,33);
  SideBarFadeSecondaryB = color(254,159,53);
  SideBarFadePrimaryC = color(254,159,53,127.5);
  SideBarFadeSecondaryC = color(202,76,33,127.5);
  */
  TopBarFadePrimary = color(59);
  TopBarFadeSecondary = color(39);
  SearchBarFadePrimary = color(235,61,131+(SearchTimeHovered*2))
  SearchBarFadeSecondary = color(80,207,189+SearchTimeHovered)
  MaxSearchTimeHovered=20
  EnglishSearch="Search"
  SearchLang=EnglishSearch
  strokeWeight(1)
  setGradient(SideBarWidth,0,w-SideBarWidth,TopBarHeight,TopBarFadePrimary,TopBarFadeSecondary,X_AXIS);
  setGradient(0,0,SideBarWidth,SideBarHeight-1,SideBarFadePrimaryB,SideBarFadeSecondaryB,X_AXIS);
  setGradient(0,0,SideBarWidth,SideBarHeight,SideBarFadePrimary,SideBarFadeSecondary,Y_AXIS);
  setGradient(0,0,SideBarWidth,SideBarHeight,SideBarFadePrimaryC,SideBarFadeSecondaryC,Y_AXIS);
  setGradient(SideBarWidth+(w/48),TopBarHeight/6,w/4,TopBarHeight/1.5,SearchBarFadePrimary,SearchBarFadeSecondary,X_AXIS);
  noFill(0)
  stroke(56)
  strokeWeight(1)
  rect(SideBarWidth+(w/48),TopBarHeight/6,w/4,TopBarHeight/1.5)
  textAlign(LEFT,TOP);
  textSize(TopBarHeight/1.5/1.5)
  fill(255,150)
  noStroke()
  text(SearchLang,SideBarWidth+(w/28),TopBarHeight/3.3)

  //followers
  FollowersDisplayFadePrimary = color(235,61,131);
  FollowersDisplayFadeSecondary = color(80,207,189);
  FollowersDisplayFadePrimaryB = color(80,207,189,127.5);
  FollowersDisplayFadeSecondaryB = color(235,61,131,127.5);
  FollowersDisplayX=SideBarWidth+(w/48)
  FollowersDisplayY=TopBarHeight+w/32
  FollowersDisplayW=w/7
  FollowersDisplayH=h/10
  strokeWeight(1)
  
  


 
  
  //following
  FollowingDisplayFadePrimary = color(235,61,131);
  FollowingDisplayFadeSecondary = color(80,207+FollowingDashTimeHovered,189);
  FollowingDisplayFadePrimaryB = color(80,207,189,127.5);
  FollowingDisplayFadeSecondaryB = color(235,61,131+(FollowingDashTimeHovered*2),127.5);
  FollowingDisplayX=FollowersDisplayX+FollowersDisplayW+w/256
  FollowingDisplayY=TopBarHeight+w/32
  FollowingDisplayW=w/7
  FollowingDisplayH=h/10
  strokeWeight(1)
 
   //setGradient(FollowingDisplayX,FollowingDisplayY,FollowingDisplayW/1.25,FollowingDisplayH-1,FollowersDisplayFadePrimary,FollowersDisplayFadeSecondary,X_AXIS);
  //setGradient(FollowingDisplayX,FollowingDisplayY,FollowingDisplayW/1.25,FollowingDisplayH,FollowersDisplayFadePrimaryB,FollowersDisplayFadeSecondaryB,Y_AXIS);
 setGradient(FollowersDisplayX,FollowersDisplayY,FollowersDisplayW/1.25,FollowersDisplayH-1,FollowingDisplayFadePrimary,FollowingDisplayFadeSecondary,X_AXIS);
  setGradient(FollowersDisplayX,FollowersDisplayY,FollowersDisplayW/1.25,FollowersDisplayH,FollowingDisplayFadePrimaryB,FollowingDisplayFadeSecondaryB,Y_AXIS);
  
  fill(255)
  textSize(FollowersDisplayW/8)
  text(FollowingAmount,FollowersDisplayX+(FollowersDisplayW/16),FollowersDisplayY+(FollowersDisplayH/6))
  textSize(FollowersDisplayW/15)
  text("Following",FollowersDisplayX+(FollowersDisplayW/16),FollowersDisplayY+(FollowersDisplayH/6)+FollowersDisplayW/9+FollowersDisplayH/16)
  
  MaxFollowingDashTimeHovered=20
  
  stroke(0,0)
  ellipse(FollowersDisplayX+FollowersDisplayW-w/19,FollowersDisplayY+(FollowersDisplayH/3),FollowersDisplayW/7.5/2,FollowersDisplayH/4)
  rect(FollowersDisplayX+FollowersDisplayW-w/16,FollowersDisplayY+(FollowersDisplayH/2.1),FollowersDisplayW/7.5,FollowersDisplayH/6,16)
  rect(FollowersDisplayX+FollowersDisplayW-w/16,FollowersDisplayY+(FollowersDisplayH/1.8),FollowersDisplayW/7.5,FollowersDisplayH/8)
  strokeWeight(2)
  stroke(255)
  rect(FollowersDisplayX+FollowersDisplayW-w/24.1,FollowersDisplayY+(FollowersDisplayH/4),FollowersDisplayW/7.5/14,FollowersDisplayH/8)
  rect(FollowersDisplayX+FollowersDisplayW-w/22/1.04,FollowersDisplayY+(FollowersDisplayH/3.3),FollowersDisplayW/7.5/1.8/1.75,FollowersDisplayH/32)
  ellipse(FollowingDisplayX-w/256-FollowingDisplayW,10,10,20)
  circle(FollowingDisplayX+FollowingDisplayW,10,10)
  if(mouseX>FollowingDisplayX-w/256-FollowingDisplayW){
    if(mouseX<FollowingDisplayX+FollowingDisplayW){
      if(mouseY>FollowingDisplayY){
        if(mouseY<FollowingDisplayY+FollowingDisplayH){
          if(FollowingDashTimeHovered<MaxFollowingDashTimeHovered){
            FollowingDashTimeHovered=FollowingDashTimeHovered+1
            print("FollowingHover:"+FollowingDashTimeHovered)
          }
        } else if(FollowingDashTimeHovered>1){
          FollowingDashTimeHovered=FollowingDashTimeHovered-1
        }
      } else if(FollowingDashTimeHovered>1){
          FollowingDashTimeHovered=FollowingDashTimeHovered-1
        }
    } else if(FollowingDashTimeHovered>1){
          FollowingDashTimeHovered=FollowingDashTimeHovered-1
        }
  } else if(FollowingDashTimeHovered>1){
          FollowingDashTimeHovered=FollowingDashTimeHovered-1
        }

  if(mouseX>SideBarWidth+(w/48)){
    if(mouseX<SideBarWidth+(w/48)+w/4){
      if(mouseY>TopBarHeight/6){
        if(mouseY<TopBarHeight/6+TopBarHeight/1.5){
          if(SearchTimeHovered<MaxSearchTimeHovered){
            SearchTimeHovered=SearchTimeHovered+1
          }
        } else if(SearchTimeHovered>1){
          SearchTimeHovered=SearchTimeHovered-1
        }
      } else if(SearchTimeHovered>1){
          SearchTimeHovered=SearchTimeHovered-1
        }
    } else if(SearchTimeHovered>1){
          SearchTimeHovered=SearchTimeHovered-1
        }
  } else if(SearchTimeHovered>1){
          SearchTimeHovered=SearchTimeHovered-1
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
function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}