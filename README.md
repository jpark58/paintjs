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

3. To change color of line, we will get color property from a mouse event. So, get a collection of color class and put them into an arrray with an event listener.
   ```
   Array.from(colors).forEach((color) =>
   color.addEventListener("click", handleColorClick)
   );
   ```
