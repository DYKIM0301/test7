<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title>통신사 비교 견적서</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

<style>

body{
font-family:Arial;
background:#f2f4f7;
padding:40px;
}

h2{
text-align:center;
}

table{
border-collapse:collapse;
width:800px;
margin:auto;
text-align:center;
}

td{
border:1px solid #333;
padding:10px;
}

.blue{
background:#1f77b4;
color:white;
font-weight:bold;
}

.yellow{
background:yellow;
}

.red{
background:#ff3b3b;
color:white;
font-weight:bold;
}

input{
width:130px;
border:none;
background:transparent;
text-align:center;
}

.infoInput input{
border:1px solid #ccc;
background:white;
padding:5px;
}

button{
margin:15px;
padding:12px 20px;
font-size:16px;
cursor:pointer;
}

.quote{
background:white;
padding:40px;
width:850px;
margin:40px auto;
}

.header{
display:flex;
justify-content:space-between;
align-items:center;
}

.titleBox h1{
margin:0;
font-size:32px;
}

.titleBox p{
margin:0;
color:#6b7a90;
}

.redline{
border:2px solid #e60023;
margin:20px 0;
}

.infoArea{
display:flex;
justify-content:space-between;
margin-bottom:30px;
}

.receiverBox{
background:#f1f3f6;
padding:20px;
border-radius:10px;
width:50%;
}

.infoTable{
width:40%;
}

.infoRow{
display:flex;
justify-content:space-between;
padding:10px 0;
border-bottom:1px solid #ddd;
}

.serviceTable{
width:100%;
border-collapse:collapse;
}

.serviceTable th{
background:#f0f2f5;
padding:10px;
}

.serviceTable td{
padding:10px;
border-bottom:1px solid #ddd;
}

.priceBox{
background:#0b1a33;
color:white;
margin-top:30px;
padding:20px;
border-radius:10px;
}

.priceRow{
display:flex;
justify-content:space-between;
font-size:20px;
margin:10px 0;
}

</style>

<script>

function calc(){

let a_fee = Number(document.getElementById("a_fee").value)
let a_gift = Number(document.getElementById("a_gift").value)
let a_free = Number(document.getElementById("a_free").value)
let a_contract = Number(document.getElementById("a_contract").value)

let b_fee = Number(document.getElementById("b_fee").value)
let b_gift = Number(document.getElementById("b_gift").value)
let b_free = Number(document.getElementById("b_free").value)
let b_contract = Number(document.getElementById("b_contract").value)

let a_total = (a_fee*a_contract) - a_gift - (a_free*a_fee)
let b_total = (b_fee*b_contract) - b_gift - (b_free*b_fee)

let a_avg = a_total/a_contract
let b_avg = b_total/b_contract

document.getElementById("a_total").innerText = a_total.toLocaleString()
document.getElementById("b_total").innerText = b_total.toLocaleString()

document.getElementById("a_avg").innerText = Math.round(a_avg).toLocaleString()
document.getElementById("b_avg").innerText = Math.round(b_avg).toLocaleString()

}


function makeQuote(){

let receiver = document.getElementById("receiver").value
let date = document.getElementById("date").value
let manager = document.getElementById("manager").value
let phone = document.getElementById("phone").value

document.getElementById("q_receiver").innerText = receiver + " 님"
document.getElementById("quote_date").innerText = date
document.getElementById("q_manager").innerText = manager
document.getElementById("q_phone").innerText = phone


let a_fee = document.getElementById("a_fee").value
let a_gift = document.getElementById("a_gift").value
let a_free = document.getElementById("a_free").value
let a_contract = document.getElementById("a_contract").value

let b_fee = document.getElementById("b_fee").value
let b_gift = document.getElementById("b_gift").value
let b_free = document.getElementById("b_free").value
let b_contract = document.getElementById("b_contract").value

let a_total = document.getElementById("a_total").innerText
let b_total = document.getElementById("b_total").innerText

let a_avg = document.getElementById("a_avg").innerText
let b_avg = document.getElementById("b_avg").innerText

document.getElementById("qa_fee").innerText = a_fee
document.getElementById("qb_fee").innerText = b_fee

document.getElementById("qa_gift").innerText = a_gift
document.getElementById("qb_gift").innerText = b_gift

document.getElementById("qa_free").innerText = a_free
document.getElementById("qb_free").innerText = b_free

document.getElementById("qa_contract").innerText = a_contract
document.getElementById("qb_contract").innerText = b_contract

document.getElementById("qa_total").innerText = a_total
document.getElementById("qb_total").innerText = b_total

document.getElementById("qa_avg").innerText = a_avg
document.getElementById("qb_avg").innerText = b_avg

document.getElementById("qa_avg_box").innerText = a_avg + " 원"
document.getElementById("qb_avg_box").innerText = b_avg + " 원"

}


function downloadImage(){

html2canvas(document.querySelector("#quote")).then(canvas => {

let link = document.createElement("a")
link.download = "견적서.png"
link.href = canvas.toDataURL()
link.click()

})

}

</script>

</head>


<body>

<h2>통신사 요금 비교 계산기</h2>

<table class="infoInput">

<tr>
<td>수신인</td>
<td><input id="receiver"></td>
<td>견적작성일</td>
<td><input id="date" type="date"></td>
</tr>

<tr>
<td>담당자</td>
<td><input id="manager"></td>
<td>연락처</td>
<td><input id="phone"></td>
</tr>

</table>

<br>

<table>

<tr>
<td class="blue">비고</td>
<td class="blue">타 통신사</td>
<td class="blue">LG헬로비전</td>
</tr>

<tr>
<td class="blue">월요금</td>
<td class="yellow"><input id="a_fee" oninput="calc()"></td>
<td class="yellow"><input id="b_fee" oninput="calc()"></td>
</tr>

<tr>
<td class="blue">사은품</td>
<td class="yellow"><input id="a_gift" oninput="calc()"></td>
<td class="yellow"><input id="b_gift" oninput="calc()"></td>
</tr>

<tr>
<td class="blue">무료개월</td>
<td class="yellow"><input id="a_free" oninput="calc()"></td>
<td class="yellow"><input id="b_free" oninput="calc()"></td>
</tr>

<tr>
<td class="blue">약정</td>
<td class="yellow"><input id="a_contract" oninput="calc()"></td>
<td class="yellow"><input id="b_contract" oninput="calc()"></td>
</tr>

<tr>
<td class="blue">36개월 총 부담금</td>
<td class="red" id="a_total">0</td>
<td class="red" id="b_total">0</td>
</tr>

<tr>
<td class="blue">월평균 요금</td>
<td class="red" id="a_avg">0</td>
<td class="red" id="b_avg">0</td>
</tr>

</table>

<div style="text-align:center">
<button onclick="makeQuote()">견적서 만들기</button>
<button onclick="downloadImage()">견적서 이미지 저장</button>
</div>


<div id="quote" class="quote">

<div class="header">

<div class="titleBox">
<h1>LG헬로비전 다회선 견적서</h1>
<p>LG HELLOVISION MULTI-LINE SERVICE</p>
</div>

<div class="logoBox">
<img src="logo.png" style="height:50px;">
</div>

</div>

<hr class="redline">

<div class="infoArea">

<div class="receiverBox">
<p>수신</p>
<h2 id="q_receiver"></h2>
<p>당사의 서비스를 제안하게 되어 영광입니다.</p>
</div>

<div class="infoTable">

<div class="infoRow">
<span>견적작성일</span>
<span id="quote_date"></span>
</div>

<div class="infoRow">
<span>담당자</span>
<span id="q_manager"></span>
</div>

<div class="infoRow">
<span>연락처</span>
<span id="q_phone"></span>
</div>

</div>

</div>


<table class="serviceTable">

<tr>
<th>항목</th>
<th>타 통신사</th>
<th>LG헬로비전</th>
</tr>

<tr>
<td>월요금</td>
<td id="qa_fee"></td>
<td id="qb_fee"></td>
</tr>

<tr>
<td>사은품</td>
<td id="qa_gift"></td>
<td id="qb_gift"></td>
</tr>

<tr>
<td>무료개월</td>
<td id="qa_free"></td>
<td id="qb_free"></td>
</tr>

<tr>
<td>약정개월</td>
<td id="qa_contract"></td>
<td id="qb_contract"></td>
</tr>

<tr>
<td>36개월 총 부담금</td>
<td id="qa_total"></td>
<td id="qb_total"></td>
</tr>

<tr>
<td>월평균 요금</td>
<td id="qa_avg"></td>
<td id="qb_avg"></td>
</tr>

</table>


<div class="priceBox">

<div class="priceRow">
<span>타 통신사 월평균 요금</span>
<span id="qa_avg_box"></span>
</div>

<div class="priceRow">
<span>LG헬로비전 월 평균 요금</span>
<span id="qb_avg_box"></span>
</div>

</div>

</div>

</body>
</html>
