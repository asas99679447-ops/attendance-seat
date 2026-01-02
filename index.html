const SHEET_URL =
  "https://docs.google.com/spreadsheets/d/19v0sq-d56HOyVWSBA77_YYmH8gPjEj_lmO8kmWRYDoQ/gviz/tq?tqx=out:csv&sheet=신청 좌석";

let seats = [];
let selectedSeat = null;
let mode = "attend";
let filterType = "오픈형";

/* 시트 불러오기 */
fetch(SHEET_URL)
  .then(r => r.text())
  .then(text => {
    const rows = text.trim().split("\n").slice(1);

    rows.forEach(r => {
      const [id, type, num, p8, p9, p10] =
        r.replaceAll('"', "").split(",");

      const seat = {
        owner: id || null,
        type,
        number: num,
        fixed: [],
        attended: [],
        using: []
      };

      if (p8 === "0") seat.fixed.push(8);
      if (p9 === "0") seat.fixed.push(9);
      if (p10 === "0") seat.fixed.push(10);

      seats.push(seat);
    });

    initFilter();
    render();
  });

/* 좌석 유형 필터 */
function initFilter() {
  const order = ["오픈형","독립형","카페형","개방형","스터디형"];
  const select = document.getElementById("typeFilter");

  order.forEach(t => {
    const o = document.createElement("option");
    o.value = t;
    o.textContent = t;
    select.appendChild(o);
  });

  select.value = filterType;
  select.onchange = () => {
    filterType = select.value;
    selectedSeat = null;
    render();
  };
}

/* 렌더링 */
function render() {
  const box = document.getElementById("seatContainer");
  box.innerHTML = "";

  const list = seats.filter(s => s.type === filterType);
  const grid = document.createElement("div");
  grid.className = "seats";

  list.forEach(seat => {
    const div = document.createElement("div");
    div.className = "seat" + (seat === selectedSeat ? " selected" : "");

    const uniq = arr => [...new Set(arr)];

    let html = `<b>${seat.number}번</b><br>`;

    if (seat.using.length)
      html += `⏳ 사용중: ${uniq(seat.using).join(",")}<br>`;
    if (seat.attended.length)
      html += `✅ 출석완료: ${uniq(seat.attended).join(",")}<br>`;
    if (seat.fixed.length)
      html += `🔒 고정: ${seat.fixed.join(",")}`;

    div.innerHTML = html;

    div.onclick = () => {
      selectedSeat = seat;
      render();
    };

    grid.appendChild(div);
  });

  box.appendChild(grid);
}

/* 모드 변경 */
function setMode(m, text, btn) {
  mode = m;
  document.getElementById("actionBtn").textContent = text;
  document.querySelectorAll(".mode button")
    .forEach(b => b.classList.remove("active"));
  btn.classList.add("active");
}

document.getElementById("modeAttend").onclick = e =>
  setMode("attend","출석",e.target);
document.getElementById("modeFree").onclick = e =>
  setMode("free","자율 사용",e.target);
document.getElementById("modeAbsent").onclick = e =>
  setMode("absent","결석",e.target);

/* 실행 버튼 */
document.getElementById("actionBtn").onclick = () => {
  if (!selectedSeat) return alert("좌석 선택");

  const id = document.getElementById("studentId").value.trim();
  const times = [...document.querySelectorAll(".time-select input:checked")]
    .map(c => Number(c.value));

  if (!times.length) return alert("교시 선택");

  /* 자율 + 고정석 차단 */
  if (mode === "free" && times.some(t => selectedSeat.fixed.includes(t))) {
    alert("고정석입니다");
    return;
  }

  /* 출석/결석은 신청 학번만 */
  if (mode !== "free" && selectedSeat.owner !== id) {
    alert("신청한 학번만 가능합니다");
    return;
  }

  times.forEach(t => {

    /* 출석 */
    if (mode === "attend") {
      if (!selectedSeat.attended.includes(t))
        selectedSeat.attended.push(t);

      selectedSeat.using =
        selectedSeat.using.filter(p => p !== t);
    }

    /* 자율 */
    if (mode === "free") {
      if (!selectedSeat.using.includes(t))
        selectedSeat.using.push(t);
    }

    /* 결석 = 완전 초기화 → 사용가능 */
    if (mode === "absent") {
      selectedSeat.attended =
        selectedSeat.attended.filter(p => p !== t);
      selectedSeat.using =
        selectedSeat.using.filter(p => p !== t);
    }
  });

  render();
};
