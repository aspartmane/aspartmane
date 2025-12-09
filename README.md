<!-- Pixel-art floating cookie (no face, no crumbles) -->
<div class="cookie-wrap">
  <div class="pixel-cookie" aria-hidden="true"></div>
</div>

<style>
/* container to center */
.cookie-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 18px 0;
}

/* Pixel-cookie */
.pixel-cookie{
  width: 220px;              /* change size here */
  height: 220px;
  border-radius: 50%;        /* keep circular silhouette */
  /* radial gradient creates the cookie color + subtle rim;
     background-size set small to force the "pixel" block repetition */
  background-image:
    radial-gradient(circle at 50% 42%, #e8b77a 55%, #cf8b46 57%),
    radial-gradient(circle at 50% 50%, rgba(0,0,0,0.06), transparent 62%);
  background-repeat: repeat;
  background-size: 14px 14px; /* <--- controls pixel block size; smaller == more detail */
  box-shadow:
    0 6px 0 0 rgba(0,0,0,0.06) inset,   /* subtle inner depth */
    0 18px 30px rgba(0,0,0,0.25);      /* outer shadow */
  image-rendering: pixelated;  /* make the repeated pattern look crisp/pixelated */
  transform-origin: center;
  /* small 3D feel */
  will-change: transform;
  /* animations */
  animation:
    float 3.8s ease-in-out infinite,
    slow-tilt 6s ease-in-out infinite;
}

/* optional thin darker rim to reinforce pixel-art look */
.pixel-cookie::before{
  content: "";
  position: absolute;
  width: 220px;
  height: 220px;
  left: calc(50% - 110px);   /* centers the pseudo element relative to page */
  top: 18px;
  border-radius: 50%;
  pointer-events: none;
  background-image: radial-gradient(circle at 50% 50%, rgba(0,0,0,0.0) 64%, rgba(0,0,0,0.08) 66%);
  background-size: 14px 14px;
  image-rendering: pixelated;
  transform: translateZ(0);
  mix-blend-mode: multiply;
  animation: same-float 3.8s ease-in-out infinite;
}

/* float up/down and scale slightly for bobbing */
@keyframes float {
  0%   { transform: translateY(0) scale(1); }
  50%  { transform: translateY(-12px) scale(1.02); }
  100% { transform: translateY(0) scale(1); }
}

/* slow rotate/tilt for liveliness */
@keyframes slow-tilt {
  0%   { transform: rotate(0deg); }
  25%  { transform: rotate(-2deg); }
  50%  { transform: rotate(0.8deg); }
  75%  { transform: rotate(-1deg); }
  100% { transform: rotate(0deg); }
}

/* keep the pseudo-element animation in sync */
@keyframes same-float {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-12px); }
  100% { transform: translateY(0); }
}

/* make it responsive (optional) */
@media (max-width: 520px){
  .pixel-cookie, .pixel-cookie::before {
    width: 140px;
    height: 140px;
    left: calc(50% - 70px);
  }
  .pixel-cookie { background-size: 10px 10px; }
  .pixel-cookie::before { background-size: 10px 10px; }
}
</style>
