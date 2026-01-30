# smart-event-dashboard-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Smart Event Dashboard</title>
<style>
body{
margin:0;
font-family:Arial,Helvetica,sans-serif;
background:linear-gradient(120deg,#8ec5fc,#e0c3fc);
}
.container{
max-width:1000px;
margin:40px auto;
background:#fff;
border-radius:12px;
padding:20px;
}
h1{
text-align:center;
margin-bottom:20px;
}
.dashboard{
display:flex;
gap:20px;
}
.form-box,.events-box{
flex:1;
background:#f6fbf4;
padding:15px;
border-radius:10px;
}
input,select,textarea,button{
width:100%;
margin-bottom:10px;
padding:8px;
border-radius:6px;
border:1px solid #cccccc;
}
button{
background:#3e3a58;
color:#fff;
border:none;
cursor:pointer;
}
button:hover{
opacity:0.9;
}
.event-card{
background:#fff;
padding:10px;
border-radius:8px;
margin-bottom:10px;
display:flex;
justify-content:space-between;
align-items:center;
}
.event-card span{
display:block;
font-size:14px;
}
.remove{
background:#ff4d4d;
color:#fff;
border:none;
border-radius:50%;
width:24px;
height:24px;
cursor:pointer;
}
.dom-box{
margin-top:20px;
background:#f4f6fb;
padding:15px;
border-radius:10px;
}
.highlight{
color:#6a5acd;
font-weight:bold;
}
</style>
</head>
<body>

<div class="container">
<h1>Smart Event Dashboard</h1>

<div class="dashboard">
<div class="form-box">
<h3>Add New Event</h3>
<input id="title" placeholder="Event Title">
<input id="date" type="date">
<select id="category">
<option>Conference</option>
<option>Workshop</option>
<option>Meeting</option>
</select>
<textarea id="desc" placeholder="Description"></textarea>
<button id="addBtn">Add Event</button>
</div>

<div class="events-box">
<h3>My Events</h3>
<div id="events"></div>
<button id="clearBtn">Clear All Events</button>
</div>
</div>

<div class="dom-box">
<h3>DOM Manipulation Demo</h3>
<p id="text">This is <b>sample</b> text</p>
<button id="textBtn">Change Text Style</button>
</div>
</div>

<script>
const addBtn=document.getElementById("addBtn")
const clearBtn=document.getElementById("clearBtn")
const events=document.getElementById("events")
const text=document.getElementById("text")
const textBtn=document.getElementById("textBtn")

addBtn.addEventListener("click",()=>{
const title=document.getElementById("title").value
const date=document.getElementById("date").value
const category=document.getElementById("category").value
const desc=document.getElementById("desc").value
if(title==="")return
const card=document.createElement("div")
card.className="event-card"
card.innerHTML=`<span><b>${title}</b><br>${date}<br>${category}<br>${desc}</span><button class="remove">×</button>`
events.appendChild(card)
})

events.addEventListener("click",e=>{
if(e.target.classList.contains("remove")){
e.target.parentElement.remove()
}
})

clearBtn.addEventListener("click",()=>{
events.innerHTML=""
})

textBtn.addEventListener("click",()=>{
text.classList.toggle("highlight")
})
</script>

</body>
</html>
