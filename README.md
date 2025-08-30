<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instituto Polivalente San José de Cupertino</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        /* ----------------- RESET Y ESTILOS GENERALES ----------------- */
        * { margin:0; padding:0; box-sizing:border-box; font-family:'Poppins', sans-serif; }
        body { background:#f5f5f5; color:#333; line-height:1.6; overflow-x:hidden; }
        a { text-decoration:none; }
        img { max-width:100%; display:block; }

        /* ----------------- HEADER ----------------- */
        header { 
            background:#0056a6; 
            color:#fff; 
            padding:15px 50px; 
            display:flex; 
            justify-content:space-between; 
            align-items:center; 
            position:fixed; 
            top:0; 
            width:100%; 
            z-index:1000; 
            border-bottom: 3px solid #ffd700; 
        }
        header .logo-title { display:flex; align-items:center; gap:15px; }
        header img { height:50px; border-radius:8px; }
        header h1 { font-size:22px; font-weight:700; }
        nav a { color:#fff; margin-left:20px; font-weight:500; transition:color 0.3s; }
        nav a:hover { color:#ffd700; }

        /* ----------------- HERO ----------------- */
        .hero {
            height:80vh;
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url("img/fondo.png") center/cover no-repeat;
            display:flex;
            justify-content:center;
            align-items:center;
            text-align:center;
            color:#fff;
            position:relative;
            padding:20px;
            margin-top: 70px; /* Este margen ayuda a que no se superponga con el header */
        }
        .hero h2 { font-size:3rem; text-shadow:2px 2px 8px rgba(0,0,0,0.6); }
        .hero p { font-size:1.2rem; margin-top:15px; text-shadow:1px 1px 5px rgba(0,0,0,0.5); }
        .hero .btn { display:inline-block; background:linear-gradient(45deg,#ffd700,#ffae00); color:#000; padding:15px 30px; margin-top:20px; border-radius:30px; font-weight:700; position:relative; overflow:hidden; transition:all 0.4s; }
        .hero .btn:hover { transform:scale(1.05); color:#fff; }

        /* ----------------- CARRUSEL DE IMÁGENES ----------------- */
        .carousel-container { 
            position:relative; 
            max-width:1000px; 
            margin:40px auto; 
            overflow:hidden; 
            border-radius:12px; 
            box-shadow:0 6px 16px rgba(0,0,0,0.15); 
        }
        .carousel-title { text-align:center; font-size:2rem; color:#0056a6; margin-bottom:15px; }
        .carousel-slide { display:flex; width:100%; height:400px; }
        .carousel-btn { 
            position:absolute; 
            top:50%; 
            transform:translateY(-50%); 
            background-color:rgba(0,0,0,0.4); 
            color:white; 
            padding:15px; 
            cursor:pointer; 
            z-index:1; 
            font-size:1.5rem; 
            border-radius:50%; 
            width:50px; 
            height:50px; 
            display:flex; 
            align-items:center; 
            justify-content:center; 
        }
        .carousel-btn:hover { background-color:rgba(0,0,0,0.7); }
        .carousel-nav { position:absolute; bottom:20px; left:50%; transform:translateX(-50%); display:flex; gap:10px; z-index:1; }
        .carousel-indicator { width:12px; height:12px; background-color:rgba(255,255,255,0.5); border-radius:50%; cursor:pointer; }
        .carousel-indicator.active { background-color:white; }

        /* ----------------- SECCIONES ----------------- */
        section { padding:60px 50px; max-width:1200px; margin:auto; }
        section h2 { text-align:center; margin-bottom:40px; font-size:2rem; color:#0056a6; }

        /* ----------------- NOSOTROS ----------------- */
        .nosotros { display:grid; grid-template-columns:1fr 1fr; gap:30px; align-items:center; }
        .nosotros img { border-radius:15px; box-shadow:0 10px 25px rgba(0,0,0,0.15); }
        .nosotros p { font-size:1.05rem; }

        /* ----------------- MISION Y VISION ----------------- */
        .mision-vision { display:grid; grid-template-columns:1fr 1fr; gap:30px; text-align:center; }
        .mision-vision div { background:#fff; padding:25px; border-radius:15px; box-shadow:0 10px 25px rgba(0,0,0,0.15); }
        .mision-vision h3 { color:#0056a6; margin-bottom:15px; }

        /* ----------------- PROGRAMAS ----------------- */
        .cards { display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:20px; }
        .card { background:#fff; padding:20px; border-radius:15px; box-shadow:0 10px 25px rgba(0,0,0,0.15); text-align:center; }
        .card h3 { margin-bottom:10px; color:#0056a6; }
        .card p { font-size:1rem; }

        /* ----------------- ADMISIONES ----------------- */
        .admisiones ul { list-style:none; max-width:700px; margin:auto; padding:0; }
        .admisiones ul li { background:#fff; padding:18px; margin:12px 0; border-radius:12px; box-shadow:0 8px 20px rgba(0,0,0,0.1); }

        /* ----------------- CONTACTO ----------------- */
        .contacto form { display:flex; flex-direction:column; max-width:650px; margin:auto; padding:30px; background:#fff; border-radius:15px; box-shadow:0 15px 35px rgba(0,0,0,0.15); }
        .contacto input, .contacto textarea { padding:18px; margin:12px 0; border:1px solid #ccc; border-radius:12px; }
        .contacto button { background:#0056a6; color:#fff; border:none; padding:18px; border-radius:12px; cursor:pointer; font-weight:700; font-size:16px; margin-top:10px; }

        /* ----------------- FOOTER ----------------- */
        footer { background:#003f75; color:#fff; text-align:center; padding:20px; margin-top:40px; }

        /* ----------------- RESPONSIVE ----------------- */
        @media(max-width:900px){ 
            .nosotros, .mision-vision { grid-template-columns:1fr; } 
            header { flex-direction:column; text-align:center; gap:10px; } 
            nav a { margin:5px; } 
            .carousel-slide{height:250px;} 
            .hero h2{font-size:2rem;} 
            .hero p{font-size:1rem;} 
        }
    </style>
</head>
<body>

<!-- ----------------- HEADER ----------------- -->
<header>
  <div class="logo-title">
    <img src="img/logo.png" alt="Logo Instituto Polivalente San José de Cupertino">
    <h1>Instituto Polivalente San José de Cupertino</h1>
  </div>
  <nav>
    <a href="#nosotros">Nosotros</a>
    <a href="#mision-vision">Misión y Visión</a>
    <a href="#programas">Programas</a>
    <a href="#admisiones">Admisiones</a>
    <a href="#contacto">Contacto</a>
  </nav>
</header>

<!-- ----------------- HERO ----------------- -->
<section class="hero">
  <div>
    <h2>Formando Líderes del Futuro</h2>
    <p>Educación integral con valores y excelencia académica</p>
    <a href="#contacto" class="btn">Inscríbete Ahora</a>
  </div>
</section>

<!-- ----------------- CARRUSEL DE IMÁGENES ----------------- -->
<div class="carousel-container">
  <div class="carousel-title">Galería del Instituto</div>
  <div class="carousel-slide">
    <img src="img/imagen1.png" alt="Instalaciones del Instituto">
    <img src="img/imagen2.png" alt="Estudiantes en clase">
    <img src="img/imagen3.png" alt="Actividades extracurriculares">
  </div>
  <button class="carousel-btn" id="prevBtn">&#10094;</button>
  <button class="carousel-btn" id="nextBtn">&#10095;</button>
</div>

<!-- ----------------- SECCIONES ----------------- -->
<section id="nosotros">
  <h2>Sobre Nosotros</h2>
  <div class="nosotros">
    <img src="https://images.unsplash.com/photo-1596495577886-d920f1fb7238?auto=format&fit=crop&w=900&q=80" alt="Aulas modernas">
    <p>
      En el Instituto Polivalente San José de Cupertino creemos en una educación moderna, con instalaciones de primer nivel,
      programas innovadores y un equipo docente comprometido con el futuro de nuestros estudiantes.
    </p>
  </div>
</section>

<!-- ----------------- FOOTER ----------------- -->
<footer>
  <p>&copy; 2025 Instituto Polivalente San José de Cupertino | Todos los derechos reservados</p>
</footer>

<script>
// Aquí van tus scripts de interactividad
</script>

</body>
</html>

