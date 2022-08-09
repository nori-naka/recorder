<script setup>
const emit = defineEmits(["on_switch"]);

const on_switch = () => emit("on_switch", onoff.checked);
const force_off = () => { onoff.checked = true }

defineExpose({
  force_off
})

</script>

<template>
  <div class="btn-switch btn-switch-wrap">
    <input type="checkbox" v-model="onoff" id="onoff" name="onoff" checked @change="on_switch">
    <div class="btn-switch-bg">
      <label class="btn-switch-in" for="onoff">
        <span class="on">録画</span>
        <span class="off">停止</span>
      </label>
    </div>
  </div>
</template>

<style>
*,
*:before,
*:after {
  -webkit-box-sizing: inherit;
  box-sizing: inherit;
}

html {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  font-size: 62.5%;
}

.btn,
a.btn,
button.btn {
  font-size: 1.6rem;
  font-weight: 700;
  line-height: 1.5;
  position: relative;
  display: inline-block;
  padding: 1rem 4rem;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  -webkit-transition: all 0.3s;
  transition: all 0.3s;
  text-align: center;
  vertical-align: middle;
  text-decoration: none;
  letter-spacing: 0.1em;
  color: #212529;
  border-radius: 0.5rem;
}

.btn-switch {
  width: 148px;
  height: 250px;
  margin: 0 auto;
  padding: 20px;

  border-radius: 10px;
  background: -webkit-gradient(
    linear,
    left top,
    left bottom,
    from(#444),
    to(#222)
  );
  background: -webkit-linear-gradient(top, #444, #222);
  background: linear-gradient(180deg, #444, #222);
  -webkit-box-shadow: 0 0 0 8px rgba(0, 0, 0, 0), 0 0 3px 1px black,
    inset 0 8px 4px -8px white;
  box-shadow: 0 0 0 8px rgba(0, 0, 0, 0), 0 0 3px 1px black,
    inset 0 8px 4px -8px white;
}

.btn-switch input {
  display: none;
}

.btn-switch-bg {
  width: 108px;
  height: 210px;
  padding: 4px 4px;

  -webkit-transition: all 0.2s;

  transition: all 0.2s;

  border-radius: 5px;
  background-color: #370305;
  background-image: -webkit-linear-gradient(
      0deg,
      transparent 30%,
      transparent 70%
    ),
    -webkit-linear-gradient(0deg, rgba(150, 150, 150, 0) 30%, rgba(
            150,
            150,
            150,
            0.1
          )
          50%, rgba(150, 150, 150, 0) 70%);
  -webkit-box-shadow: 30px 30px 30px -20px rgba(0, 0, 0, 0.3),
    -30px 30px 30px -20px rgba(0, 0, 0, 0.3), 0 30px 30px 0 rgba(0, 0, 0, 0.3),
    inset 0 -1px 0 0 #333;
  box-shadow: 30px 30px 30px -20px rgba(0, 0, 0, 0.3),
    -30px 30px 30px -20px rgba(0, 0, 0, 0.3), 0 30px 30px 0 rgba(0, 0, 0, 0.3),
    inset 0 -1px 0 0 #333;
}

.btn-switch-in {
  position: relative;

  display: block;

  width: 100px;
  height: 178px;

  -webkit-transition: all 0.2s;

  border-radius: 10px;
  background-image: -webkit-gradient(
    linear,
    left bottom,
    left top,
    from(#8c1313),
    color-stop(84%, #ff2a2a)
  );
  background-image: -webkit-linear-gradient(bottom, #8c1313 0%, #ff2a2a 84%);
  background-image: linear-gradient(to top, #8c1313 0%, #ff2a2a 84%);
  -webkit-box-shadow: inset 0 20px 60px -200px rgba(240, 0, 0, 0.2),
    inset 8px 6px 5px -7px #f95253, inset -8px 6px 5px -7px #f95253,
    inset 0 -3px 2px -2px rgba(200, 200, 200, 0.5), 0 3px 3px -2px #f95253,
    inset 0 230px 60px -200px rgba(255, 255, 255, 0.2),
    0 -20px 50px 10px rgba(240, 0, 0, 0.3);
  box-shadow: inset 0 20px 60px -200px rgba(240, 0, 0, 0.2),
    inset 8px 6px 5px -7px #f95253, inset -8px 6px 5px -7px #f95253,
    inset 0 -3px 2px -2px rgba(200, 200, 200, 0.5), 0 3px 3px -2px #f95253,
    inset 0 230px 60px -200px rgba(255, 255, 255, 0.2),
    0 -20px 50px 10px rgba(240, 0, 0, 0.3);
}

.btn-switch-in .on {
  font-size: 20px;
  font-weight: bold;

  position: absolute;
  top: 25px;
  left: 0;

  width: 100%;

  -webkit-transition: all 0.1s ease;

  transition: all 0.1s ease;
  text-align: center;

  opacity: 1;
  color: #fff;
  text-shadow: 0 0 5px #ffc7c7, 0 0 5px #ffc7c7, 0 0 5px #ffc7c7,
    0 0 5px #ffc7c7;
}

.btn-switch-in .off {
  font-size: 20px;
  font-weight: bold;

  position: absolute;
  bottom: 20px;
  left: 0;

  width: 100%;

  -webkit-transition: all 0.3s ease;

  transition: all 0.3s ease;
  -webkit-transform: scaleY(0.9);
  transform: scaleY(0.9);
  text-align: center;

  opacity: 0.5;
  color: #500101;
}

.btn-switch input:checked + .btn-switch-bg .on {
  height: 20px;

  -webkit-transform: scaleY(0.85);

  transform: scaleY(0.85);

  opacity: 0.6;
  color: #500101;
  text-shadow: none;
}

.btn-switch input:checked + .btn-switch-bg .off {
  -webkit-transform: scaleY(1);
  transform: scaleY(1);

  opacity: 0.5;
}

.btn-switch input:checked + .btn-switch-bg .btn-switch-in {
  margin-top: 20px;

  background-image: -webkit-gradient(
    linear,
    left bottom,
    left top,
    from(#f95253),
    color-stop(74%, #b40000)
  );

  background-image: -webkit-linear-gradient(bottom, #f95253 0%, #b40000 74%);

  background-image: linear-gradient(to top, #f95253 0%, #b40000 74%);
  -webkit-box-shadow: inset 1px 1px 1px 1px rgba(255, 255, 255, 0.5),
    inset 8px -4px 5px -7px black, inset -8px -4px 5px -7px black,
    0 -3px 8px -4px rgba(250, 250, 250, 0.4), inset 0 3px 4px -2px #0a0a0a,
    inset 0 280px 40px -200px rgba(0, 0, 0, 0.2),
    inset 0 -200px 40px -200px rgba(180, 180, 180, 0.2);
  box-shadow: inset 1px 1px 1px 1px rgba(255, 255, 255, 0.5),
    inset 8px -4px 5px -7px black, inset -8px -4px 5px -7px black,
    0 -3px 8px -4px rgba(250, 250, 250, 0.4), inset 0 3px 4px -2px #0a0a0a,
    inset 0 280px 40px -200px rgba(0, 0, 0, 0.2),
    inset 0 -200px 40px -200px rgba(180, 180, 180, 0.2);
}

.btn-switch input:checked + .btn-switch-bg {
  background-image: -webkit-linear-gradient(90deg, #000 30%, transparent 70%),
    -webkit-linear-gradient(180deg, rgba(250, 250, 250, 0) 0%, rgba(
            250,
            250,
            250,
            0.5
          )
          50%, rgba(150, 150, 150, 0) 100%);
  -webkit-box-shadow: 30px 30px 30px -20px rgba(0, 0, 0, 0.1),
    -30px 30px 30px -20px rgba(0, 0, 0, 0.1), 0 30px 30px 0 rgba(0, 0, 0, 0.2),
    inset 0 1px 2px 0 rgba(0, 0, 0, 0.6);
  box-shadow: 30px 30px 30px -20px rgba(0, 0, 0, 0.1),
    -30px 30px 30px -20px rgba(0, 0, 0, 0.1), 0 30px 30px 0 rgba(0, 0, 0, 0.2),
    inset 0 1px 2px 0 rgba(0, 0, 0, 0.6);
}

#onoff,
.btn-switch-bg,
.btn-switch-in,
.on,
.off {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

</style>