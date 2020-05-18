## WebRTC study: remote camera / screen

A minimal setup for transmitting / receiving canvas as a video signal using WebRTC.

### Requirements

* node `v10.14` or higher
* npm
* (optional) [ngrok](https://ngrok.com) for testing over the internet

### Running the example locally

```sh
npm i
npm start

# open these urls in your browser
open http://localhost:3000/canvas.html
open http://localhost:3000/screen.html
```

### Running the example over the network

```
npm i
npm start

# in a separate terminal / tab
ngrok http 3000

# open on different devices
open https://${NGROK_URL}/canvas.html
open https://${NGROK_URL}/screen.html
```

### What's included

* Server
    * Serves static files (.html & .js)
    * Acts as a signalling server, communicating with clients over
      websockets

* Camera page `/canvas.html`
    * Acts as an initializer peer
    * Streams canvas signal over WebRTC

* Screen page `/screen.html`
    * Receives & displays camera signal

### Problems

I've noticed google's STUN server a little unreliable.  Not sure why, I tried different STUN servers, with varying success.

### Acknowledgements

* This project is basically a copy of
  [webrtc-video-broadcast](https://github.com/Basscord/webrtc-video-broadcast)
  by [Basscord](https://github.com/Basscord).
  Differences from the original:

    * I'm using async/await instead of promises
    * `RTCPeerConnection.ontrack` instead of deprecated
      `RTCPeerConnection.onaddstrea`
    * Websockets instead of socket.io.

* This fork is almost an exact copy of [webrtc-study-broadcaster](https://github.com/flpvsk/webrtc-study-broadcaster).  Differences are:
    * I'm streaming a canvas input instead of a camera input.  Just as a test.
  
