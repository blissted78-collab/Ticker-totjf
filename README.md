<!doctype html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<style>
  body{margin:0;background:transparent;}
  .wrap{
    width:100%; overflow:hidden;
    background:linear-gradient(#1b1409,#2a1f10,#1b1409);
    border-top:1px solid rgba(255,200,120,.35);
    border-bottom:1px solid rgba(255,200,120,.35);
    box-shadow:inset 0 0 18px rgba(255,170,60,.25);
    padding:8px 0;
  }
  .fade:before,.fade:after{
    content:""; position:absolute; top:0; bottom:0; width:40px; pointer-events:none;
  }
  .fade{position:relative;}
  .fade:before{left:0;background:linear-gradient(to right, rgba(0,0,0,.75), rgba(0,0,0,0));}
  .fade:after{right:0;background:linear-gradient(to left, rgba(0,0,0,.75), rgba(0,0,0,0));}

  .track{
    display:flex; width:max-content; gap:2.5rem;
    will-change:transform;
    animation:scroll 24s linear infinite;
    transform:translate3d(0,0,0);
  }
  .item{
    white-space:nowrap;
    font:600 14px Georgia,serif;
    letter-spacing:.08em;
    color:#ffcc88;
    text-shadow:0 0 6px rgba(255,190,90,.65),0 0 12px rgba(255,160,60,.45);
  }
  @keyframes scroll{to{transform:translate3d(-50%,0,0)}}
  @media (prefers-reduced-motion: reduce){.track{animation:none}}
</style>
</head>

<body>
  <div class="wrap fade">
    <div class="track" id="t"></div>
  </div>

<script>
  const params = new URLSearchParams(location.search);
  const msgRaw = (params.get("msg") || "Service to All • You are not walking alone • Progress, not perfection • Breathe. Focus. Continue.").trim();

  const items = msgRaw
    .split("•")
    .map(s => s.trim())
    .filter(Boolean);

  const line = items.length
    ? items.map(s => `✦ ${s} ✦`).join("   ")
    : "✦ Service to All ✦";

  // Duplicate for seamless loop
  document.getElementById("t").innerHTML =
    `<div class="item">${line}</div><div class="item">${line}</div>`;
</script>
</body>
</html>
