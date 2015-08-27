# Elements: view changes

1. Representation of the DOM
2. Magnifying glass search
3. Right click and add attribute, edit as HTML
4. Click & drag

# Elements: Styles

1. Computed CSS Style
2. Add. edit, enable/disable 
3. Edit rules for pseudo-class
4. Link directly to which CSS

* Starts with most specific CSS styles

- Add property button
- Pseudo-element button: active, focus, hover, visited
- Color-picker swatch button

# Sources: edit files directly
- Modify source files
- Export changes
- Track file versions

Right click:
- Save as
- Local modifications

# Console: JavaScript
- View log output
- Debug
- Test any JS

document.getElementById('id');

console.log(console);
> returns a DOM object

console.assert(1==1);
> undefined if true

console.assert(1==2);
> assertion failed

console.warn("String!");

# Console: Errors
Read line number at .js
Read error message

>= icon to jump to Console

# Console helper methods

/ Find selector & descendants
$('#title');

$('#date)[0];

/ Find element in Elements
inspect($('date')[0]);

/ $0, $1, $2

# Debugging JavaScript

// If statements

if (events == null) {
    events = [];
}

// Pause on exception icon (||)

When next error occurs, code will be paused.

Click on objects to check if it's null.

Pretty print mode icon {}

// Pause only on Uncaught Exceptions dbclick (||)

// Create debugger Breakpoints

Click line number

Will highlight line @ point

// Right-hand buttons
Resume |>
Step over (go to next fxn)
Step into (down into fxn)
Step out (go up into caller)
Deactivate all breakpoints

# Resources

LocalStorage
file://

Edit your JSON

# Network panel

See how fast your page loads, status codes

1. Shift+Refresh
2. See Timeline and seconds status bar
3. Status should be: 200 OK
4. Disable the Cache
* New incognito window
* Click Gear icon and Settings: Disable cache checkbox

Latency: How long from the start from asking to when it begins?

Timeline: Color-coded by type of request, how long between begin & end

Initiator: Where resource was found in index.html

Blue line: DOM fired when browser is done parsing HTML

Red line: All done downloading

Endpoint: All data from request was received 

# Analyze Network performance

* PageSpeed extension
* Optimize .js files
- Minify .js files
- Combine .js files
- Google Closure Tools
- closure-compiler.appspot.com
* Avoid bad requests
- Remove broken links
* Optimize stylesheet order
- CSS first, then JS
- <script async src="">
* Serve correctly-sized imgs


# Profiles

* Frames View

Your website's FPS can be lowered by:
- HTML loading (Loading)
- JS execution (Scripting)
- Styling (Rendering)
- Painting (Painting)

Frames View shows how your FPS slows down: Timeline > Frames

Record button
Click an event
See slide animation

* CPU Profiler

Profiles
Collect JavaScript CPU Profile
Record/Stop
Each fxn and time %

# Find memory leaks

Timeline > Memory

Amount of memory allocated to application. Healthy apps don't grow in memory.

Heap Snapshots

Figure out where the leak might be.
 
Profiles > Take Heap Snapshots

Right click: comparison







