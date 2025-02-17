# Teknisk dokumentation for Tema 7 gruppeprojekt

Når man er flere der bidrager til en kodebase, lærer man hurtigt, at ens sædvanlige måder at gøre tingene på ikke nødvendigvis er logisk for alle.

Skriv derfor jeres fælles retningslinjer for punkterne herunder(tilføj gerne flere selv), sådan som det giver bedst mening for jer som gruppe. Dokumentationen sikre, at jeres fælles kodebase forbliver overskuelig, er let at arbejde med og til at forstå for alle, og at I undgå konflikter, og har nemmere ved at hjælpe hinanden undervejs.

## Projektstruktur

Alle billeder skal i mappen kaldet imgs, i en undermappe med samme navn som siden. Ligger billeder ikke i en undermappe, er det fordi de bruges på flere sider. Fonte skal i mappen fonts, javascript skal i mappen js, CSS skal i mappen css, html-filer (udover index.html) skal i mappen html.

## Navngivning

Filer navngives med småt, uden mellemrum. Er der brug for mellemrum i navnet bruges underscore. Filer der hører sammen navngives det samme - fx. index.html, index.css, index.js. Filer kan også navngives efter et element, hvis de bruges til et element der figurerer på flere sider - fx. menu.css, menu.js.

## Link til scripts

Links til scripts placeres til sidst i body.

## Git branches

Branches navngives med en beskrivende titel i lower camel-case, efterfulgt af en bindestreg efterfulgt af navnet på den der arbejder på branchen. Fx. cssReset-mikkel, indexDesktop-lukas, singleDesktop-sille. Titlen skal være beskrivende, og skal kunne idenficeres med en arbejdsopgave på scrum-boardet.

## Arbejdsflow

- Hvordan fordeler I arbejdet, så I undgår at flere arbejder i de samme filer samtidigt?
- Hvordan sikrer I, at commit-beskeder er beskrivende?
- Hvordan kommunikerer i om ændringer i main branchen når feature merges?

### Scrum + Git Arbejdsflow

Alle filer er relateret til en arbejdsopgave på vores scrumboard. Ved at bruge scrum-boardet, sikrer vi at der ikke arbejdes på de samme filer samtidigt. Filer der bruges på flere sider, skal have en selvstændig arbejdsopgave, samt branch tilknyttet.

### Commit-beskeder

Commit-beskeder skrives altid på engelsk, og følger en forsimplet udgave af conventional commit specification (<https://www.conventionalcommits.org/en/v1.0.0/>), og struktureres således:

```bash
<type>[scope]: <description>

[body]

# Eksempler
feat(css): add global variabler

Added global color variables to CSS.

####################################

docs(readme): add javascript styleguide to readme

Added javascript styleguide to readme.

####################################

feat(js): add auto-hide to global menu

Added an auto-hide on scroll function to the global menu, so users have more screenspace for content.
```

## Kode

- Hvordan skriver i funktioner i JavaScript?(fx med function keyword eller som arrow functions)
- Beslut hvilken CSS selector i benyttes til referener i henholdsvis CSS og JavaScript(fx. id'er til JavaScript og Classes til CSS)
- Skal filer have korte forklaringer som kommentarer?

### JavaScript styleguide

Dette er vores styleguide til JavaScript. Guiden beskriver følgende:

- Navgivning af funktioner, variabler, filer m.v.
- Strukturering af kode
- Brug af variabler eller konstanter
- Brug af funktioner
- Hvor, hvornår og hvordan bruger man kommentarer

#### JS Navngivning

Navne er altid på engelsk, hvad enten der er tale om filnavne eller navne på funktioner eller lignende i selve koden.

##### Filnavne

Alle javascript filer navngives efter den html-fil eller det element det inteagerer med. Navne skal skrives med småt, og der må ikke være mellemrum. Er der flere ord i navnet adskilles de med underscore.

Eksempel:

> index.js, menu.js, contact_form.js.

##### Variabler og konstanter

Variabler navngives med et beskrivende navn, skrevet i lower camel-case.

```javascript
// KORREKT
let firstName = "Sofie";
let lastName = "Jensen";

// FORKERT
let variabelEt = "Sofie";
let VariabelTo = "Jensen";
let FirstName = "Jan";
let NAVN = "Mikkel";
```

Konstanter navngives med et beskrivende navn skrevet med store bogstaver med underscore som mellemrum, medmindre der er tale om et local alias (fx en queryselector), hvor det navgives efter den sidste del af queryselector (det valgte element), skrevet i lower camel-case. Det gælder også for konstanter der er en del af en funktion.

Eksempler:

```javascript
// KORREKT
const NUMBER = 5;
const FETCH_LIMIT = 20;
const productContainer = document.queryselector(".product_container");

function myFunction() {
  const fetchLimit = 20;
}

// FORKERT
const number = 5;
const fetchLimit = 20;
const product_container = document.queryselector(".product_container");

function myFunction() {
  const FETCH_LIMIT = 20;
}
```

Funktioner navgives med lower camel-case:

```javascript
// KORREKT
function myFunction () {
  ...
}

// FORKERT
function MyFunction () {
  ...
}

function myfunction () {
  ...
}
```

#### JS Struktur

Ens javascript skal struktureres på følgende måde:

- local aliases
- global constants
- functions
- e.v.t. kald af funktion(er) i et script eller med eventlistener.

Hvert afsnit har en overskrift skrevet som kommentar i Caps lock. Der er to tomme linjer mellem hvert afsnit.

Eksempel:

```javascript
// LOCAL ALIASES
const productContainer = document.queryselector('.product_container');
const menuIcon = document.queryselector('menu_icon');


// EVENTLISTENER
productContainer.addEventListener('click', () => {
  ...
});
```

#### JS kommentarer

Eventuelle kommentarer i koden skrives inline, og holdes meget korte og bruges til at beskrive hvad der sker på den enkelte linje kode. Kommentarer skrives altid på engelsk.

Eksempel:

```javascript
// KORREKT
function myFunction() {
  const a = 5;
  const b = 6;

  let myValue = a + b; // calculate a + b

  return myValue;
}

// FORKERT
function myFunction() {
  const a = 5;
  const b = 6;

  let myValue = a + b; // Her udregner jeg resultatet af min funktion, det vil jeg gerne forklare hvordan jeg gør med en meget lang tekst om hvordan det hele fungerer, som du kan læse her. Jeg har også skrevet den på dansk, så hvis nogen fra udlandet vil læse min kommentar er det bare ærgeligt for dem.

  return myValue;
}
```

#### JS Variabler eller konstanter

Man bruger som udgangspunkt altid konstanter, med mindre man ved et er en værdi som skal manipuleres i koden.

#### JS Brug af arrow-funktioner

Brug som udgangspunkt altid arrow-funktioner, med mindre der er tale om en funktion der skal kaldes flere gange, forskellige steder i scriptet.

## Funktionalitet

Dette afsnit skal forklare hvad I konkret har arbejde med, for at udvikle websitet. Tænk over hvilke interaktioner brugeren kan foretage på sitet? Eller hvordan websitet håndterer og præsenterer data? Eksempler på funktionalitet, der kan beskrives:

- Hentning af produkter fra API.
- Filtrering af produkter baseret på brugerens valg.
- Dynamisk visning af produkter i HTML.

Brug korte beskrivelser, som i eksemplerne herover

# API endpoints

Dette afsnit skal liste de endpoints fra API'et i har benyttet:

- (fx. <https://dummyjson.com/products>)

# Dokumentation af Funktion

Dette afsnit skal beskrive en funktion I selv har udviklet. Det kunne eksempelvis være en funktion der generere en listen over fx. produkter:

- Beskrivelse: Hvad gør funktionen? Hvordan spiller den sammen med resten af koden?
- Parametre: Hvilke input forventes (fx en værdi fra en dropdown eller URL'en)?
- Returnerer: Beskriv, om funktionen returnerer en værdi eller blot manipulerer DOM’en.
- Eksempel på brug: Indsæt funktions-koden herunder(der hvor koden er i eksemplet) og vis, hvordan funktionen kaldes:

```javascript
//funktionens kode:
function voresFunktion(sprog) {
  console.log(`${sprog} syntax highlighting`);
}
//hvordan funktionen kaldes:
voresFunktion("JavaScript");
```
