const matches = [
  {
    id: 1,
    matchNo: "Match 01",
    date: "22 Mar 2026",
    time: "7:30 PM IST",
    teams: ["CSK", "RCB"],
    title: "CSK vs RCB",
    venue: "M. A. Chidambaram Stadium, Chennai"
  },
  {
    id: 2,
    matchNo: "Match 02",
    date: "23 Mar 2026",
    time: "7:30 PM IST",
    teams: ["MI", "KKR"],
    title: "MI vs KKR",
    venue: "Wankhede Stadium, Mumbai"
  },
  {
    id: 3,
    matchNo: "Match 03",
    date: "25 Mar 2026",
    time: "7:30 PM IST",
    teams: ["RCB", "MI"],
    title: "RCB vs MI",
    venue: "M. Chinnaswamy Stadium, Bengaluru"
  },
  {
    id: 4,
    matchNo: "Match 04",
    date: "27 Mar 2026",
    time: "7:30 PM IST",
    teams: ["KKR", "CSK"],
    title: "KKR vs CSK",
    venue: "Eden Gardens, Kolkata"
  },
  {
    id: 5,
    matchNo: "Match 05",
    date: "29 Mar 2026",
    time: "3:30 PM IST",
    teams: ["CSK", "MI"],
    title: "CSK vs MI",
    venue: "M. A. Chidambaram Stadium, Chennai"
  },
  {
    id: 6,
    matchNo: "Match 06",
    date: "31 Mar 2026",
    time: "7:30 PM IST",
    teams: ["RCB", "KKR"],
    title: "RCB vs KKR",
    venue: "M. Chinnaswamy Stadium, Bengaluru"
  }
];

const matchContainer = document.getElementById("matchContainer");
const teamFilter = document.getElementById("teamFilter");
const viewToggleBtn = document.getElementById("viewToggleBtn");
const hamburgerBtn = document.getElementById("hamburgerBtn");
const navLinks = document.getElementById("navLinks");

function renderMatches(selectedTeam) {
  const filtered =
    selectedTeam === "ALL"
      ? matches
      : matches.filter((match) => match.teams.includes(selectedTeam));

  matchContainer.innerHTML = filtered
    .map(
      (match) => `
      <article class="match-card">
        <div>
          <p class="match-meta">${match.matchNo} • ${match.date} • ${match.time}</p>
          <h2 class="match-teams">${match.title}</h2>
        </div>
        <p class="match-venue">${match.venue}</p>
      </article>
    `
    )
    .join("");
}

teamFilter.addEventListener("change", (event) => {
  renderMatches(event.target.value);
});

viewToggleBtn.addEventListener("click", () => {
  const isList = matchContainer.classList.toggle("list-view");
  viewToggleBtn.dataset.view = isList ? "list" : "grid";
  viewToggleBtn.textContent = isList
    ? "Switch to Grid View"
    : "Switch to List View";
});

hamburgerBtn.addEventListener("click", () => {
  const isOpen = navLinks.classList.toggle("open");
  hamburgerBtn.setAttribute("aria-expanded", String(isOpen));
});

navLinks.querySelectorAll("a").forEach((link) => {
  link.addEventListener("click", () => {
    navLinks.classList.remove("open");
    hamburgerBtn.setAttribute("aria-expanded", "false");
  });
});

renderMatche
