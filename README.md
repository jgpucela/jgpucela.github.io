# Zapandemic Heroes

Fork of the classic Space Invaders game written in JavaScript developed by [dwmkerr](https://dwmkerr.github.io/spaceinvaders/) 

No jQuery or any other third party libraries, just raw JavaScript, CSS and HTML.

See it Live: [https://jgpucela.github.io/index.html/](https://jgpucela.github.io/index.html/)

[![Space Invaders Screenshot](./screenshot.jpg "Space Invaders Screenshot")](https://jgpucela.github.io/zapandemicheroes/)


## Adding Zapandemic Heroes to a Web Page

First, drop the `spaceinvaders.js` file into the website.

Now add a canvas to the page.

```html
<canvas id="gameCanvas"></canvas>
```

Next, add the Zapandemic Heroes game code. You create the game, initialise it with the canvas, start it and make sure you tell it when a key is pressed or released. That's it!

```html
<script>
//  Setup the canvas.
var canvas = document.getElementById("gameCanvas");
canvas.width = 800;
canvas.height = 600;

//  Create the game.
var game = new Game();

//  Initialise it with the game canvas.
game.initialise(canvas);

//  Start the game.
game.start();

//  Listen for keyboard events.
var pressedKeys = [];
window.addEventListener("keydown", function keydown(e) {
  var keycode = window.event.keycode || e.which;
    if(!pressedKeys[keycode])
      pressedKeys[keycode] = true;
    //  Supress further processing of left/right/space (37/29/32)
    if(keycode == 37 || keycode == 39 || keycode == 32) {
      e.preventDefault();
    }
    game.keyDown(keycode);
});
window.addEventListener("keyup", function keydown(e) {
  var keycode = window.event.keycode || e.which;
    if(pressedKeys[keycode])
      delete pressedKeys[keycode];
    game.keyUp(keycode);
});
</script>
```

## References

- Virus icon  [Nerdzmasterz from https://opengameart.org/content/everyones-favorite-target](https://opengameart.org/content/everyones-favorite-target)

- CSS intro animation [Christopher Kade](https://codepen.io/christopherkade/pen/rJVPjz)
