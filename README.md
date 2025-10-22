<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A.I.O Explorer - Stories & Games</title>
<style>
body { margin:0; font-family:'Poppins',sans-serif; background: linear-gradient(135deg,#b7f0c1,#a7e0ff,#fff4a3,#ffcf91); background-size:400% 400%; animation:gradientShift 15s ease infinite; color:#083a2a; text-align:center; }
@keyframes gradientShift {0%{background-position:0% 50%;}50%{background-position:100% 50%;}100{background-position:0% 50%;}}
header{background:linear-gradient(to right, rgba(45,204,112,0.8), rgba(64,147,230,0.8)); padding:35px 0 25px 0; box-shadow:0 4px 20px rgba(0,0,0,0.25);}
h1{font-size:3rem;color:white;text-shadow:0 0 15px rgba(0,0,0,0.3); margin-bottom:10px;}
.subtitle{color:#f5fff5; font-size:1.2rem; max-width:800px;margin:0 auto; line-height:1.6;text-shadow:0 0 8px rgba(0,0,0,0.3);}
.folder-container{display:flex; justify-content:center; gap:30px; margin:30px 0; flex-wrap:wrap;}
.folder{background:linear-gradient(145deg,#f9d976,#f39f86); padding:25px 40px; border-radius:15px; box-shadow:0 4px 10px rgba(0,0,0,0.2); cursor:pointer; transition:all 0.3s ease; font-weight:bold; font-size:1.3rem; color:#083a2a;}
.folder:nth-child(2){background:linear-gradient(145deg,#8fd3f4,#84fab0);}
.folder:hover{transform:translateY(-5px) scale(1.05); box-shadow:0 8px 20px rgba(0,0,0,0.3);}
.story-section{display:none; margin:40px auto; max-width:900px; padding:20px;}
.story{background:rgba(255,255,255,0.95); border-radius:20px; overflow:hidden; box-shadow:0 4px 15px rgba(0,0,0,0.2); margin-bottom:40px; transition:all 0.3s ease; text-align:left;}
.story-content{padding:20px;}
.story h2{color:#046b5c; font-size:1.6rem; margin:0;}
.story p{line-height:1.7; font-size:1.05rem; color:#083a2a; margin-top:10px;}
.sdg-gallery{display:grid; grid-template-columns:repeat(auto-fit, minmax(150px,1fr)); gap:25px; padding:40px; max-width:1200px; margin:0 auto 60px auto;}
.sdg-card{background:rgba(255,255,255,0.9); border-radius:20px; box-shadow:0 4px 10px rgba(0,0,0,0.2); padding:15px; transition:all 0.3s ease; cursor:pointer;}
.sdg-card:hover{transform:translateY(-5px) scale(1.03); box-shadow:0 8px 20px rgba(0,0,0,0.3);}
.sdg-card img{width:100%; height:auto; border-radius:10px;}
.sdg-number{font-weight:700; margin-top:10px; color:#046b5c; font-size:1.2rem;}
.sdg-name{font-size:1rem; color:#083a2a; margin-bottom:10px;}
footer{padding:20px; background:linear-gradient(to right, rgba(45,204,112,0.8), rgba(64,147,230,0.8)); color:white; font-size:0.9rem;}
.modal{display:none; position:fixed; z-index:1000; left:0; top:0; width:100%; height:100%; background-color:rgba(0,0,0,0.6); justify-content:center; align-items:center;}
.modal-content{background:white; padding:30px; border-radius:15px; max-width:600px; text-align:center; box-shadow:0 4px 20px rgba(0,0,0,0.3);}
.close{float:right; font-size:1.5rem; font-weight:bold; cursor:pointer; color:#084c26;}
.games-panel{display:none; padding:20px; max-width:900px; margin:0 auto;}
.game-slot{background:rgba(255,255,255,0.9); border-radius:15px; margin:10px 0; padding:15px; cursor:pointer; transition:0.3s; box-shadow:0 4px 10px rgba(0,0,0,0.2);}
.game-slot:hover{transform:scale(1.02); box-shadow:0 8px 15px rgba(0,0,0,0.3);}
canvas{border:3px solid #046b5c; display:block; margin:10px auto; background:#1a1a1a;}
button{padding:8px 15px; font-size:1rem; margin:5px;}
</style>
</head>
<body>

<header>
  <h1>A.I.O Explorer</h1>
  <p class="subtitle">Empowering young minds through fun games, moral stories, and awareness adventures!</p>
</header>

<div class="folder-container">
  <div class="folder" onclick="showGames()">🎮 Games</div>
  <div class="folder" onclick="showStories()">📘 Stories</div>
</div>

<!-- Games Panel -->
<section class="games-panel" id="gamesPanel">
  <h2>Pick a Game</h2>
  <div class="game-slot" onclick="startJumpingDot()">Jumping Dot 🎯</div>
  <div class="game-slot" onclick="alert('Color Ball coming soon!')">Color Ball 🌈</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Catch the Star ⭐</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Whack the Mole 🐹</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Maze Runner 🌀</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Memory Match 🧠</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Fruit Slice 🍎</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Ping Pong 🏓</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Ball Bounce 🏀</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Snake Game 🐍</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Tic Tac Toe ❌⭕</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Flappy Dot 🐦</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Rocket Launch 🚀</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Catch Water 💧</div>
  <div class="game-slot" onclick="alert('Coming Soon!')">Balloon Pop 🎈</div>

  <canvas id="gameCanvas" width="360" height="600"></canvas>
  <div id="score">Score: 0</div>
  <label for="ballColor">Ball Color:</label>
  <input type="color" id="ballColor" value="#ffd600" onchange="changeBallColor(this.value)">
  <br>
  <button onclick="restartJumpingDot()">Restart Game</button>
  <button onclick="stopGame()">Back</button>
</section>

<!-- Story Section -->
<section class="story-section" id="storySection">
  <h2 style="text-align:center; color:#046b5c; margin-bottom:30px;">Sustainable Development Goals Stories</h2>
  <div class="sdg-gallery" id="sdgGallery"></div>
  <div class="modal" id="sdgModal">
    <div class="modal-content">
      <span class="close" onclick="closeModal()">&times;</span>
      <h2 id="modalTitle"></h2>
      <p id="modalDescription"></p>
    </div>
  </div>
</section>

<footer>
  © 2025 A.I.O Explorer | Inspired by the UN Sustainable Development Goals
</footer>

<script>
// Show panels
function showGames(){document.getElementById('gamesPanel').style.display='block'; document.getElementById('storySection').style.display='none'; stopGame();}
function showStories(){document.getElementById('storySection').style.display='block'; document.getElementById('gamesPanel').style.display='none'; stopGame();}

// SDGs stories
const sdgs = [
{num:1,name:"No Poverty",desc:"In the small village of Sarana, nestled in the shadow of a changing climate, generational poverty had been a constant companion. For centuries, families relied on a single, rain-fed crop, making them vulnerable to frequent droughts. One family, led by the young widow Elara, refused to accept this fate. Driven by the need to feed her two children, Elara joined a local micro-lending group. With a small loan, she invested not in crops, but in chickens. The eggs provided both a source of protein for her family and a steady income. As her business grew, she taught other villagers how to raise chickens, and the cooperative expanded to include vegetable gardens using innovative water-saving techniques. Elara's single act of innovation blossomed into a village-wide movement, transforming a community from one of scarcity and dependence into one of resilience and self-sufficiency, pulling families out of poverty for good."},
{num:2,name:"Zero Hunger",desc:"The arid lands of Somalia, plagued by prolonged drought, once left nomadic pastoralists and their families on the brink of famine. A young photojournalist, Karel Prinsloo, documented the plight of these communities, highlighting the breakdown of terrestrial ecosystems that threatened their way of life. The international attention his work garnered led the UN Food and Agricultural Organization (FAO) to work with these pastoralists. Instead of traditional aid, the FAO provided sustainable farming and livestock management training, empowering the community with the knowledge to thrive in their challenging environment. This story illustrates how documenting a crisis can foster international partnerships and action, turning the tide on food insecurity and helping communities adapt to climate change."},
{num:3,name:"Good Health and Well-being",desc:"A young doctor, Ben, recognized that many people in rural communities lacked access to basic medical services. He launched a mobile clinic, traveling to remote areas to provide vaccinations, health screenings, and education on sanitation. His team's arrival was a cause for celebration in each village, bringing hope and healing. By addressing preventable diseases and focusing on community education, Ben's mobile clinic transformed healthcare access, leading to a significant drop in preventable illnesses and a rise in overall well-being. This story highlights the power of grassroots efforts in bridging healthcare disparities and ensuring that good health is not a privilege, but a right for all."},
{num:4,name:"Quality Education",desc:"In a conflict-ridden region, many children were forced to abandon their education. Teacher Sarah refused to accept this reality and, in a refugee camp, established a makeshift classroom using limited resources. Despite the immense challenges, she created a safe space where children could learn, share stories, and rediscover their lost sense of normalcy. Her unwavering dedication eventually drew the attention of aid organizations and international partners, leading to the establishment of permanent school structures and educational programs. This story, much like the inspiring example of Malala Yousafzai, underscores how one person's determination can lead to systemic change, ensuring that children, even in the most vulnerable situations, have access to a quality education."},
{num:5,name:"Gender Equality",desc:"In a patriarchal society where girls' education was not prioritized, a young girl named Amina excelled in her studies, becoming a beacon of hope for her community. Initially, her father was hesitant to support her pursuit of higher education, but Amina's achievements eventually won him over, and he became her strongest advocate. Amina's journey to college and a leadership role inspired other families to invest in their daughters' education, challenging outdated gender stereotypes. Her success not only changed her life but also shifted the community's perspective, proving that empowering girls is a powerful catalyst for change."},
{num:6,name:"Clean Water and Sanitation",desc:"In a village suffering from contaminated water, a teenage engineer, Leo, used his skills to design a low-cost water filtration system. He worked with the community to implement the system, and within months, waterborne diseases became a thing of the past. Leo's innovation transformed a life-threatening problem into a sustainable solution, showcasing how local ingenuity and community collaboration can address critical sanitation issues. This story emphasizes that small, localized actions, coupled with innovation, can have a profound and lasting impact on public health and well-being."},
{num:7,name:"Affordable and Clean Energy",desc:"An elderly artisan struggled to work after sunset due to the high cost of electricity. His granddaughter, a student of renewable energy, built a solar-powered lamp for his workshop. This simple act of kindness sparked a village-wide project, where residents pooled their resources to install solar panels. The village embraced a cleaner, more affordable energy source, allowing artisans to work longer and businesses to thrive. This story demonstrates how innovation and community collaboration can provide sustainable energy solutions, improving livelihoods and fostering economic growth."},
{num:8,name:"Decent Work and Economic Growth",desc:"At a textile factory with exploitative working conditions, a foreman named Raj led a union of employees in advocating for better treatment. Through dialogue and peaceful protests, they successfully negotiated for fair wages, safety standards, and skills training programs. The factory became a model of ethical labor practices, leading to increased productivity and a boost in market share. This story highlights the importance of advocating for fair labor practices and the positive impact that decent work can have on both employees and economic growth."},
{num:9,name:"Industry, Innovation, and Infrastructure",desc:"The town of Haven was isolated by poor infrastructure, hindering economic development. A community engineer and local volunteers used innovative techniques and locally sourced materials to build a durable, low-cost bridge. The bridge reconnected the town to the nearest market, allowing local businesses to thrive and attracting new opportunities. This story illustrates how community-driven innovation can overcome infrastructural challenges, fostering economic growth and social connectivity."},
{num:10,name:"Reduced Inequalities",desc:"In a diverse city, different neighborhoods experienced vast inequalities. Community leaders from various backgrounds formed a council to address these disparities, pushing for inclusive policies on housing, education, and organizing cultural exchange programs. Their efforts led to a more equitable distribution of resources and opportunities, fostering a sense of belonging among all residents. This story highlights the power of collaboration and advocacy in reducing inequalities and building a more inclusive society."},
{num:11,name:"Sustainable Cities and Communities",desc:"Faced with increasing air pollution, the city of Verde converted an abandoned railroad track into a public greenway, led by citizens and supported by the government. The project transformed a derelict space into a vibrant park with bike paths and gardens, improving air quality and encouraging a healthier, more sustainable lifestyle. This story serves as a testament to the power of community involvement in creating sustainable, livable urban spaces."},
{num:12,name:"Responsible Consumption and Production",desc:"A high school student, Sarah, started a campaign to reduce food waste in her school cafeteria by partnering with local farms to compost scraps and donating excess food to a food bank. Her initiative not only significantly reduced waste but also helped feed those in need, demonstrating that individual actions, driven by a commitment to responsible consumption, can have a far-reaching impact."},
{num:13,name:"Climate Action",desc:"As a remote island community faced rising sea levels, a fisherman named Kai rallied his neighbors to plant mangrove trees along the coast. The mangroves created a natural barrier against storms and helped prevent erosion, serving as a powerful example of how local communities can take proactive steps to adapt to climate change. This story emphasizes the importance of community resilience and nature-based solutions in the face of environmental threats."},
{num:14,name:"Life Below Water",desc:"A group of marine biologists and scuba divers, dismayed by a dying coral reef, launched a restoration project. They collaborated with local fishers, educating them on sustainable fishing practices and working with universities to monitor the reef's health. Over time, the reef began to regenerate, demonstrating how concerted effort and collaboration can bring life back to a fragile ecosystem. This story highlights the importance of protecting and restoring marine life and ecosystems."},
{num:15,name:"Life on Land",desc:"Forest fires threatened a mountain community's water supply and biodiversity. Local conservationists worked with firefighters and forestry officials to clear underbrush and plant fire-resistant native trees. This collaborative effort not only protected homes but also restored the forest's health, ensuring the land could continue to support both wildlife and the human community. This story illustrates the power of partnerships in preserving and restoring land-based ecosystems."},
{num:16,name:"Peace, Justice, and Strong Institutions",desc:"In a country recovering from conflict, a young lawyer, Sofia, provided legal aid to victims of violence. She worked with local officials to establish a transparent and fair legal process, which helped to restore trust in the justice system. Her work gave a voice to the voiceless, demonstrating how the tireless efforts of individuals can build the foundation for a more just and peaceful society."},
{num:17,name:"Partnerships for the Goals",desc:"The city government, a local tech company, and a non-profit organization collaborated on 'Tech for Good,' an app connecting homeless individuals with social services. The tech company provided resources and expertise, the government streamlined regulations, and the non-profit mobilized volunteers. This partnership harnessed diverse strengths to achieve a common goal, illustrating the powerful potential of cross-sectoral collaboration in addressing social challenges."}
];

const gallery = document.getElementById("sdgGallery");
const modal=document.getElementById("sdgModal");
const modalTitle=document.getElementById("modalTitle");
const modalDescription=document.getElementById("modalDescription");
sdgs.forEach(sdg=>{
  const card=document.createElement("div"); card.classList.add("sdg-card");
  card.innerHTML=`<div class="sdg-number">SDG ${sdg.num}</div><div class="sdg-name">${sdg.name}</div>`;
  card.onclick=()=>{modalTitle.textContent=`SDG ${sdg.num}: ${sdg.name}`; modalDescription.textContent=sdg.desc; modal.style.display="flex";}
  gallery.appendChild(card);
});
function closeModal(){modal.style.display="none";}
window.onclick = function(e){if(e.target===modal) closeModal();}

// Jumping Dot Game
let canvas=document.getElementById('gameCanvas'), ctx=canvas.getContext('2d');
let gameInterval, dot, platforms, score, running, gravity=0.23, moveSpeed=4.2, ballColor="#ffd600";
document.getElementById('ballColor').addEventListener('change', e=>{ballColor=e.target.value;});
function changeBallColor(color){ballColor=color;}

function initJumpingDot(){
  dot={x:canvas.width/2,y:canvas.height-40,vy:-6,r:16};
  score=0; running=true;
  platforms=[]; for(let i=0;i<9;i++){let x=Math.random()*(canvas.width-60); let y=canvas.height-i*65; platforms.push({x,y,w:60,h:12});}
}

function drawJumpingDot(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle="#4caf50"; for(let p of platforms) ctx.fillRect(p.x,p.y,p.w,p.h);
  ctx.beginPath(); ctx.arc(dot.x,dot.y,dot.r,0,Math.PI*2); ctx.fillStyle=ballColor; ctx.fill(); ctx.strokeStyle="#fff"; ctx.lineWidth=2; ctx.stroke();
  document.getElementById('score').innerText="Score: "+score;
}

let keys={};
document.addEventListener("keydown",e=>keys[e.key]=true);
document.addEventListener("keyup",e=>keys[e.key]=false);

function updateJumpingDot(){
  if(keys["ArrowLeft"]||keys["a"]) dot.x-=moveSpeed;
  if(keys["ArrowRight"]||keys["d"]) dot.x+=moveSpeed;
  if(dot.x<dot.r) dot.x=dot.r; if(dot.x>canvas.width-dot.r) dot.x=canvas.width-dot.r;
  dot.y+=dot.vy; dot.vy+=gravity;
  for(let p of platforms){
    if(dot.vy>0 && dot.x+dot.r>p.x && dot.x-dot.r<p.x+p.w && dot.y+dot.r>p.y && dot.y+dot.r<p.y+p.h+6){dot.vy=-8.5;}
  }
  if(dot.y<canvas.height/2){let diff=canvas.height/2-dot.y; dot.y=canvas.height/2; for(let p of platforms) p.y+=diff; score+=Math.floor(diff);}
  for(let p of platforms){if(p.y>canvas.height){p.x=Math.random()*(canvas.width-60); p.y=-12;}}
  if(dot.y-dot.r>canvas.height) running=false;
}

function gameLoop(){
  if(!running) return;
  drawJumpingDot(); updateJumpingDot();
  gameInterval=requestAnimationFrame(gameLoop);
}

function startJumpingDot(){initJumpingDot(); gameLoop();}
function restartJumpingDot(){initJumpingDot(); gameLoop();}
function stopGame(){running=false; cancelAnimationFrame(gameInterval);}
</script>

</body>
</html>
