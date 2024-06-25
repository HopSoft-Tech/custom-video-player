# Custom Video Player

Welcome to the Custom Video Player project! This project is a basic video player built using HTML, CSS, and JavaScript. It includes essential functionalities such as play/pause, a stop button, a progress bar using the input range element, and a timer to display the current playback time.

## Features

- **Play/Pause Button**: Toggle between playing and pausing the video.
- **Stop Button**: Stop the video and reset the playback to the beginning.
- **Progress Bar**: Use the input range element to show and control the video progress.
- **Timer**: Display the current playback time in minutes and seconds.

## Demo

<!-- Add a screenshot of your project -->

![Video Player Screenshot](screenshot.png)

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Code Overview](#code-overview)
  - [HTML](#html)
  - [JavaScript](#javascript)
- [Contributing](#contributing)
- [License](#license)

## Installation

To get a local copy up and running, follow these simple steps:

1. **Clone the repo**:

   ```sh
   git clone https://github.com/HopSoft-Tech/custom-video-player.git
   ```

2. **Open the project folder**:

   ```sh
   cd custom-video-player
   ```

3. **Open `index.html` in your browser**.

## Usage

1. **Play/Pause**: Click the play/pause button to start or pause the video.
2. **Stop**: Click the stop button to stop the video and reset playback to the beginning.
3. **Progress Bar**: Drag the progress bar to seek through the video.
4. **Timer**: The timer updates automatically to show the current playback time.

## Code Overview

### HTML

The HTML file contains the structure of the video player, including the video element, controls, and the progress bar.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Custom Video Player</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css"
      integrity="sha512-SnH5WK+bZxgPHs44uWIX+LLJAJ9/2PkPKZ5QiAj6Ta86w+fsb2TkcmfRyVX3pBnMFcV7oQPJkl9QevSCWr3W6A=="
      crossorigin="anonymous"
      referrerpolicy="no-referrer"
    />
    <link rel="stylesheet" href="style.css" />
    <script src="app.js" defer></script>
  </head>
  <body>
    <video
      src="media/clouds.mov"
      poster="media/poster.png"
      id="video"
      class="screen"
    ></video>
    <div class="controls">
      <button class="btn" id="play">
        <i class="fa fa-play fa-2x"></i>
      </button>
      <button class="btn" id="stop">
        <i class="fa fa-stop fa-2x"></i>
      </button>
      <input
        type="range"
        id="progress"
        class="progress"
        min="0"
        max="100"
        step="0.1"
        value="0"
      />
      <span class="timestamp" id="timestamp">00:00</span>
    </div>
  </body>
</html>
```

### JavaScript

The JavaScript file contains the functionality of the video player, including play/pause, stopping the video, updating the progress bar, and displaying the timer.

```js
/* app.js */
const video = document.getElementById("video");
const play = document.getElementById("play");
const stop = document.getElementById("stop");
const progress = document.getElementById("progress");
const timestamp = document.getElementById("timestamp");

function playPause() {
  if (video.paused) {
    video.play();
  } else {
    video.pause();
  }
}

function stopVideo() {
  video.pause();
  video.currentTime = 0;
}

function updateIcon() {
  if (video.paused) {
    play.innerHTML = "<i class='fa fa-play fa-2x'></i>";
  } else {
    play.innerHTML = "<i class='fa fa-pause fa-2x'></i>";
  }
}

function updateProgress() {
  progress.value = (video.currentTime / video.duration) * 100;

  // Get Minutes
  let minutes = Math.floor(video.currentTime / 60);
  if (minutes < 10) {
    minutes = "0" + String(minutes);
  }

  let seconds = Math.floor(video.currentTime % 60);
  if (seconds < 10) {
    seconds = "0" + String(seconds);
  }

  timestamp.innerHTML = `${minutes}:${seconds}`;
}

function setProgress() {
  video.currentTime = (+progress.value * video.duration) / 100;
}

video.addEventListener("click", playPause);
video.addEventListener("play", updateIcon);
video.addEventListener("pause", updateIcon);
video.addEventListener("timeupdate", updateProgress);

play.addEventListener("click", playPause);
stop.addEventListener("click", stopVideo);
progress.addEventListener("click", setProgress);
```

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.
