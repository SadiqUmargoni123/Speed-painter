const upload = document.getElementById("upload");
const startBtn = document.getElementById("startBtn");
const downloadBtn = document.getElementById("downloadBtn");
const speedSlider = document.getElementById("speed");
const styleSelect = document.getElementById("style");
const handToggle = document.getElementById("handToggle");
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

let img = new Image();
let recorder, chunks = [];
let handImg = new Image();
handImg.src = "hand.png";

// Load uploaded image
upload.addEventListener("change", e => {
  const file = e.target.files[0];
  if (!file) return;
  const reader = new FileReader();
  reader.onload = function(ev) {
    img.onload = () => {
      canvas.width = img.width;
      canvas.height = img.height;
      ctx.drawImage(img, 0, 0);
    };
    img.src = ev.target.result;
  };
  reader.readAsDataURL(file);
});

// Simulated drawing
function drawImageStepByStep(speed, style, showHand) {
  let x = 0, y = 0, step = 5;
  const interval = setInterval(() => {
    let w = step, h = step;

    // Apply style
    if (style === "sketch") {
      ctx.strokeStyle = "black";
      ctx.strokeRect(x, y, w, h);
    } else if (style === "ink") {
      ctx.fillStyle = "black";
      ctx.fillRect(x, y, w, h);
    } else if (style === "color") {
      let pixel = ctx.getImageData(x, y, 1, 1).data;
      ctx.fillStyle = `rgb(${pixel[0]},${pixel[1]},${pixel[2]})`;
      ctx.fillRect(x, y, w, h);
    } else {
      ctx.drawImage(img, x, y, w, h, x, y, w, h);
    }

    // Hand overlay
    if (showHand) {
      ctx.drawImage(handImg, x - 30, y - 30, 60, 60);
    }

    x += speed;
    if (x >= img.width) {
      x = 0;
      y += speed;
    }
    if (y >= img.height) {
      clearInterval(interval);
      stopRecording();
      downloadBtn.disabled = false;
    }
  }, 30);
}

// Start recording + drawing
startBtn.addEventListener("click", () => {
  chunks = [];
  let stream = canvas.captureStream(30); // 30 FPS
  recorder = new MediaRecorder(stream, { mimeType: "video/webm" });
  recorder.ondataavailable = e => chunks.push(e.data);
  recorder.onstop = saveVideo;
  recorder.start();

  ctx.clearRect(0, 0, canvas.width, canvas.height);
  drawImageStepByStep(
    parseInt(speedSlider.value),
    styleSelect.value,
    handToggle.checked
  );
});

// Stop recording
function stopRecording() {
  recorder.stop();
}

// Save as video
function saveVideo() {
  const blob = new Blob(chunks, { type: "video/webm" });
  const url = URL.createObjectURL(blob);
  downloadBtn.onclick = () => {
    const a = document.createElement("a");
    a.href = url;
    a.download = "drawit.webm";
    a.click();
  };
}