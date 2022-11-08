    // next animation frame

    requestAnimationFrame(render);

   

    // update time

    var newTime   = new Date().getTime() / 1000,

        deltaTime = newTime - (time || newTime);

    time = newTime;

   

    // clear canvas

    context.clearRect(0, 0, canvas.width, canvas.height);

   

    // create new particles

    var amount = particleRate * deltaTime;

    for (var i = 0; i < amount; i++) {

      var pos = pointOnHeart(Math.PI - 2 * Math.PI * Math.random());

      var dir = pos.clone().length(settings.particles.velocity);

      particles.add(canvas.width / 2 + pos.x, canvas.height / 2 - pos.y, dir.x, -dir.y);

    }

   

    // update and draw particles

    particles.update(deltaTime);

    particles.draw(context, image);

  }

 

  // handle (re-)sizing of the canvas

  function onResize() {

    canvas.width  = canvas.clientWidth;

    canvas.height = canvas.clientHeight;

  }

  window.onresize = onResize;

 

  // delay rendering bootstrap

  setTimeout(function() {

    onResize();

    render();

  }, 10);

})(document.getElementById('pinkboard'));

  </script>

 </BODY>

</HTML>
