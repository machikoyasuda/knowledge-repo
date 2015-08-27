## FLUID
pixels --> ems
1em=10px, 
font-size: 16px;
font-size: 62.5%;

Target divided by current context = result

30 px / 10 px = 3em

font-size: 3em; /30px/10px/

The default font-size for a browser is 16px.

Use at least six places after decimal point

24px/10px = 2.4em

### Fluid foundations

### Fluid site:
Fluid sites are usually based on fluid grid.

Fluid sites have relative percentage values, rather than pixels. Need to convert width, margin, padding by dividing target by context (960px).

Block elements inherit widths of parent element. Don't set fixed-widths on elements that don't need it.

Flexible padding: when setting flexible padding on an element, your context is the width of the element itself. 

## ADAPTIVE
Designing for controlled adaptation - know the device and context; design accordingly.

Who is your user?
How will they use it?
Context?
Content?

Markup: 

Break points: 480x320, 768x

Media queries: In group at bottom of stylesheet

<link rel… media="screen" />
@media screen and (max-width: 320px){
.class {
    float: none;
    width: inherit;
    }
    
@media screen and (max-width: 480px){


For any viewport less than or equal to 320, use these styles. 


## RESPONSIVE: MOBILE FIRST

Simplify content
Prioritize layout
Optimize UX

Universal

No filler content

All responsive is adaptive
But not all adaptive is responsive

Responsive provides continuity between contexts. Portable and accessible.

Content defines breakpoints. 

@media screen and (max-width: 870px) {

.box {
    float: none;
    width: inherit;
    margin: auto;
}

}

orientation
aspect-ratio

### Images:

Save img larger than you actually need
Optimize image for context widths

img, embed, object, video {
    max-width: 100%;
}

FitText - font-sizing flexible
Lettering.js - typography
FitVids.js - videos

Retina images: Use MQ to target those specific devices and optimize those imgs

only screen and (-webkit-min-device-pixel-ratio: 1.5),
only screen and (min-device-pixel-ratio: 1.5),

Images

PictureFill
https://github.com/scottjehl/picturefill#readme


background-size: px px;
background-image: url();
-webkit-background-size: px px;

<picture alt="Our Alternate Text">
 <!-- Smallest size first - no @media qualifier -->
<source src="content-image.jpeg" />
 <!-- Large size - send to viewports 800px wide and up -->



