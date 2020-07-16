# Painting Board made with VanillaJS

## Canvas API

You can refer to below link.  
https://developer.mozilla.org/ko/docs/Web/HTML/Canvas  
We will use this Canvas API to draw a figure on our own cavas.

---

## 2D Context

1. Logic  
   If "painting'" is false, just keep tracking the position of x and y. While "painting" is true, current position of mouse will keep connecting to privious position of x and y. stroke() will fill in the line with its color.
   ```
   if (!painting) {
   ctx.beginPath();
   ctx.moveTo(x, y);
   } else {
   ctx.lineTo(x, y);
   ctx.stroke();
   }
   ```
2. We have to give canvas its size in javascript, not only in CSS.

   ```
   canvas.width = 700;
   canvas.height = 700;
   ```

---

## Changing Color

To change color of line, we will get color property from a mouse event. So, get a collection of color class and put them into an arrray with an event listener.

```
Array.from(colors).forEach((color) =>
color.addEventListener("click", handleColorClick)
);

function handleColorClick(event) {
const color = event.target.style.backgroundColor;
ctx.strokeStyle = color;
}
```

---

## Changing Brush Size

Same as above, get range element from HTML and add an event listener to it. Then, override the "lineWidth".

```
function handleRangeChange(event) {
  const size = event.target.value;
  ctx.lineWidth = size;
}
```

---

## Filling The Canvas

1. If a user clicks the mode button, it will call "handleModeClick".
   ```
   if (mode) {
   mode.addEventListener("click", handleModeClick);
   }
   ```
2. When the button is clicked, change the function of button.
   ```
   function handleModeClick() {
   if (filling === true) {
       filling = false;
       mode.innerText = "Fill";
   } else {
       filling = true;
       mode.innerText = "Paint";
   }
   }
   ```
3. When a user clicks a color, the color will be set to "fillStyle".
   ```
   function handleColorClick(event) {
   const color = event.target.style.backgroundColor;
   ctx.strokeStyle = color;
   ctx.fillStyle = color;
   }
   ```
4. Then finally fill in the canvas with color.
   ```
   function handleCanvasClick() {
   if (filling) {
       ctx.fillRect(0, 0, CANVAS_SIZE, CANVAS_SIZE);
   }
   }
   ```
