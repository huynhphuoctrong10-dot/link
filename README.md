"Vui lòng nhập đủ thông tin hợp lệ!");
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
