 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Personal Portfolio</title>

    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: #f4f1ea;
            color: #222;
        }

        header {
            background: #222;
            color: white;
            padding: 20px 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        header h1 {
            margin: 0;
            font-size: 24px;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin-left: 20px;
        }

        .hero {
            text-align: center;
            padding: 100px 20px;
            background: #ded7c9;
        }

        .hero h2 {
            font-size: 50px;
            margin-bottom: 15px;
        }

        .hero p {
            font-size: 20px;
        }

        section {
            max-width: 900px;
            margin: auto;
            padding: 70px 20px;
        }

        section h2 {
            font-size: 32px;
            margin-bottom: 25px;
        }

        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
        }

        .card {
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
        }

        .card h3 {
            font-size: 24px;
        }

        footer {
            text-align: center;
            padding: 30px;
            background: #222;
            color: white;
        }
    </style>
</head>

<body>

<header>
    <h1>My Portfolio</h1>

    <nav>
        <a href="#about">About</a>
        <a href="#interests">Interests</a>
        <a href="#projects">Projects</a>
    </nav>
</header>

<div class="hero">
    <h2>Personal Portfolio</h2>
    <p>Ideas, interests, projects and discoveries.</p>
</div>

<section id="about">
    <h2>About Me</h2>

    <p>
        Welcome to my personal portfolio.
        This website is a space where I collect my interests,
        ideas, projects and things I discover over time.
    </p>
</section>

<section id="interests">
    <h2>My Interests</h2>

    <div class="cards">

        <div class="card">
            <h3>Philosophy</h3>
            <p>
                Ideas, thinkers, questions and reflections
                about human existence and society.
            </p>
        </div>

        <div class="card">
            <h3>Art</h3>
            <p>
                Painting, architecture, aesthetics,
                artists and works that inspire me.
            </p>
        </div>

        <div class="card">
            <h3>Finance</h3>
            <p>
                Markets, economics, investing and
                understanding how money and economies work.
            </p>
        </div>

    </div>
</section>

<section id="projects">
    <h2>Projects</h2>

    <div class="card">
        <h3>Coming Soon</h3>
        <p>
            This section will contain my future projects,
            ideas and experiments.
        </p>
    </div>
</section>

<footer>
    <p>© 2026 My Personal Portfolio</p>
</footer>

</body>
</html>
