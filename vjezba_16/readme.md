# Vježba 16 – Selektori atributa i pseudo klase na meniju i galeriji

U ovoj vježbi nadograđujemo LEGO projekt:

1. primijenit ćete **selektore atributa i pseudo klase** na linkove u **glavnom izborniku (menu)**  
2. izradit ćete **novu stranicu `galerija.html`** s jednostavnom **galerijom slika**, gdje ćete primijeniti selektore atributa na `<img>` elementima.

Cilj je napraviti:
- selektore atributa: `[attr]`, `[attr="vrijednost"]`, `[attr^=""]`, `[attr$=""]`, `[attr*=""]`
- pseudo klase: `:hover`, `:focus`, `:active`, `:visited`
- osnovno korištenje `::after` (pseudo element) u kombinaciji s atribut selektorom (za vanjsku poveznicu)

---

## 1. Nadogradnja navigacije (menu)

### 1.1. Dodavanje linka na galeriju i vanjsku stranicu

1. U datotekama u kojima imate glavni izbornik (npr. `index.html`, `kontakt.html`), pronađite `<nav class="main-nav">`.
2. U listu dodajte:
   - novi link **„Galerija”** koji vodi na novu stranicu `galerija.html`
   - još jedan link koji vodi na **službenu LEGO stranicu** i otvara se u novom tabu

Primjer strukture (možete prilagoditi tekst, važno je da atributi ostanu):

```html
<nav class="main-nav">
    <ul>
        <li><a href="index.html">Početna</a></li>
        <li><a href="#">O nama</a></li>
        <li><a href="#">Radionice</a></li>
        <li><a href="kontakt.html">Kontakt</a></li>
        <li><a href="galerija.html">Galerija</a></li>
        <li><a href="https://www.lego.com" target="_blank">LEGO službena stranica</a></li>
    </ul>
</nav>
```

## 1.2. CSS zadatak za meni

U vašoj CSS datoteci (npr. style.css) dodajte pravila za:

### 1.2.1 Osnovni izgled linkova u meniju

stilizirajte `.main-nav` a tako da svi linkovi izgledaju kao gumbi (padding, bez podcrtavanja, osnovna boja teksta i pozadine).

### 1.2.2 Pseudo klase na linkovima

**:hover** – kad je miš iznad linka, neka se pozadina ili boja teksta promijeni

**:focus** – kad je link u fokusu (tipkovnica), neka ima sličan efekt kao na :hover

**:active** – kratki efekt „pritisnutog” gumba

**:visited** – po želji promijenite nijansu boje za već posjećene linkove

### 1.2.3 Selektori atributa na linkovima

posebnim stilom istaknite link koji vodi na galeriju:

primjer selektora:
`nav.main-nav a[href="galerija.html"] { ... }`
ili
`nav.main-nav a[href*="galerija"] { ... }`

posebnim stilom istaknite vanjski link koji se otvara u novom tabu:

`selektor: nav.main-nav a[target="_blank"] { ... }`

dodajte mali simbol (strelicu) iza vanjskog linka koristeći pseudo element i selektor atributa:

npr. `nav.main-nav a[target="_blank"]::after { content: " ↗"; }`

# 2. Nova stranica – galerija slika

## 2.1. Izrada datoteke galerija.html

U mapi projekta kreirajte novu datoteku galerija.html.

Kopirajte osnovnu strukturu (doctype, `<html>`, `<head>`, `<body>`, header s menijem, footer) s neke postojeće stranice (npr. index.html).

Unutar `<main>` elementa dodajte sekciju:

```html
<main>

    <section class="lego-gallery">
        <h2>Galerija LEGO setova</h2>
        <p>Ovdje možete vidjeti nekoliko LEGO setova iz naše kolekcije.</p>

        <div class="gallery-row">
            <img src="img/lego_city_1.jpg" alt="LEGO City Formula 1" data-set="city">
            <img src="img/lego_technic_1.jpg" alt="LEGO Technic trkaći auto" data-set="technic">
            <img src="img/lego_friends_1.jpg" alt="LEGO Friends kafić" data-set="friends">
        </div>

        <div class="gallery-row">
            <img src="img/lego_city_2.jpg" alt="LEGO City vatrogasci" data-set="city">
            <img src="img/lego_technic_2.jpg" alt="LEGO Technic helikopter" data-set="technic">
            <img src="img/lego_friends_2.jpg" alt="LEGO Friends kuća" data-set="friends">
        </div>
    </section>

</main>
```

Ako nemate ovakve slike, slobodno iskoristite druge .jpg slike i zadržite atribute alt i data-set (city / technic / friends).

## 2.2. CSS zadatak za galeriju

U **style.css** dodajte:

Raspored slika „jedna do druge”

`.lego-gallery` centrirajte i ograničite širinu (npr. max-width).

`.gallery-row` napravite kao fleks-kontejner tako da su tri slike u jednom redu.

slike neka imaju width tako da stanu tri u red, s razmakom (gap ili margin).

Selektori atributa na slikama

Svim slikama koje imaju `data-set="city"` dodajte plavi okvir.

Svim slikama koje imaju `data-set="technic"` dodajte npr. narančasti okvir.

Svim slikama koje imaju `data-set="friends"` dodajte ružičasti okvir.

Iskoristite i još jedan selektor atributa, npr. sve slike koje su .jpg:

```css
.lego-gallery img[src$=".jpg"] { border-radius: 8px; }
```

Pseudo klase na slikama

Dodajte `:hover` efekt na slike u galeriji (npr. blagi zoom i sjena).

Po želji, dodajte i `cursor: pointer;` na hover kako bi se vidjelo da je slika „interaktivna”.

# 3. Deklaracije

Možete koristiti neke od ovih deklaracija (kombinirajte ih uz ispravne selektore):

```css
/* Meni */
display: inline-block;
padding: 0.5rem 1rem;
text-decoration: none;
background-color: #333333;
color: #ffffff;

background-color: #555555;   /* :hover */
outline: 2px solid #ffffff;  /* :focus */
transform: scale(0.97);      /* :active */

/* Galerija */
display: flex;
gap: 1rem;
max-width: 900px;
margin: 2rem auto;

width: 100%;
border: 4px solid blue;
border: 4px solid orange;
border: 4px solid deeppink;

border-radius: 8px;
box-shadow: 0 0 10px rgba(0,0,0,0.3);
transform: scale(1.03);
cursor: pointer;
```
