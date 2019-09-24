<template>
  <div id="app">
    <!--<HelloWorld msg="Welcome to Your Vue.js App" />-->

    <audio id="audio-track" loop>
      <source src="./assets/audio/SIREN.mp3" type="audio/mpeg">
      <source src="./assets/audio/SIREN.ogg" type="audio/ogg">
      Your browser does not support the audio element.
    </audio>

    <div id="cover" class="show">
      <div class="cover-overlay"></div>
      <img class="cover-play" alt="play" src="./assets/img/rose.gif"/>
      <img id="cover-img" class="img-sheitan" alt="sheitan" src="./assets/img/sheitan-overlay.jpg"/>
    </div>

    <div id="container" class="hide">
      <img class="img-sheitan flicker" alt="sheitan" src="./assets/img/sheitan-invert-slow.gif"/>
      <img class="img-sheitan gif-sheitan" alt="sheitan" src="./assets/img/sheitan-960x540-slow.gif"/>

      <!--<img id="random-img" class="img-move" alt="image" src="./assets/img/play.gif"/>-->

      <p class="page-title blink-slow">ARNO</p>
      <p class="track-title blink-fast">SIREN</p>

      <p class="page-info">
        <span class="shanghai">上海</span><br>
        ARTIST: ARNO<br>
        TRACK: SIREN<br>
        3D: <a href="https://www.instagram.com/joli_gillet/" target="_blank">JOLI_GILLET</a><br>
        CODE: <a href="https://www.instagram.com/special.gee/" target="_blank">SPECIAL.GEE</a><br>
        .////////////////////////////<br>
        <a href="SIREN.wav" class="download-link" download>DOWNLOAD</a><br>
        .////////////////////////////
      </p>

      <img class="img-logo" alt="logo" src="./assets/img/cd-logo.png"/>
      <img class="img-cd" alt="logo" src="./assets/img/cd.gif"/>
    </div>

    <div id="footer">
      <p id="copyright">COPYRIGHT SPECIAL GEE © 2019</p>
    </div>

  </div>
</template>

<script>
//import HelloWorld from "./components/HelloWorld.vue";
import $ from "jquery";

export default {
  name: "app",
  components: {
    //HelloWorld
  },
  mounted () {
    var audio = document.getElementById("audio-track");

    $('#cover').click(function() {
      if (audio.readyState > 1) {
        $(this).removeClass("show");
        $(this).addClass("hide");

        $("#container").removeClass("hide");
        $("#container").addClass("show");

        audio.play();
      }
    });

    $('#container').click(function() {
      $(this).removeClass("show");
      $(this).addClass("hide");

      $("#cover").removeClass("hide");
      $("#cover").addClass("show");

      audio.pause();
    });


    function flicker() {

      var maxFlick = 4,
      amount = Math.round(Math.random() * maxFlick),
      delta = 2,
      timer;

      var doneFlicks = 0;

      var flickInterval = setInterval(showHide, timer);

      function showHide() {
          timer = Math.round((Math.random() + delta) * 100)

          $(".flicker").show();
          $(".gif-sheitan").hide();

          var hide = setTimeout(function() {
              $(".gif-sheitan").show();
              $(".flicker").hide();
              doneFlicks++
          }, 4000)

          if (doneFlicks == amount) {
              clearInterval(flickInterval);
          }
      }       
    }

    setInterval(flicker, 4000);


    /*
    window.onLoad = Prep();

        var window_Height;
        var window_Width;
        
        var image_Element;
        var image_Height;
        var image_Width;
        
        var availSpace_V;
        var availSpace_H;


    function Prep(){
        window_Height = window.innerHeight;
        window_Width = window.innerWidth;
        
        image_Element = document.getElementById("random-img");
        image_Height = image_Element.clientHeight;
        image_Width = image_Element.clientWidth;
        
        availSpace_V = window_Height - image_Height;
        availSpace_H = window_Width - image_Width;
        
        var changeInterval = 3500;
        setInterval(moveImage, changeInterval);
    }
    
    function moveImage(){
        var randNum_V = Math.round(Math.random() * availSpace_V);
        var randNum_H = Math.round(Math.random() * availSpace_H);
        
        image_Element.style.top = randNum_V + "px";
        image_Element.style.left = randNum_H + "px";        
    }

    */


  },
  computed: {
  }
};
</script>

<style>
@font-face {
  font-family: Hanson;
  src: url(assets/font/Hanson-Bold.ttf);
}

@keyframes blinker {
  50% {
    opacity: 0;
    -webkit-text-stroke: 2px #1dffff;
  }
}

.blink-fast {
  animation: blinker 80ms linear infinite;
}

.blink-slow {
  animation: blinker 6s linear infinite;
}

body {
  font-family: Hanson, sans-serif;
  background: #000;
  margin: 0 auto;
  overflow: -moz-scrollbars-none;
  overflow-y: hidden;
  -ms-overflow-style: none;
  scrollbar-width: none;
}

body::-webkit-scrollbar { width: 0 !important }

:focus {
  outline: 0;
  background: rgb(0, 0, 0, 0);
}

.noselect {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

a {
    text-decoration: none;
}

a:link, a:visited {
  color: rgba(255,255,255,0.8);
}

.download-link {
  position: relative;
  left: 1vw;
  font-size: 1.5vw;
}

#app {
  font-family: Hanson, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin: 0 auto;
}

#cover {
  width: 100vw;
  height: 100vh;
}

.cover-overlay {
  width: 100vw;
  height: 100vh;
  position: absolute;
  background-color: rgba(0,0,0,0.7);
}

.cover-play {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 480px;
  height: 480px;
  max-width: 100%;  margin: 0 auto;
  margin-left: -240px;
  margin-top: -240px;
}

.show {
  visibility: visible;
  display: block;
}

.hide {
  visibility: hidden;
  display: none;
}

.img-sheitan {
  width: 100vw;
  height: 90vh;
  margin-top: 5vh;
  margin-bottom: 5vh;
}

.img-logo {
  position: absolute;
  width: 8vw;
  height: 7vh;
  left: 2%;
  bottom: 7%;
}

.img-cd {
  position: absolute;
  width: 6vw;
  height: 8vh;
  left: 14%;
  bottom: 7%;
}

.img-move {
  position: absolute;
  max-width: 400px;
  max-height: 400px;
}

.page-title {
  position: absolute;
  font-size: 16vw;
  top: 0px;
  left: 1%;
  margin: 0 auto;
  color: rgba(0,0,0,0);
  -webkit-text-stroke: 3px #fc7a78;
}

.track-title {
  position: absolute;
  font-size: 10vw;
  bottom: 5%;
  right: 2%;
  margin: 0 auto;
  color: rgba(0,0,0,0);
  -webkit-text-stroke: 3px #fc7a78;
}

.page-info {
  position: absolute;
  text-align: left;
  font-size: 14px;
  letter-spacing: 4px;
  left: 1%;
  bottom: 20%;
  color: rgba(255,255,255,0.8);
}

.shanghai {
  font-size:10vw;
}

#footer {
  width: 100%;
  position: absolute;
  bottom: 1%;
}

#copyright {
  font-size: 8px;
  letter-spacing: 4px;
  color: rgba(255,255,255,0.8);
}

@media (max-width: 768px) {
  #cover {
    width: 100vw;
    height: 100vh;
  }

  .cover-overlay {
    width: 100vw;
    height: 100vh;
    position: absolute;
    background-color: rgba(0,0,0,0.7);
  }

  .cover-play {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 240px;
    height: 240px;
    max-width: 100%; 
    margin: 0 auto;
    margin-left: -120px;
    margin-top: -120px;
  }

  .img-sheitan {
    width: 95vw;
    height: 90vh;
    margin-top: 5vh;
    margin-bottom: 5vh;
  }

  .img-logo {
    position: absolute;
    width: 8vw;
    height: 5vh;
    left: 5%;
    bottom: 7%;
  }

  .img-cd {
    position: absolute;
    width: 6vw;
    height: 8vh;
    left: 15%;
    bottom: 7%;
  }

  .page-title {
    position: absolute;
    font-size: 16vw;
    top: 5%;
    left: 3%;
    margin: 0 auto;
    color: rgba(0,0,0,0);
    -webkit-text-stroke: 2px #fc7a78;
  }

  .track-title {
    position: absolute;
    font-size: 10vw;
    bottom: 5%;
    right: 3%;
    margin: 0 auto;
    color: rgba(0,0,0,0);
    -webkit-text-stroke: 2px #fc7a78;
  }

  .page-info {
    position: absolute;
    text-align: left;
    font-size: 9px;
    letter-spacing: 4px;
    left: 5%;
    bottom: 18%;
    color: rgba(255,255,255,0.8);
  }

  .shanghai {
    font-size:8vw;
  }

  #footer {
    width: 100%;
    position: absolute;
    bottom: 0%;
  }
}

@media (max-width: 480px) {
  #cover {
    width: 100vw;
    height: 100vh;
  }

  .cover-overlay {
    width: 100vw;
    height: 100vh;
    position: absolute;
    background-color: rgba(0,0,0,0.7);
  }

  .cover-play {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 240px;
    height: 240px;
    max-width: 100%; 
    margin: 0 auto;
    margin-left: -120px;
    margin-top: -120px;
  }

  .img-sheitan {
    width: 95vw;
    height: 80vh;
    margin-top: 5vh;
    margin-bottom: 5vh;
  }

  .img-logo {
    position: absolute;
    width: 12vw;
    height: 5vh;
    left: 5%;
    bottom: 7%;
  }

  .img-cd {
    position: absolute;
    width: 12vw;
    height: 8vh;
    left: 22%;
    bottom: 7%;
  }

  .page-title {
    position: absolute;
    font-size: 16vw;
    top: 5%;
    left: 3%;
    margin: 0 auto;
    color: rgba(0,0,0,0);
    -webkit-text-stroke: 2px #fc7a78;
  }

  .track-title {
    position: absolute;
    font-size: 10vw;
    bottom: 5%;
    right: 4%;
    margin: 0 auto;
    color: rgba(0,0,0,0);
    -webkit-text-stroke: 2px #fc7a78;
  }

  .page-info {
    position: absolute;
    text-align: left;
    font-size: 9px;
    letter-spacing: 4px;
    left: 6%;
    bottom: 18%;
    color: rgba(255,255,255,0.8);
  }

  .shanghai {
    font-size:20vw;
  }

  .download-link {
    position: relative;
    left: 5vw;
    font-size: 5vw;
  }

  #copyright {
    font-size: 6px;
    letter-spacing: 4px;
    color: rgba(255,255,255,0.8);
  }
}

</style>
