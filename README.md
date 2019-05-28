# HarveyBallSVG

CSS for SVG based Harvey Balls and user macro for Atlassian Confluence

> Harvey balls are round ideograms used for visual communication of qualitative information. They are commonly used in comparison tables to indicate the degree to which a particular item meets a particular criterion. ([Wikipedia](https://en.wikipedia.org/wiki/Harvey_balls))

included:

- stylesheet for formatting the icon
- example HTML for using SVG to create a Harvey Ball icon and format it using classes
- VTL (Apache Velocity Templating Language) file that can be installed in Atlassian Confluence as a user macro

## Using Harvey Balls in HTML

1. link to the CSS file in your HTML's header
2. add the SVG defs to the end of your file
```html
<!--  <svg width="100" height="100" display="none"> -->
  <svg display="none">
    <defs>
      <title>Komponenten für den Harvey Ball</title>
      <symbol id="harvey-circle" viewBox="0 0 100 100">
        <desc>Kreis für den Hintergrund</desc>
        <circle cx="50" cy="50" r="40" />
      </symbol>
      <symbol id="clockwise-1of4" viewBox="0 0 100 100">
        <desc>Kreissegment 1/4 für den Vordergrund</desc>
        <path d="M 50 50 L 50 10 A 40 40 0 0 1 90 50 L 50 50" />
      </symbol>
      <symbol id="clockwise-2of4" viewBox="0 0 100 100">
        <desc>Kreissegment 1/4 für den Vordergrund</desc>
        <path d="M 50 50 L 50 10 A 40 40 0 0 1 50 90 L 50 50" />
      </symbol>
      <symbol id="clockwise-3of4" viewBox="0 0 100 100">
        <desc>Kreissegment 1/4 für den Vordergrund</desc>
        <path d="M 50 50 L 50 10 A 40 40 0 1 1 10 50 L 50 50" />
      </symbol>
      <symbol id="counterclockwise-1of4" viewBox="0 0 100 100">
        <desc>Kreissegment 1/4 für den Vordergrund</desc>
        <path d="M 50 50 L 50 10 A 40 40 0 0 0 10 50 L 50 50" />
      </symbol>
      <symbol id="counterclockwise-2of4" viewBox="0 0 100 100">
        <desc>Kreissegment 1/4 für den Vordergrund</desc>
        <path d="M 50 50 L 50 10 A 40 40 0 0 0 50 90 L 50 50" />
      </symbol>
      <symbol id="counterclockwise-3of4" viewBox="0 0 100 100">
        <desc>Kreissegment 1/4 für den Vordergrund</desc>
        <path d="M 50 50 L 50 10 A 40 40 0 1 0 90 50 L 50 50" />
      </symbol>
    </defs>
  </svg>
  ```
  
  3. enter your Harvey Balls in your HTML like this:
  
     - `<svg class="harvey-ball size2em"><g><use href="#harvey-circle" class="harvey grey" /></g></svg>`
     ... for an empty ball with grey color and double line height - 
     - `<svg class="harvey-ball size2em"><g><use href="#harvey-circle" class="harvey grey" /><use href="#clockwise-1of4" class="harvey-fill green" /></g></svg>` 
     ... for a ball with grey background and double line height filled green for one quadrant
     
## Add the Harvey Ball Macro to Atlassian Confluence

With Confluence Admin rights ...
* add the contents of the [HarveyBalls.css](HarveyBalls.css) file to the global stylesheet in the admin UI
* add a new user macro and insert the content of the [HarveyBalls.vtl](HarveyBalls.vtl) file in the code section
  * visible to all users in the macro browser
  * category: Confluence content
  * no macro body
