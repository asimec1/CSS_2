# Vježba 15 – Pseudo klase za forme i fokus

Ova vježba nadograđuje  postojeću stranicu **„Lego“** iz repozitorija `CSS_1` (mapa `vjezba_14`).  
Cilj je dodati **kontakt formu** i preko nje uvježbati pseudo klase:

- `:focus`
- `:checked`
- `:disabled`
- `:enabled`

Ne dodajemo inline stilove u HTML – **sve stiliziranje ide u CSS datoteku**.

---

# 1. Zadatak – dodaj kontakt formu na Lego stranicu

1. Uzmite zadatak iz mape `vjezba_14`, te kreirajte novi direktorij vjezba_15 i unutra stavite `index.html` i **novu HTML datoteku** `kontakt.html` u koju ćete smjestiti kontakt formu.
2. U postojećoj datoteci `index.html` dodajte **hipervezu „Kontakt”** (npr. u navigaciji ili u footeru) koja vodi na novu stranicu: `kontakt.html`.
3. U datoteku `kontakt.html`, unutar `<body>` elementa, zalijepite sljedeći HTML kod kontakt forme uz već postojeći kod koji mora biti za prikaz svih elemenata stranice:


```html
        <section class="lego-contact">
            <h2>Kontaktirajte nas – LEGO podrška</h2>
            <p>Ako imate pitanje o svom LEGO setu, ispunite kontakt obrazac u nastavku.</p>
        
            <form class="lego-form" action="#" method="post">
                <div class="form-row">
                    <label for="first-name">Ime *</label>
                    <input type="text" id="first-name" name="first-name" placeholder="Vaše ime..." required>
                </div>
        
                <div class="form-row">
                    <label for="last-name">Prezime *</label>
                    <input type="text" id="last-name" name="last-name" placeholder="Vaše prezime..." required>
                </div>
        
                <div class="form-row">
                    <label for="email">Vaš e-mail *</label>
                    <input type="email" id="email" name="email" placeholder="Vaš e-mail..." required>
                </div>
        
                <div class="form-row">
                    <label for="country">Država</label>
                    <select id="country" name="country">
                        <option value="hrvatska">Hrvatska</option>
                        <option value="slovenija">Slovenija</option>
                        <option value="drugo">Drugo</option>
                    </select>
                </div>
        
                <div class="form-row">
                    <label for="subject">Poruka</label>
                    <textarea id="subject" name="subject" rows="5" placeholder="Napišite svoju poruku..."></textarea>
                </div>
        
                <div class="form-row">
                    <p><strong>Newsletter</strong></p>
                    <div class="option">
                        <input type="checkbox" id="newsletter" name="newsletter">
                        <label for="newsletter">Želim primati LEGO novosti i popuste</label>
                    </div>
                </div>
        
                <div class="form-row">
                    <p><strong>Način dostave</strong></p>
                    <div class="option">
                        <input type="radio" id="delivery-standard" name="delivery" value="standardna" checked>
                        <label for="delivery-standard">Standardna dostava</label>
                    </div>
                    <div class="option">
                        <input type="radio" id="delivery-express" name="delivery" value="ekspresna">
                        <label for="delivery-express">Ekspresna dostava</label>
                    </div>
                </div>
        
                <div class="form-row">
                    <label for="promo-code">Promo kod (onemogućeno polje)</label>
                    <input type="text" id="promo-code" name="promo-code" value="USKORO" disabled>
                </div>
        
                <div class="form-row">
                    <button type="submit" class="btn-send">Pošalji</button>
                </div>
            </form>
        </section>
```

**Napomena:** Studenti ovaj HTML samo prepisuju (ili kopiraju).

# 2. Zadatak – stiliziranje forme pomoću pseudo klasa
U pripadajućoj CSS datoteci (npr. style.css):

Osnovni izgled forme

Stilizirajte .lego-contact tako da se vizualno izdvoji od ostatka stranice
(margine, padding, pozadinska boja po želji).

Elementi .lego-form .form-row neka imaju razmak između redaka.

Label i polja (input, select, textarea) uskladite tako da je forma čitljiva i uredna.

Pseudo klasa :focus

Napišite pravilo koje zahvaća sva tekstualna polja, e-mail, select i textarea
unutar forme kada su u fokusu:

```css
/* primjer selektora – vi ga možete proširiti po potrebi */
.lego-form input:focus,
.lego-form select:focus,
.lego-form textarea:focus {
    /* vaša deklaracija */
}
```
Promijenite boju ruba i pozadinu aktivnog polja; maknite defaultni outline preglednika.

Pseudo klasa :checked (checkbox i radio)

Napišite pravilo koje će za označene checkbox i radio tipke promijeniti stil pripadajuće labele:

```css
.lego-form .form-check-input:checked + label { ... } 
```

```css
.lego-form input[type="checkbox"]:checked + label,
.lego-form input[type="radio"]:checked + label {
    /* npr. bold + zelena boja */
}
```
Kada se označi newsletter ili promijeni tip dostave, neka se labela uz taj odabir istakne
(npr. bold + zelena boja).

Pseudo klase :disabled i :enabled

Stilizirajte polje #promo-code koje je onemogućeno (disabled):

```css
.lego-form input:disabled {
    /* siva pozadina, drugačija boja teksta,  cursor: not-allowed; */
}
```
Napišite i pravilo za :enabled kako biste razlikovali aktivna polja:

```css
.lego-form input:enabled,
.lego-form select:enabled,
.lego-form textarea:enabled {
    /* normalna bijela pozadina itd. */
}
```

Dodajte pseudo klasu :hover na gumb .btn-send da se gumb malo promijeni kad prijeđemo mišem.

Po želji, iskoristite i attribute selektore
(npr. .lego-form input[type="email"] ili .lego-form input[required]).

# 3. Pomoć sa deklaracijom

U CSS-u sami odaberite ispravne selektore, a ove deklaracije iskoristite po potrebi kako biste postigli željeni vizualni efekt.

```css
/* Osnovni izgled polja u formi */
width: 100%;
box-sizing: border-box;
padding: 0.6rem 0.75rem;
border: 1px solid #cccccc;
border-radius: 4px;
font: inherit;

/* Fokusirano polje (:focus) */
border-color: #007bff;
background-color: #eef6ff;
outline: none;
box-shadow: 0 0 0 2px rgba(0, 123, 255, 0.25);

/* Označeni checkbox / radio (:checked na labelu) */
font-weight: 700;
color: #1a7f1a;

/* Onemogućeno polje (:disabled) */
background-color: #eeeeee;
color: #666666;
cursor: not-allowed;

/* Omogućena polja (:enabled) */
background-color: #ffffff;

/* Gumb za slanje */
display: inline-block;
padding: 0.6rem 1.5rem;
border: none;
border-radius: 4px;
background-color: #28a745;
color: #ffffff;
font-weight: 600;
cursor: pointer;

/* Gumb na :hover (bonus) */
background-color: #218838;
```

# 4. Predaja zadatka
Provjerite da se forma ispravno prikazuje u pregledniku.

**Testirajte:**

klik u svako polje (provjerite :focus),

označavanje checkboxa i radio tipki (:checked),

izgled onemogućenog polja Promo code (:disabled).

Pushajte promjene na svoj GitHub repozitorij CSS_2 u mapu vjezba_15.

