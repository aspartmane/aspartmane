<!-- awee cookie! -->
<div class="cookie-wrap">
  <div class="pixel-cookie" aria-hidden="true"></div>
</div>

<style>
/* center */
.cookie-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 18px 0;
}

/* pixel??? */
.pixel-cookie{
  width: 220px;              /* change size here */
  height: 220px;
  border-radius: 50%;        
  background-image:
    radial-gradient(circle at 50% 42%, #e8b77a 55%, #cf8b46 57%),
    radial-gradient(circle at 50% 50%, rgba(0,0,0,0.06), transparent 62%);
  background-repeat: repeat;
  background-size: 14px 14px; /* <--- controls pixel block size */
  box-shadow:
    0 6px 0 0 rgba(0,0,0,0.06) inset,   /* crispppp */
    0 18px 30px rgba(0,0,0,0.25);     
  image-rendering: pixelated;  
  transform-origin: center;
  /* 3D */
  will-change: transform;
  /* animation */
  animation:
    float 3.8s ease-in-out infinite,
    slow-tilt 6s ease-in-out infinite;
}

/* optional shi */
.pixel-cookie::before{
  content: "";
  position: absolute;
  width: 220px;
  height: 220px;
  left: calc(50% - 110px);   
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

/* float  */
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

@keyframes same-float {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-12px); }
  100% { transform: translateY(0); }
}

/* responsive */
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
