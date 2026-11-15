
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#080d1b">
<title>LinkGate Ultra</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap');

:root {
 --bg:#080d1b;
 --panel:#111a2e;
 --border:#293a58;
 --text:#f8fafc;
 --muted:#91a1ba;
 --blue:#5687ff;
 --green:#19cb91;
}

*{box-sizing:border-box;margin:0;padding:0}

body{
 min-height:100vh;
 padding:20px;
 display:flex;
 align-items:center;
 justify-content:center;
 font-family:Inter,Arial,sans-serif;
 color:var(--text);
 background:
 radial-gradient(ellipse at 15% 5%,#1c3158,transparent 45%),
 var(--bg);
}

.container{
 width:100%;
 max-width:540px;
 padding:30px;
 border:1px solid #26354c;
 border-radius:24px;
 background:rgba(17,26,46,.97);
 box-shadow:0 25px 80px #0008;
}

.logo{
 text-align:center;
 font-size:36px;
 font-weight:900;
 letter-spacing:-2px;
 background:linear-gradient(110deg,#72b5ff,#7585ff,#bb79ff);
 color:transparent;
 background-clip:text;
}

.subtitle{
 text-align:center;
 color:#8193b3;
 font-size:10px;
 font-weight:800;
 letter-spacing:4px;
 margin:8px 0 30px;
}

h2{
 text-align:center;
 font-size:22px;
 margin-bottom:10px;
}

.desc{
 text-align:center;
 color:var(--muted);
 font-size:12px;
 line-height:1.7;
 margin-bottom:23px;
}

.label{
 display:block;
 color:#c5d2e7;
 font-size:11px;
 font-weight:800;
 margin:15px 0 7px;
}

input,select{
 width:100%;
 height:49px;
 padding:0 14px;
 background:#0a1325;
 color:white;
 border:1px solid var(--border);
 border-radius:11px;
 font-size:13px;
 outline:none;
}

input:focus,select:focus{
 border-color:var(--blue);
}

button{
 width:100%;
 min-height:48px;
 margin-top:12px;
 border:0;
 border-radius:11px;
 color:white;
 font-size:13px;
 font-weight:800;
 cursor:pointer;
}

button:disabled{
 opacity:.5;
 cursor:not-allowed;
}

.primary{
 background:linear-gradient(110deg,#377df4,#7459f0);
}

.success{
 background:linear-gradient(110deg,#0bbd88,#12a77a);
}

.copy{background:#087da9}
.danger{background:#a8324b}
.secondary{background:#293a58}

.mode-box{
 display:grid;
 grid-template-columns:1fr 1fr;
 gap:10px;
 margin:15px 0;
}

.mode-option{
 padding:15px 10px;
 background:#0a1325;
 border:1px solid var(--border);
 border-radius:12px;
 cursor:pointer;
 text-align:center;
 font-size:12px;
 font-weight:800;
}

.mode-option.active{
 border-color:#5687ff;
 background:#17294b;
 color:#91b6ff;
}

.mode-option input{
 width:auto;
 height:auto;
 margin:0 5px 0 0;
}

.link-row{
 background:#0a1427;
 border:1px solid var(--border);
 border-radius:12px;
 padding:13px;
 margin-top:12px;
}

.link-row button{
 margin-top:9px;
}

.result{
 display:none;
 margin-top:18px;
 padding:16px;
 background:#0a1427;
 border:1px solid var(--border);
 border-radius:12px;
}

.result b{
 display:block;
 color:#91b6ff;
 font-size:12px;
 margin-bottom:10px;
}

.note{
 padding:14px;
 margin:17px 0;
 background:#1a2a45;
 border-left:3px solid var(--blue);
 border-radius:8px;
 font-size:12px;
 line-height:1.7;
 color:#c5d5f1;
}

.message{
 text-align:center;
 font-size:12px;
 margin-top:13px;
 line-height:1.7;
 color:var(--muted);
}

.error{color:#ff7088}
.ok{color:#36e4ae}

.footer{
 margin-top:25px;
 padding-top:15px;
 border-top:1px solid var(--border);
 text-align:center;
 color:#62738f;
 font-size:10px;
}

.owner{
 text-align:center;
 font-size:23px;
 font-weight:900;
 overflow-wrap:anywhere;
 margin:10px 0;
 color:#fff;
}

.public-links{
 display:flex;
 flex-direction:column;
 gap:13px;
 margin-top:25px;
}

.public-link{
 display:flex;
 align-items:center;
 justify-content:space-between;
 gap:10px;
 padding:17px;
 border:1px solid #34496c;
 border-radius:13px;
 background:linear-gradient(110deg,#172944,#101b32);
 text-decoration:none;
 color:white;
 font-size:13px;
 font-weight:800;
 transition:.2s;
}

.public-link:hover{
 border-color:#5687ff;
 transform:translateY(-2px);
}

.public-link span:last-child{
 color:#83aaff;
 font-size:18px;
}

.ad-overlay{
 display:none;
 position:fixed;
 inset:0;
 z-index:9999;
 align-items:center;
 justify-content:center;
 padding:20px;
 background:rgba(0,0,0,.94);
 backdrop-filter:blur(10px);
}

.ad-overlay.show{display:flex}

.ad-card{
 width:100%;
 max-width:400px;
 padding:20px;
 border:1px solid #40516f;
 border-radius:18px;
 background:#111a2e;
 text-align:center;
}

.ad-title{
 font-size:18px;
 font-weight:800;
 margin-bottom:12px;
}

.ad-button{
 display:block;
 padding:14px;
 margin-top:15px;
 background:linear-gradient(110deg,#377df4,#7459f0);
 border-radius:10px;
 color:white;
 text-decoration:none;
 font-size:13px;
 font-weight:800;
}

.continue{display:none;background:#16a77c}
.continue.show{display:block}

@media(max-width:480px){
 .container{padding:23px 18px}
 .logo{font-size:32px}
 .mode-box{grid-template-columns:1fr}
}
</style>
</head>

<body>

<main class="container" id="app"></main>

<div class="ad-overlay" id="adOverlay">
 <div class="ad-card">
  <div class="subtitle">SPONSORED ADVERTISEMENT</div>
  <div class="ad-title">Quảng cáo tài trợ</div>
  <a class="ad-button" id="adVisit"
     target="_blank"
     rel="sponsored noopener noreferrer">
     XEM QUẢNG CÁO
  </a>
  <div class="message" id="adCount"></div>
  <button class="continue" id="continueBtn">
   TIẾP TỤC XÁC THỰC
  </button>
 </div>
</div>

<script>
"use strict";

const app=document.getElementById("app");
const params=new URLSearchParams(location.search);
const encoded=params.get("d");

const AD_WAIT=8;

function validURL(value){
 try{
  const u=new URL(value);
  return ["http:","https:"].includes(u.protocol);
 }catch{return false}
}

function encodeData(data){
 const bytes=new TextEncoder().encode(JSON.stringify(data));
 let binary="";
 bytes.forEach(b=>binary+=String.fromCharCode(b));

 return btoa(binary)
  .replace(/\+/g,"-")
  .replace(/\//g,"_")
  .replace(/=+$/g,"");
}

function decodeData(value){
 if(!/^[A-Za-z0-9_-]+$/.test(value))throw Error();

 const base=value.replace(/-/g,"+").replace(/_/g,"/");
 const binary=atob(base);
 const bytes=Uint8Array.from(binary,c=>c.charCodeAt(0));

 return JSON.parse(new TextDecoder().decode(bytes));
}

function el(tag,text,parent=app,cls=""){
 const node=document.createElement(tag);
 node.textContent=text;
 if(cls)node.className=cls;
 parent.appendChild(node);
 return node;
}

function field(label,placeholder,type="text",parent=app){
 el("label",label,parent,"label");

 const node=document.createElement("input");
 node.placeholder=placeholder;
 node.type=type;
 node.autocomplete="off";

 parent.appendChild(node);
 return node;
}

function btn(text,cls,callback,parent=app){
 const node=document.createElement("button");
 node.textContent=text;
 node.className=cls;
 node.type="button";
 node.onclick=callback;
 parent.appendChild(node);
 return node;
}

function header(){
 el("div","LINKGATE",app,"logo");
 el("div","SMART LINK GATEWAY",app,"subtitle");
}

function footer(){
 el("div","LINKGATE ULTRA • GITHUB PAGES",app,"footer");
}

/* =========================
   TRANG TẠO LINK
========================= */

function renderCreator(){
 app.innerHTML="";
 header();

 el("h2","Tạo liên kết mới");
 el("p","Chọn chế độ liên kết mà bạn muốn tạo.",app,"desc");

 let mode="normal";

 const modeBox=el("div","",app,"mode-box");

 function modeOption(value,title,description){
  const label=document.createElement("label");
  label.className="mode-option"+(mode===value?" active":"");

  const radio=document.createElement("input");
  radio.type="radio";
  radio.name="linkMode";
  radio.value=value;
  radio.checked=mode===value;

  const titleNode=document.createElement("div");
  titleNode.textContent=title;

  const descNode=document.createElement("div");
  descNode.textContent=description;
  descNode.style.cssText="font-size:10px;color:#91a1ba;margin-top:7px";

  label.append(radio,titleNode,descNode);
  modeBox.appendChild(label);

  radio.onchange=()=>{
   mode=value;
   renderCreator();
  };
 }

 modeOption("normal","LINK BÌNH THƯỜNG","Danh sách nhiều link");
 modeOption("gate","LINK VƯỢT","Quảng cáo và mật khẩu");

 const owner=field("TÊN NGƯỜI SỞ HỮU","Nhập tên hiển thị");

 let password,video,ad;
 const rows=[];

 if(mode==="normal"){

  el("div","DANH SÁCH LIÊN KẾT",app,"label");

  const list=el("div","",app);

  function addLink(name="",url=""){
   const row=el("div","",list,"link-row");

   const title=field("TÊN LIÊN KẾT","Ví dụ: Google Drive", "text",row);
   title.value=name;

   const address=field("URL ĐÍCH","https://...", "url",row);
   address.value=url;

   const remove=btn("✕ XÓA LIÊN KẾT","danger",()=>{
    row.remove();
    rows.splice(rows.indexOf(item),1);
   },row);

   const item={title,address,row};
   rows.push(item);
  }

  btn("+ THÊM LIÊN KẾT","secondary",()=>addLink());

  addLink();

 }else{

  password=field("MẬT KHẨU XÁC THỰC","Nhập mật khẩu");
  video=field("LINK VIDEO HƯỚNG DẪN","https://...");
  ad=field("LINK QUẢNG CÁO","https://...");

  const target=field("LINK TẢI ĐÍCH","https://...");
  rows.push({title:{value:"Liên kết tải"},address:target});
 }

 const result=el("div","",app,"result");

 btn("✦ TẠO LINK NGAY","primary",()=>{
  const name=owner.value.trim();

  if(!name){
   alert("Vui lòng nhập tên người sở hữu!");
   return;
  }

  let data;

  if(mode==="normal"){

   const links=rows.map(item=>({
    name:item.title.value.trim(),
    url:item.address.value.trim()
   }));

   if(!links.length){
    alert("Hãy thêm ít nhất một liên kết!");
    return;
   }

   if(links.some(x=>!x.name||!validURL(x.url))){
    alert("Vui lòng kiểm tra tên và URL của tất cả liên kết!");
    return;
   }

   data={
    mode:"normal",
    owner:name,
    links:links
   };

  }else{

   const p=password.value.trim();
   const v=video.value.trim();
   const a=ad.value.trim();
   const t=rows[0].address.value.trim();

   if(!p||!validURL(v)||!validURL(a)||!validURL(t)){
    alert("Vui lòng nhập đủ thông tin hợp lệ!");
    return;
   }

   data={
    mode:"gate",
    owner:name,
    p,t,v,a
   };
  }

  const link=location.origin+location.pathname+
   "?d="+encodeData(data);

  result.style.display="block";
  result.innerHTML="";

  el("b","✓ LINK ĐÃ ĐƯỢC TẠO",result);

  const output=document.createElement("input");
  output.value=link;
  output.readOnly=true;
  output.style.marginTop="10px";
  result.appendChild(output);

  btn("SAO CHÉP LINK","copy",async()=>{
   try{
    await navigator.clipboard.writeText(link);
    alert("Đã sao chép!");
   }catch{
    output.select();
    document.execCommand("copy");
   }
  },result);

  result.scrollIntoView({behavior:"smooth"});
 });

 footer();
}

/* =========================
   TRANG DANH SÁCH LINK
========================= */

function renderDirect(data){

 app.innerHTML="";
 header();

 el("div",data.owner,app,"owner");

 el(
  "p",
  "DANH SÁCH LIÊN KẾT",
  app,
  "desc"
 );

 el(
  "p",
  "Chọn liên kết bạn muốn truy cập.",
  app,
  "message"
 );

 const list=el("div","",app,"public-links");

 data.links.forEach(item=>{

  const a=document.createElement("a");

  a.href=item.url;
  a.target="_blank";
  a.rel="noopener noreferrer";
  a.className="public-link";

  const name=document.createElement("span");
  name.textContent=item.name;

  const arrow=document.createElement("span");
  arrow.textContent="↗";

  a.append(name,arrow);
  list.appendChild(a);

 });

 footer();
}

/* =========================
   QUẢNG CÁO
========================= */

function showAdvertisement(data){

 const overlay=document.getElementById("adOverlay");
 const visit=document.getElementById("adVisit");
 const count=document.getElementById("adCount");
 const continueBtn=document.getElementById("continueBtn");

 visit.href=data.a;
 overlay.classList.add("show");

 let remaining=AD_WAIT;
 count.textContent="Vui lòng chờ "+remaining+" giây.";

 const timer=setInterval(()=>{
  remaining--;

  if(remaining<=0){
   clearInterval(timer);
   count.textContent="Bạn có thể tiếp tục.";
   continueBtn.classList.add("show");
  }else{
   count.textContent="Vui lòng chờ "+remaining+" giây.";
  }
 },1000);

 continueBtn.onclick=()=>{
  clearInterval(timer);
  overlay.classList.remove("show");
  renderGate(data);
 };
}

/* =========================
   TRANG VƯỢT LINK
========================= */

function renderGate(data){

 app.innerHTML="";
 header();

 el("h2","Xác thực liên kết");
 el("p","Xem video hướng dẫn và nhập mật khẩu để tiếp tục.",app,"desc");

 const video=document.createElement("a");

 video.href=data.v;
 video.target="_blank";
 video.rel="noopener noreferrer";
 video.className="success";
 video.style.display="block";
 video.style.textAlign="center";
 video.style.padding="16px";
 video.style.textDecoration="none";
 video.textContent="▶ XEM VIDEO HƯỚNG DẪN";

 app.appendChild(video);

 el("div","Vui lòng nhập mật khẩu chính xác để lấy liên kết.",app,"note");

 const password=field(
  "MẬT KHẨU XÁC THỰC",
  "Nhập mật khẩu...",
  "password"
 );

 const message=el("div","",app,"message");

 let verified=false;

 function verify(){

  if(verified)return;

  if(password.value===data.p){

   verified=true;

   message.textContent="✓ Thành công! Đang chuyển hướng...";
   message.className="message ok";

   const link=document.createElement("a");
   link.href=data.t;
   link.textContent="Nhấn vào đây nếu không tự chuyển hướng";
   link.style.display="block";
   link.style.color="#82adff";
   link.style.textAlign="center";
   link.style.marginTop="15px";

   app.appendChild(link);

   setTimeout(()=>location.assign(data.t),1200);

  }else{

   message.textContent="Mật khẩu không chính xác!";
   message.className="message error";

   password.value="";
   password.focus();
  }
 }

 btn("✓ XÁC NHẬN & LẤY LINK","success",verify);

 password.addEventListener("keydown",e=>{
  if(e.key==="Enter")verify();
 });

 footer();
}

/* =========================
   KHỞI ĐỘNG
========================= */

try{

 if(!encoded){

  renderCreator();

 }else{

  if(encoded.length>1000000)throw Error();

  const data=decodeData(encoded);

  if(!data||typeof data.owner!=="string"||!data.owner){
   throw Error();
  }

  if(data.mode==="normal"){

   if(!Array.isArray(data.links)||!data.links.length){
    throw Error();
   }

   if(data.links.some(x=>
    !x||
    typeof x.name!=="string"||
    !x.name||
    !validURL(x.url)
   )){
    throw Error();
   }

   renderDirect(data);

  }else if(data.mode==="gate"){

   if(
    typeof data.p!=="string"||
    !data.p||
    !validURL(data.t)||
    !validURL(data.v)||
    !validURL(data.a)
   ){
    throw Error();
   }

   showAdvertisement(data);

  }else{
   throw Error();
  }
 }

}catch{

 app.innerHTML="";
 header();

 el("h2","Link không hợp lệ");
 el("p","Dữ liệu bị lỗi hoặc liên kết không hợp lệ.",app,"message error");

 btn("QUAY LẠI","primary",()=>location.href=location.pathname);

 footer();
}
</script>

</body>
</html>
