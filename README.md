<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mouse Move Event</title>
  <style>
    #mousemove-container {
      background: linear-gradient(145deg, rgb(30, 30, 30), rgb(0, 0, 0));
      height: 100vh;
      overflow: hidden;
    }

    .mouse-dot {
      width: 15px;
      height: 15px;
      background-color: green;
      border-radius: 50%;
      position: absolute;
      opacity: 20%;
    }
  </style>
</head>
<body>
<div id="mousemove-container" onmousemove="createDot(event)">
</div>

<script>
  var DotCount = 0;
  var DotX = 0;
  var DotY = 0;

  function createDot(event) {
    var container = document.getElementById('mousemove-container');
    var dot = document.createElement('div');
    dot.className = 'mouse-dot';
    DotX = ((DotX/100)*95)+((event.clientX/100)*5);
    DotY = ((DotY/100)*95)+((event.clientY/100)*5);
    // Set the dot's position
    var dotLeft = DotX - container.offsetLeft;
    var dotTop = DotY - container.offsetTop;
    dot.style.left = dotLeft + 'px';
    dot.style.top = dotTop + 'px';

    // Append the dot to the container
    container.appendChild(dot);
    DotCount++;
    
    // Remove the dot after 2000 milliseconds (2 seconds)
    
      setTimeout(function () {
        container.removeChild(dot);
        DotCount--;
      
      }, 2000);
  }

</script>

</body>
</html>
