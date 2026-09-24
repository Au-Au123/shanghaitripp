// State & Navigation Controller
(function() {
  'use strict';

  const state = {
    currentHour: 10,
    selectedHour: 10,
    currentTab: 'today',
    daySubTab: 'personal',
    friends: [],
    hours: [],
    userPhotos: {},
    countdownSeconds: 23 * 60 + 41,
    cameraStream: null,
    facingMode: 'environment',
    capturedTempPhoto: null,
    recap: {
      active: false,
      mode: 'normal',
      items: [],
      currentIndex: 0,
      timer: null,
      audioPlaying: false,
      isPaused: false
    }
  };

  // Audio Synthesizer (Zero MP3 Dependencies)
  let audioCtx = null;
  function getAudioContext() {
    if (!audioCtx) {
      const AudioContext = window.AudioContext || window.webkitAudioContext;
      if (AudioContext) audioCtx = new AudioContext();
    }
    if (audioCtx && audioCtx.state === 'suspended') audioCtx.resume();
    return audioCtx;
  }

  function playShutterSound() {
    const ctx = getAudioContext();
    if (!ctx) return;
    const osc = ctx.createOscillator();
    const gain = ctx.createGain();
    osc.type = 'triangle';
    osc.frequency.setValueAtTime(800, ctx.currentTime);
    osc.frequency.exponentialRampToValueAtTime(100, ctx.currentTime + 0.08);
    gain.gain.setValueAtTime(0.5, ctx.currentTime);
    gain.gain.exponentialRampToValueAtTime(0.01, ctx.currentTime + 0.08);
    osc.connect(gain);
    gain.connect(ctx.destination);
    osc.start();
    osc.stop(ctx.currentTime + 0.08);
  }

  // Camera Management & WebRTC
  async function openCameraModal() {
    const modal = document.getElementById('cameraModal');
    const video = document.getElementById('cameraVideo');
    if (modal) modal.classList.add('active');

    try {
      if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
        state.cameraStream = await navigator.mediaDevices.getUserMedia({
          video: { facingMode: state.facingMode, width: { ideal: 1080 }, height: { ideal: 1920 } },
          audio: false
        });
        if (video) {
          video.srcObject = state.cameraStream;
          video.play();
        }
      }
    } catch (err) {
      console.warn("Camera fallback active (file upload / preset snaps):", err);
    }
  }

  // Submit Photo & Reveal Grid
  function submitPhoto() {
    const hObj = state.hours[state.selectedHour];
    const timestamp = `${String(hObj.hour).padStart(2, '0')}:14 ${hObj.hour < 12 ? 'AM' : 'PM'}`;
    state.userPhotos[state.selectedHour] = {
      photoUrl: state.capturedTempPhoto,
      timestamp,
      caption: "Our 24H photo in Shanghai!"
    };
    if (hObj.submissions.auau) {
      hObj.submissions.auau.submitted = true;
      hObj.submissions.auau.photoUrl = state.capturedTempPhoto;
      hObj.submissions.auau.timestamp = timestamp;
    }
    localStorage.setItem('24h_user_photos', JSON.stringify(state.userPhotos));
    triggerConfetti();
    document.getElementById('photoReviewModal').classList.remove('active');
    document.getElementById('celebrationOverlay').classList.add('active');
  }

  // TikTok/Reels Recap Player
  function startRecapPlayer(mode = 'normal') {
    state.recap.mode = mode;
    state.recap.active = true;
    state.recap.currentIndex = 0;
    // Build slide queue from all submitted hours & friends...
    document.getElementById('videoPlayerModal').classList.add('active');
    showRecapSlide(0);
  }

  // (Listeners, timeline nodes, and DOM binding omitted for brevity; see zip for complete file)
})();
