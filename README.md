# MicroView Arduino Library

Developed by [Geek Ammo Pty Ltd](http://www.geekammo.com) based on Arduino and other Open Source libraries.  

## Description

Arduino library for MicroView.  

## Required Libraries

1. [Time.h](http://www.pjrc.com/teensy/td_libs_Time.html) NOTE: Only required when using clock/time functions.  For example the MicroViewDemo in the example folder.

## Installation

1. Change directory to Arduino's main directory
2. cd libraries
3. mkdir MicroView
4. cd MicroView
5. git clone git@github.com:geekammo/microview.git .
6. Start Arduino IDE.
7. MicroView example is located at, File--->Example--->MicroView--->MicroViewDemo

### Example 1 - Hello World!
<pre><code>
#include &lt;MicroView.h&gt;

void setup() {
	uView.begin();
}

void loop() {
	uView.print("HelloWorld");
	uView.display();		// display current page buffer
}
</code></pre>

### Example 2 - Basic Drawing
<pre><code>
#include &lt;MicroView.h&gt;

void setup() {
	uView.begin();
	uView.clear(PAGE);		// clear the page buffer
}

void loop() {
	uView.line(0,0,64,48);
	uView.circle(32,24,10);
	uView.rect(10,10,20,20);
	uView.pixel(50,5);
	uView.setCursor(0,40);
	uView.print(" MicroView");
	uView.display();		// display current page buffer
}
</code></pre>

### Example 3 - Widgets
<pre><code>
#include &lt;MicroView.h&gt;

MicroViewWidget *widget,*widget2;

void setup() {
	uView.begin();
	uView.clear(PAGE);
	widget= new MicroViewGauge(32,30,0,100);  // draw Gauge widget at x=32,y=30,min=0, max=100
	widget2= new MicroViewSlider(0,0,0,100);  // draw Slider widget at x=0,y=0,min=0, max=100
}

void loop() {
	for(int i=0; i&lt;=100;i++) {
		widget->setValue(i);	// give a value to widget
		widget2->setValue(i);
		uView.display();		// display current page buffer
	}
}
</code></pre>

### Example 4 - Communication
<pre><code>
#include &lt;MicroView.h&gt;

void setup() {
  uView.begin();
  uView.clear(PAGE);
}

void loop() {
  uView.checkComm();
}
</code></pre>

## History
**v1.10b: 22th April 2014 by JP Liew**
* changed SS, RESET, DC pins to use weak internal pull-up resistors

**v1.09b: 17th April 2014 by JP Liew**
* changed verticalFlip() to flipVertical() and horizontalFlip() to flipHorizontal() for consistency
* added debug messages for doCmd()

**v1.08b: 18th February 2014 by JP Liew**
* added verticalFlip(), horizontalFlip()

**v1.07b: 15th February 2014 by JP Liew**
* changed function name stopScroll to scrollStop for consistency
* added contrast function
* added invert function
* added KEYWORD to keywords.txt
* added checkComm() function to communicate with host PC

**v1.06b: 9th February 2014 by JP Liew**
* fixed Slider negative value not working
* added round Gauge widget
* changed Example 3 to show round Gauge

**v1.05b: 6th February 2014 by JP Liew**
* changed MICROVIEW class name to MicroView
* created MICROVIEWWIDGET class
* added routines to draw widget
* added slider widget
* merged MicroViewWidget into MicroView
* merged SPI.h into MicroView 

**v1.04b: 3rd February 2014 by JP Liew**
* declared permanent uView variable.
* cleaned code and added some remarks.
* added drawing functions that make use of default color and draw mode.
* added example in README.md

**v1.03b: 1st February 2014 by JP Liew**  
* added 7 segment number only font.

**v1.02b: 31th January 2014 by JP Liew**  
* added sprite animation demo.  

**v1.01b:	30th January 2014 by JP Liew**  
* fixed font draw XOR mode bug.  
* added analog clock demo.

**v1.00b:	30th January 2014 by JP Liew**  
* Initial commit.  Beta with minor bugs.