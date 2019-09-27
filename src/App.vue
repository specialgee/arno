<style lang="css">
@import './assets/css/style.css';
</style>

<template>
  <div id="app">
    <!--<HelloWorld msg="Welcome to Your Vue.js App" />-->
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
        .////////////////////////////<br>
        ARTIST: ARNO<br>
        TRACK: SIREN<br>
        3D: <a href="https://www.instagram.com/joli_gillet/" target="_blank">JOLI_GILLET</a><br>
        CODE: <a href="https://www.instagram.com/special.gee/" target="_blank">SPECIAL.GEE</a><br>
        <!--<a href="SIREN.rar" class="download-link" download>DOWNLOAD</a>-->
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
    var sound = new Howl({
      src: ["SIREN.mp3", "SIREN.ogg"],
      loop: true
    });

    var isSoundLoaded = false;

    // Clear listener after first call.
    sound.once('load', function(){
      isSoundLoaded = true;
    });

    $('#cover').click(function() {
      if (isSoundLoaded) {
        $(this).removeClass("show");
        $(this).addClass("hide");

        $("#container").removeClass("hide");
        $("#container").addClass("show");
        
        sound.play();
      }
    });

    $('#container').click(function() {
      $(this).removeClass("show");
      $(this).addClass("hide");

      $("#cover").removeClass("hide");
      $("#cover").addClass("show");

      sound.pause();
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




  },
  computed: {
  }
};
</script>

