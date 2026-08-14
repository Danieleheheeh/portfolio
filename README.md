<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Parigi — Il mio taccuino</title>

<link
rel="stylesheet"
href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
/>

<style>

:root {
    --black: #171b20;
    --dark: #20262d;
    --blue: #8fb8ca;
    --blue-dark: #426b7d;
    --sky: #dcecf2;
    --paper: #eef4f6;
    --white: #ffffff;
    --text: #263038;
    --muted: #66737b;
    --border: #cbd9de;
}

* {
    box-sizing: border-box;
    scroll-behavior: smooth;
}

body {
    margin: 0;
    font-family: Georgia, "Times New Roman", serif;
    background: var(--paper);
    color: var(--text);
    line-height: 1.7;
}

/* PROGRESS BAR */

#progress {
    position: fixed;
    top: 0;
    left: 0;
    height: 4px;
    width: 0%;
    background: var(--blue);
    z-index: 999;
}

/* HEADER */

header {
    position: fixed;
    top: 4px;
    width: 100%;
    z-index: 100;
    padding: 17px 6%;
    background: rgba(23, 27, 32, 0.96);
    backdrop-filter: blur(10px);
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    color: white;
    font-size: 20px;
    letter-spacing: 3px;
}

nav a {
    color: #dce7eb;
    text-decoration: none;
    margin-left: 22px;
    font-family: Arial, sans-serif;
    font-size: 12px;
}

nav a:hover {
    color: var(--blue);
}

/* HERO */

.hero {
    min-height: 100vh;
    padding: 150px 25px 100px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;

    background:
        linear-gradient(
            rgba(15, 20, 24, 0.56),
            rgba(15, 20, 24, 0.72)
        ),
        url("https://images.unsplash.com/photo-1502602898657-3e91760cbb34?auto=format&fit=crop&w=2200&q=90");

    background-size: cover;
    background-position: center;
    color: white;
}

.hero small {
    text-transform: uppercase;
    letter-spacing: 5px;
    font-family: Arial, sans-serif;
    font-size: 11px;
    color: var(--blue);
}

.hero h1 {
    font-size: clamp(65px, 12vw, 145px);
    line-height: .9;
    font-weight: normal;
    margin: 25px 0;
}

.hero p {
    max-width: 700px;
    font-size: 20px;
}

.button {
    display: inline-block;
    margin-top: 25px;
    padding: 13px 30px;
    background: var(--blue);
    color: var(--black);
    text-decoration: none;
    border-radius: 30px;
    font-family: Arial, sans-serif;
    font-weight: bold;
}

.button:hover {
    background: white;
}

/* GENERAL */

section {
    max-width: 1150px;
    margin: auto;
    padding: 105px 25px;
}

.label {
    color: var(--blue-dark);
    text-transform: uppercase;
    letter-spacing: 4px;
    font-family: Arial, sans-serif;
    font-size: 11px;
}

section h2 {
    font-size: 47px;
    line-height: 1.1;
    font-weight: normal;
    margin: 12px 0 35px;
}

.intro {
    max-width: 800px;
    font-size: 20px;
}

/* CARDS */

.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(245px, 1fr));
    gap: 20px;
}

.card {
    background: white;
    padding: 30px;
    border: 1px solid var(--border);
    transition: .25s;
}

.card:hover {
    transform: translateY(-6px);
    box-shadow: 0 15px 35px rgba(20,40,50,.10);
}

.card h3 {
    font-size: 26px;
    font-weight: normal;
    margin: 12px 0;
}

.card-number {
    color: var(--blue-dark);
    font-family: Arial, sans-serif;
    font-size: 11px;
}

/* CALENDAR */

.calendar-box {
    background: var(--dark);
    color: white;
    padding: 35px;
    border-radius: 4px;
}

.calendar-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 25px;
}

.calendar-top h3 {
    margin: 0;
    font-size: 27px;
    font-weight: normal;
}

.calendar-top button {
    background: var(--blue);
    border: 0;
    padding: 8px 13px;
    cursor: pointer;
    border-radius: 4px;
}

.calendar-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 7px;
}

.calendar-day {
    min-height: 55px;
    padding: 8px;
    background: #2c343c;
    cursor: pointer;
    font-family: Arial, sans-serif;
    font-size: 13px;
}

.calendar-day:hover {
    background: var(--blue-dark);
}

.calendar-day.selected {
    background: var(--blue);
    color: var(--black);
}

.calendar-event {
    margin-top: 5px;
    font-size: 9px;
    color: #b9dbe7;
}

/* ITINERARIO */

.timeline {
    border-left: 1px solid #aebfc6;
    margin-left: 12px;
    padding-left: 30px;
}

.day {
    margin-bottom: 55px;
    position: relative;
}

.day:before {
    content: "";
    width: 10px;
    height: 10px;
    background: var(--blue);
    border-radius: 50%;
    position: absolute;
    left: -36px;
    top: 10px;
}

.day h3 {
    font-size: 28px;
    font-weight: normal;
    margin: 8px 0;
}

.day-number {
    color: var(--blue-dark);
    font-family: Arial, sans-serif;
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 2px;
}

.calendar-button,
.map-button,
.visited-button {
    display: inline-block;
    margin: 12px 7px 0 0;
    padding: 9px 15px;
    border: 0;
    border-radius: 20px;
    text-decoration: none;
    cursor: pointer;
    font-family: Arial, sans-serif;
    font-size: 11px;
}

.calendar-button {
    background: var(--dark);
    color: white;
}

.map-button {
    background: var(--blue);
    color: var(--black);
}

.visited-button {
    background: #d5e1e5;
    color: var(--text);
}

.visited-button.done {
    background: #5c7d6b;
    color: white;
}

/* MAPPA */

#map {
    width: 100%;
    height: 600px;
    border: 1px solid var(--border);
}

.map-info {
    background: white;
    padding: 20px;
    border: 1px solid var(--border);
    margin-bottom: 20px;
}

/* QUOTE */

.quote {
    background: var(--black);
    color: white;
    text-align: center;
    padding: 110px 25px;
}

.quote p {
    max-width: 850px;
    margin: auto;
    font-size: 34px;
    font-style: italic;
}

.quote small {
    display: block;
    margin-top: 20px;
    color: var(--blue);
    font-family: Arial, sans-serif;
}

/* LIST */

.list {
    display: grid;
    gap: 14px;
}

.list-item {
    background: white;
    padding: 22px;
    border-left: 4px solid var(--blue);
}

.list-item strong {
    font-size: 19px;
}

/* FOOTER */

footer {
    background: var(--black);
    color: #aab5ba;
    text-align: center;
    padding: 45px 20px;
    font-family: Arial, sans-serif;
    font-size: 12px;
}

/* MOBILE */

@media(max-width: 700px) {

    header {
        padding: 14px 15px;
    }

    .logo {
        font-size: 16px;
    }

    nav a {
        margin-left: 7px;
        font-size: 10px;
    }

    .hero h1 {
        font-size: 70px;
    }

    section h2 {
        font-size: 37px;
    }

    .calendar-grid {
        gap: 3px;
    }

    .calendar-day {
        min-height: 45px;
        padding: 5px;
    }

    #map {
        height: 450px;
    }

    .quote p {
        font-size: 26px;
    }
}

</style>
</head>

<body>

<div id="progress"></div>


<header>

<div class="logo">PARIGI</div>

<nav>
<a href="#quartieri">Quartieri</a>
<a href="#calendario">Calendario</a>
<a href="#itinerario">12 giorni</a>
<a href="#mappa">Mappa</a>
<a href="#segreti">Segreti</a>
</nav>

</header>


<!-- HERO -->

<div class="hero">

<small>Il mio taccuino di viaggio</small>

<h1>Parigi</h1>

<p>
Dodici giorni per attraversare una città
che non si lascia conoscere tutta in una volta.
</p>

<a class="button" href="#quartieri">
Inizia il viaggio
</a>

</div>


<!-- INTRO -->

<section>

<span class="label">01 — Il progetto</span>

<h2>Non una lista di monumenti.</h2>

<div class="intro">

<p>
Questa non vuole essere una guida turistica qualsiasi.
È un taccuino personale per esplorare Parigi:
arte, storia, filosofia, architettura,
quartieri, persone, cibo e piccole scoperte.
</p>

<p>
L'idea è semplice: avere tutto nello stesso posto.
Una mappa, un calendario, un itinerario,
luoghi da scoprire e luoghi già visitati.
</p>

</div>

</section>


<!-- QUARTIERI -->

<section id="quartieri">

<span class="label">02 — Quartieri</span>

<h2>Parigi cambia volto.</h2>

<div class="cards">

<div class="card">
<span class="card-number">01</span>
<h3>Le Marais</h3>
<p>Storia, palazzi, gallerie, boutique e strade perfette da attraversare senza fretta.</p>
</div>

<div class="card">
<span class="card-number">02</span>
<h3>Montmartre</h3>
<p>Arte, salite, Sacré-Cœur, atelier e una delle atmosfere più riconoscibili della città.</p>
</div>

<div class="card">
<span class="card-number">03</span>
<h3>Quartiere Latino</h3>
<p>Sorbona, librerie, storia medievale e tradizione intellettuale.</p>
</div>

<div class="card">
<span class="card-number">04</span>
<h3>Saint-Germain</h3>
<p>Letteratura, filosofia, caffè storici e gallerie.</p>
</div>

<div class="card">
<span class="card-number">05</span>
<h3>Canal Saint-Martin</h3>
<p>Una Parigi più quotidiana, rilassata e lontana dai percorsi più ovvi.</p>
</div>

<div class="card">
<span class="card-number">06</span>
<h3>La Villette</h3>
<p>Architettura contemporanea, cultura, musica e grandi spazi.</p>
</div>

<div class="card">
<span class="card-number">07</span>
<h3>Belleville</h3>
<p>Un quartiere multiculturale, creativo e interessante da osservare a piedi.</p>
</div>

<div class="card">
<span class="card-number">08</span>
<h3>Montparnasse</h3>
<p>La Parigi degli artisti, degli scrittori e delle avanguardie del Novecento.</p>
</div>

</div>

</section>


<!-- CALENDARIO -->

<section id="calendario">

<span class="label">03 — Calendario</span>

<h2>Il viaggio, giorno per giorno.</h2>

<div class="calendar-box">

<div class="calendar-top">

<h3 id="monthTitle">Agosto 2026</h3>

<div>
<button onclick="previousMonth()">‹</button>
<button onclick="nextMonth()">›</button>
</div>

</div>

<div class="calendar-grid" id="calendar"></div>

</div>

<p id="selectedDate">
Seleziona un giorno per vedere l'idea prevista.
</p>

</section>


<!-- 12 GIORNI -->

<section id="itinerario">

<span class="label">04 — Dodici giorni</span>

<h2>Un possibile viaggio.</h2>

<div class="timeline">


<div class="day">
<span class="day-number">Giorno 01 — La Parigi storica</span>
<h3>Île de la Cité → Notre-Dame → Senna</h3>
<p>Il cuore storico della città. Passeggiata lungo la Senna e Quartiere Latino.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%201%20-%20Centro%20storico">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Notre+Dame+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 02 — Arte</span>
<h3>Louvre → Tuileries → Musée d'Orsay</h3>
<p>Una giornata dedicata alla pittura e alla storia dell'arte.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%202%20-%20Arte">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Louvre+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 03 — Montmartre</span>
<h3>Montmartre → Sacré-Cœur → Pigalle</h3>
<p>Arte, panorami e strade da esplorare a piedi.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%203%20-%20Montmartre">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Montmartre+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 04 — Le Marais</span>
<h3>Place des Vosges → Hôtel de Ville → Marais</h3>
<p>Storia, architettura, gallerie e passeggiate.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%204%20-%20Le%20Marais">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Le+Marais+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 05 — Filosofia</span>
<h3>Saint-Germain → Sorbona → Panthéon</h3>
<p>La Parigi dei filosofi, degli scrittori e degli studenti.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%205%20-%20Filosofia">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Saint+Germain+des+Pres+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 06 — Versailles</span>
<h3>Palazzo → Giardini → Grand Trianon</h3>
<p>Una giornata fuori dal centro di Parigi dedicata alla storia francese.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%206%20-%20Versailles">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Palace+of+Versailles" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 07 — Parigi moderna</span>
<h3>La Défense → architettura contemporanea</h3>
<p>Una Parigi completamente diversa da quella delle cartoline.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%207%20-%20La%20Defense">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=La+Defense+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 08 — Belle Époque</span>
<h3>Opéra → Galeries Lafayette → Grands Boulevards</h3>
<p>Architettura, moda, grandi magazzini e storia urbana.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%208%20-%20Opera">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Opera+Garnier+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 09 — Natura</span>
<h3>Jardin du Luxembourg → Bois de Boulogne</h3>
<p>Una giornata più lenta tra giardini e spazi verdi.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%209%20-%20Natura">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Jardin+du+Luxembourg+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 10 — Cultura</span>
<h3>Centre Pompidou → Marais → librerie</h3>
<p>Arte moderna, cultura contemporanea e ricerca di libri.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%2010%20-%20Cultura">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Centre+Pompidou+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 11 — Senna</span>
<h3>Pont Neuf → Île Saint-Louis → crociera</h3>
<p>Guardare Parigi dall'acqua e attraversare la città lentamente.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%2011%20-%20Senna">Calendario</a>
<a class="map-button" href="https://www.google.com/maps/search/?api=1&query=Pont+Neuf+Paris" target="_blank">Google Maps</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


<div class="day">
<span class="day-number">Giorno 12 — Senza programma</span>
<h3>Il giorno della scoperta</h3>
<p>Nessun itinerario. Scegliere un quartiere e camminare senza una destinazione precisa.</p>
<a class="calendar-button" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Parigi%20-%20Giorno%2012%20-%20Esplorazione">Calendario</a>
<button class="visited-button" onclick="toggleVisited(this)">Non ancora visitato</button>
</div>


</div>

</section>


<!-- MAPPA -->

<section id="mappa">

<span class="label">05 — Mappa</span>

<h2>La mia Parigi.</h2>

<div class="map-info">
Clicca sui punti della mappa.
Puoi aprire il luogo su Google Maps oppure segnarlo come visitato.
</div>

<div id="map"></div>

</section>


<!-- IDEE NASCOSTE -->

<section id="segreti">

<span class="label">06 — Oltre le cartoline</span>

<h2>Cose da cercare.</h2>

<div class="list">

<div class="list-item">
<strong>Una libreria indipendente</strong>
<p>Entrare senza cercare necessariamente qualcosa da comprare.</p>
</div>

<div class="list-item">
<strong>Un mercato di quartiere</strong>
<p>Guardare la città mentre fa la spesa, non mentre aspetta i turisti.</p>
</div>

<div class="list-item">
<strong>Un museo piccolo</strong>
<p>Non dedicare tutto il viaggio ai grandi musei.</p>
</div>

<div class="list-item">
<strong>Un caffè senza itinerario</strong>
<p>Scegliere un tavolino e osservare la strada per mezz'ora.</p>
</div>

<div class="list-item">
<strong>Una passeggiata notturna</strong>
<p>La città dopo il tramonto è un'altra città.</p>
</div>

<div class="list-item">
<strong>Perdersi</strong>
<p>Una volta durante il viaggio, togliere Google Maps e camminare.</p>
</div>

</div>

</section>


<div class="quote">

<p>
"Parigi è una città da vedere con gli occhi,
ma soprattutto con il tempo."
</p>

<small>IL MIO TACCUINO — 2026</small>

</div>


<footer>

<p>PARIGI — IL MIO TACCUINO</p>

<p>Un progetto personale in continua evoluzione.</p>

</footer>


<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>

/* BARRA DI PROGRESSO */

window.addEventListener("scroll", function() {

    const scrollTop = document.documentElement.scrollTop;
    const height =
        document.documentElement.scrollHeight -
        document.documentElement.clientHeight;

    const progress = (scrollTop / height) * 100;

    document.getElementById("progress").style.width =
        progress + "%";
});


/* CALENDARIO */

let currentMonth = 7;
let currentYear = 2026;

const months = [
    "Gennaio",
    "Febbraio",
    "Marzo",
    "Aprile",
    "Maggio",
    "Giugno",
    "Luglio",
    "Agosto",
    "Settembre",
    "Ottobre",
    "Novembre",
    "Dicembre"
];

const calendarEvents = {
    "2026-08-01": "Arrivo a Parigi",
    "2026-08-02": "Centro storico",
    "2026-08-03": "Arte",
    "2026-08-04": "Montmartre",
    "2026-08-05": "Le Marais",
    "2026-08-06": "Filosofia",
    "2026-08-07": "Versailles",
    "2026-08-08": "Parigi moderna",
    "2026-08-09": "Belle Époque",
    "2026-08-10": "Natura",
    "2026-08-11": "Cultura",
    "2026-08-12": "Senna"
};

function renderCalendar() {

    const calendar =
        document.getElementById("calendar");

    calendar.innerHTML = "";

    document.getElementById("monthTitle").innerText =
        months[currentMonth] + " " + currentYear;

    const firstDay =
        new Date(currentYear, currentMonth, 1).getDay();

    const daysInMonth =
        new Date(currentYear, currentMonth + 1, 0).getDate();

    let start = firstDay === 0 ? 6 : firstDay - 1;

    for(let i = 0; i < start; i++) {

        const empty = document.createElement("div");

        empty.className = "calendar-day";

        calendar.appendChild(empty);
    }

    for(let day = 1; day <= daysInMonth; day++) {

        const box = document.createElement("div");

        box.className = "calendar-day";

        box.innerHTML = "<strong>" + day + "</strong>";

        const dateKey =
            currentYear + "-" +
            String(currentMonth + 1).padStart(2, "0") + "-" +
            String(day).padStart(2, "0");

        if(calendarEvents[dateKey]) {

            box.innerHTML +=
                '<div class="calendar-event">' +
                calendarEvents[dateKey] +
                '</div>';
        }

        box.onclick = function() {

            document.getElementById("selectedDate").innerText =
                "Hai selezionato: " +
                day + " " +
                months[currentMonth] +
                " " +
                currentYear +
                (calendarEvents[dateKey]
                    ? " — " + calendarEvents[dateKey]
                    : "");

        };

        calendar.appendChild(box);
    }
}

function previousMonth() {

    currentMonth--;

    if(currentMonth < 0) {

        currentMonth = 11;
        currentYear--;
    }

    renderCalendar();
}

function nextMonth() {

    currentMonth++;

    if(currentMonth > 11) {

        currentMonth = 0;
        currentYear++;
    }

    renderCalendar();
}

renderCalendar();


/* VISITATO */

function toggleVisited(button) {

    button.classList.toggle("done");

    if(button.classList.contains("done")) {

        button.innerText = "✓ Visitato";

    } else {

        button.innerText = "Non ancora visitato";
    }
}


/* MAPPA */

const map =
    L.map("map").setView(
        [48.8566, 2.3522],
        12
    );

L.tileLayer(
    "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
    {
        attribution:
        '&copy; OpenStreetMap contributors'
    }
).addTo(map);


const places = [

    {
        name: "Tour Eiffel",
        lat: 48.8584,
        lng: 2.2945
    },

    {
        name: "Louvre",
        lat: 48.8606,
        lng: 2.3376
    },

    {
        name: "Notre-Dame",
        lat: 48.8530,
        lng: 2.3499
    },

    {
        name: "Sacré-Cœur",
        lat: 48.8867,
        lng: 2.3431
    },

    {
        name: "Musée d'Orsay",
        lat: 48.8600,
        lng: 2.3266
    },

    {
        name: "Centre Pompidou",
        lat: 48.8606,
        lng: 2.3522
    },

    {
        name: "Panthéon",
        lat: 48.8462,
        lng: 2.3464
    },

    {
        name: "Jardin du Luxembourg",
        lat: 48.8462,
        lng: 2.3372
    },

    {
        name: "Place des Vosges",
        lat: 48.8555,
        lng: 2.3658
    },

    {
        name: "Canal Saint-Martin",
        lat: 48.8721,
        lng: 2.3655
    },

    {
        name: "Opéra Garnier",
        lat: 48.8719,
        lng: 2.3316
    },

    {
        name: "Arc de Triomphe",
        lat: 48.8738,
        lng: 2.2950
    },

    {
        name: "Champs-Élysées",
        lat: 48.8698,
        lng: 2.3078
    },

    {
        name: "Pont Neuf",
        lat: 48.8584,
        lng: 2.3419
    },

    {
        name: "Île Saint-Louis",
        lat: 48.8518,
        lng: 2.3560
    },

    {
        name: "Saint-Germain-des-Prés",
        lat: 48.8546,
        lng: 2.3332
    },

    {
        name: "Sorbona",
        lat: 48.8488,
        lng: 2.3449
    },

    {
        name: "Montparnasse",
        lat: 48.8422,
        lng: 2.3219
    },

    {
        name: "Belleville",
        lat: 48.8720,
        lng: 2.3820
    },

    {
        name: "La Villette",
        lat: 48.8937,
        lng: 2.3908
    },

    {
        name: "La Défense",
        lat: 48.8924,
        lng: 2.2369
    },

    {
        name: "Versailles",
        lat: 48.8049,
        lng: 2.1204
    }

];


places.forEach(function(place) {

    const marker =
        L.marker([
            place.lat,
            place.lng
        ]).addTo(map);

    const googleMaps =
        "https://www.google.com/maps/search/?api=1&query=" +
        encodeURIComponent(place.name + " Paris");

    const calendar =
        "https://calendar.google.com/calendar/render?action=TEMPLATE&text=" +
        encodeURIComponent(
            "Parigi — " + place.name
        );

    marker.bindPopup(

        "<strong>" +
        place.name +
        "</strong>" +

        "<br><br>" +

        '<a href="' +
        googleMaps +
        '" target="_blank">Apri Google Maps</a>' +

        "<br><br>" +

        '<a href="' +
        calendar +
        '" target="_blank">Aggiungi al calendario</a>'
    );

});

</script>

</body>
</html>