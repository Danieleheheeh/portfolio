<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Il mio spazio</title>

    <style>
        * {
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            margin: 0;
            font-family: Georgia, "Times New Roman", serif;
            background: #f3efe6;
            color: #27251f;
            line-height: 1.7;
        }

        header {
            position: sticky;
            top: 0;
            z-index: 10;
            background: rgba(39, 37, 31, 0.96);
            padding: 18px 8%;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        header h1 {
            margin: 0;
            color: #f3efe6;
            font-size: 22px;
            letter-spacing: 1px;
        }

        nav a {
            color: #f3efe6;
            text-decoration: none;
            margin-left: 24px;
            font-family: Arial, sans-serif;
            font-size: 14px;
        }

        nav a:hover {
            color: #c8a96b;
        }

        .hero {
            min-height: 85vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 60px 20px;
            background:
                radial-gradient(circle at top, #d9cdb8, #f3efe6 65%);
        }

        .hero span {
            font-family: Arial, sans-serif;
            text-transform: uppercase;
            letter-spacing: 4px;
            font-size: 12px;
            color: #806b43;
        }

        .hero h2 {
            font-size: clamp(48px, 9vw, 92px);
            line-height: 1;
            margin: 25px 0;
            font-weight: normal;
        }

        .hero p {
            max-width: 650px;
            font-size: 20px;
            color: #5d594f;
        }

        .button {
            display: inline-block;
            margin-top: 25px;
            padding: 13px 28px;
            background: #27251f;
            color: white;
            text-decoration: none;
            font-family: Arial, sans-serif;
            border-radius: 30px;
        }

        .button:hover {
            background: #806b43;
        }

        section {
            max-width: 1050px;
            margin: auto;
            padding: 100px 25px;
        }

        .section-label {
            font-family: Arial, sans-serif;
            text-transform: uppercase;
            letter-spacing: 3px;
            font-size: 11px;
            color: #806b43;
        }

        section h2 {
            font-size: 42px;
            font-weight: normal;
            margin: 10px 0 30px;
        }

        .about {
            max-width: 750px;
            font-size: 19px;
        }

        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
        }

        .card {
            background: #fffdf8;
            padding: 35px;
            border: 1px solid #ded6c7;
            transition: transform 0.25s ease, box-shadow 0.25s ease;
        }

        .card:hover {
            transform: translateY(-6px);
            box-shadow: 0 15px 35px rgba(39, 37, 31, 0.10);
        }

        .card .number {
            font-family: Arial, sans-serif;
            font-size: 12px;
            color: #806b43;
        }

        .card h3 {
            font-size: 28px;
            font-weight: normal;
            margin: 15px 0;
        }

        .card p {
            color: #625e54;
        }

        .quote {
            background: #27251f;
            color: #f3efe6;
            text-align: center;
            max-width: none;
            padding: 100px 25px;
        }

        .quote p {
            max-width: 800px;
            margin: auto;
            font-size: 32px;
            font-style: italic;
            line-height: 1.4;
        }

        .projects {
            display: grid;
            gap: 20px;
        }

        .project {
            padding: 30px 0;
            border-bottom: 1px solid #cfc6b6;
        }

        .project h3 {
            font-size: 25px;
            font-weight: normal;
            margin: 0 0 8px;
        }

        footer {
            background: #27251f;
            color: #bdb6a9;
            text-align: center;
            padding: 40px 20px;
            font-family: Arial, sans-serif;
            font-size: 13px;
        }

        @media (max-width: 650px) {
            header {
                flex-direction: column;
                gap: 12px;
            }

            nav a {
                margin: 0 7px;
            }

            .hero h2 {
                font-size: 55px;
            }

            section h2 {
                font-size: 35px;
            }

            .quote p {
                font-size: 25px;
            }
        }
    </style>
</head>

<body>

<header>
    <h1>Il mio spazio</h1>

    <nav>
        <a href="#chi-sono">Chi sono</a>
        <a href="#interessi">Interessi</a>
        <a href="#progetti">Progetti</a>
    </nav>
</header>


<section class="hero">

    <span>Idee · Cultura · Curiosità</span>

    <h2>Il mio spazio</h2>

    <p>
        Un luogo personale dove raccogliere idee,
        passioni, progetti e cose che vale la pena scoprire.
    </p>

    <a class="button" href="#chi-sono">Entra</a>

</section>


<section id="chi-sono">

    <span class="section-label">01 — Chi sono</span>

    <h2>Un viaggio tra idee e interessi</h2>

    <div class="about">

        <p>
            Questo è il mio spazio personale.
            Un luogo in continua evoluzione dove raccogliere
            ciò che mi interessa, ciò che studio e ciò che scopro.
        </p>

        <p>
            Mi interessano la filosofia, l'arte, la finanza,
            la storia, la letteratura e la natura.
            Non come mondi separati, ma come prospettive diverse
            attraverso cui osservare il mondo.
        </p>

    </div>

</section>


<section id="interessi">

    <span class="section-label">02 — Interessi</span>

    <h2>Le cose che mi fanno pensare</h2>

    <div class="cards">

        <div class="card">
            <span class="number">01</span>
            <h3>Filosofia</h3>
            <p>
                Domande, pensatori e idee sul significato
                dell'esistenza, sulla società e sull'uomo.
            </p>
        </div>

        <div class="card">
            <span class="number">02</span>
            <h3>Arte</h3>
            <p>
                Pittura, architettura, estetica e opere
                capaci di raccontare qualcosa oltre le parole.
            </p>
        </div>

        <div class="card">
            <span class="number">03</span>
            <h3>Finanza</h3>
            <p>
                Economia, mercati, investimenti e comprensione
                dei meccanismi che muovono il capitale.
            </p>
        </div>

        <div class="card">
            <span class="number">04</span>
            <h3>Storia</h3>
            <p>
                Eventi, persone e civiltà del passato
                per comprendere meglio il presente.
            </p>
        </div>

        <div class="card">
            <span class="number">05</span>
            <h3>Letteratura</h3>
            <p>
                Libri, autori e parole capaci di cambiare
                il modo in cui guardiamo la realtà.
            </p>
        </div>

        <div class="card">
            <span class="number">06</span>
            <h3>Natura</h3>
            <p>
                Paesaggi, esplorazione e osservazione
                del mondo naturale.
            </p>
        </div>

    </div>

</section>


<div class="quote">

    <p>
        "La curiosità è il principio di ogni conoscenza."
    </p>

</div>


<section id="progetti">

    <span class="section-label">03 — Progetti</span>

    <h2>Quello che verrà</h2>

    <div class="projects">

        <div class="project">
            <h3>Il mio primo progetto</h3>
            <p>
                Questo sito è il primo passo.
                Da qui nasceranno nuove idee e nuovi progetti.
            </p>
        </div>

        <div class="project">
            <h3>Appunti e riflessioni</h3>
            <p>
                Una raccolta di pensieri, letture,
                scoperte e riflessioni personali.
            </p>
        </div>

        <div class="project">
            <h3>Progetti futuri</h3>
            <p>
                Uno spazio aperto a nuove idee,
                esperimenti e collaborazioni.
            </p>
        </div>

    </div>

</section>


<footer>

    <p>© 2026 — Il mio spazio personale</p>

</footer>

</body>
</html>