cd .\programs\rust\gerechten_selector_web\
$env:CARGO_TARGET_DIR = "\programs\targetWindows\gerechten_selector_web\

Hier is de volledige oplossing om jouw Rust-programma om te toveren tot een interactieve web-app die perfect werkt in de browser van je iPhone.
We gebruiken hiervoor WebAssembly (WASM). Je computer compileert de Rust-code naar een supersnel pakketje dat de iPhone-browser direct lokaal kan uitvoeren. Geen servers nodig, en je kunt je bestanden direct inladen!
Eerst geef ik je een interactieve simulatie van de web-app, zodat je direct op je scherm kunt testen hoe de interface en de logica op je iPhone gaan werken. Daaronder vind je de exacte code en stappen om dit zelf te bouwen.

Hoe je dit zelf bouwt (Stappenplan)

Stap 1: Pas je Cargo.toml aan

Om Rust met de browser te laten praten, hebben we de wasm-bindgen library nodig in plaats van de terminal-library clap. Vervang de inhoud van je Cargo.toml door:

Stap 2: De Rust-code (src/lib.rs)

In plaats van een main.rs met terminal-input, maken we een lib.rs met een functie select_dishes die de browser rechtstreeks kan aanroepen. Deze functie krijgt de tekstinhoud van het bestand, de limiet P en de modus binnen als strings, en geeft het volledige resultaat als tekst terug.
Sla de volgende code op als src/lib.rs:

Stap 3: De HTML-frontend (index.html)

Maak een bestand genaamd index.html aan in de hoofdmap van je project. Dit vormt de interface die je op je iPhone te zien krijgt:

Stap 4: Compileren en online zetten

1. Installeer de compiler tool op je computer:

cargo install wasm-pack

2. Bouw het webpakket:

Run dit commando in je projectmap. Dit maakt een map genaamd pkg/ aan waar de browser-bestanden in staan:

wasm-pack build --target web

3. Zet het online:
De makkelijkste en gratis manier om dit nu op je iPhone te krijgen, is door je projectmap (met daarin index.html, src/, Cargo.toml en de gegenereerde pkg/ map) te uploaden naar GitHub en daar GitHub Pages aan te zetten via de instellingen (Settings -> Pages -> Deploy from a branch).
Zodra dat is gebeurd, genereert GitHub een link (bijvoorbeeld https://github.io). Als je die link opent in Safari op je iPhone, werkt je gerechtenselector overal, supersnel en mobielvriendelijk!
Wil je dat we nog iets finetunen voor de mobiele weergave? Ik kan:
1. De HTML-code uitbreiden zodat je het resultaat met één druk op de knop kunt kopiëren naar je klembord (om direct te appen naar de groep).
2. De website zo inrichten dat je hem als een echte app (PWA) op het startscherm van je iPhone kunt installeren, zodat hij ook offline werkt.
Laat maar weten welk nummer je eventueel wilt toevoegen!
