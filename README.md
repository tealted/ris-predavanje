# Specifikacija zahtev za informacijski sistem programa lojalnosti Maestro

## 1. Kratek opis sistema

Informacijski sistem programa lojalnosti Maestro je namenjen podpori programu zvestobe za stranke trgovske verige Maestro. Namen sistema je povečati zvestobo strank, spodbuditi večjo vrednost nakupov ter omogočiti pregledno in avtomatizirano upravljanje članstva, statusov, točk zvestobe in nagrad. Sistem mora podpirati registracijo strank, izračun točk zvestobe, samodejno spreminjanje statusov lojalnosti, uporabo točk ter administrativno upravljanje programa.

Sistem bo sestavljen iz:
- spletnega portala za člane programa,
- administrativnega portala za zaposlene oziroma skrbnike,
- povezave z obstoječim poslovnim informacijskim sistemom za prevzem podatkov o nakupih,
- podatkovne baze Oracle za hrambo vseh poslovnih in uporabniških podatkov.

Sistem mora biti zasnovan tako, da podpira vsaj 500.000 uporabnikov in omogoča nadaljnjo širitev na tuje trge. Prav tako mora podpirati slovenski in angleški jezik.

---

## 2. Funkcionalne zahteve

### 2.1 Upravljanje članstva

**FZ-1** Sistem mora omogočati spletno registracijo novega člana v program lojalnosti.

**FZ-2** Ob registraciji mora uporabnik vnesti osebne podatke, vključno z elektronskim naslovom, ki se uporabi za ustvarjanje uporabniškega računa.

**FZ-3** Sistem mora pred dokončno aktivacijo računa preveriti lastništvo elektronskega naslova z verifikacijskim postopkom.

**FZ-4** Ob uspešni registraciji mora sistem ustvariti uporabniški račun in članu dodeliti začetni status **osnovni**.

**FZ-5** Sistem mora omogočati evidenco izdaje kartice lojalnosti in pripravo podatkov za pošiljanje kartice po navadni pošti.

### 2.2 Prijava in dostop do portala

**FZ-6** Sistem mora registriranemu uporabniku omogočiti prijavo v portal z uporabniškim računom.

**FZ-7** Sistem mora omogočati varno obnovo gesla in upravljanje uporabniškega računa.

### 2.3 Pregled podatkov člana

**FZ-8** Član mora v portalu videti trenutno stanje točk zvestobe.

**FZ-9** Član mora imeti vpogled v zgodovino dodeljenih in porabljenih točk.

**FZ-10** Član mora imeti vpogled v svoj trenutni status lojalnosti in zgodovino sprememb statusov.

**FZ-11** Član mora imeti vpogled v zneske svojih nakupov po obdobjih.

**FZ-12** Član mora imeti vpogled v nagradni program, ki je na voljo za koriščenje točk.

### 2.4 Koriščenje točk

**FZ-13** Sistem mora članu omogočiti koriščenje točk za izbrane nagrade iz nagradnega programa.

**FZ-14** Sistem mora ob koriščenju preveriti, ali ima član dovolj razpoložljivih točk.

**FZ-15** Sistem mora po uspešnem koriščenju zmanjšati stanje točk in zabeležiti transakcijo koriščenja.

### 2.5 Izračun točk zvestobe

**FZ-16** Sistem mora enkrat mesečno izvesti obračun točk za pretekli mesec na podlagi zneska opravljenih nakupov, pridobljenih iz poslovnega informacijskega sistema.

**FZ-17** Sistem mora podpirati pravila točkovanja glede na mesečni znesek nakupov in status člana:
- do 200 EUR,
- od 200 EUR do 1000 EUR,
- nad 1000 EUR,

pri čemer se število točk razlikuje glede na status osnovni, bronasti, srebrni ali zlati.

**FZ-18** Sistem mora omogočiti spremembo vrednosti pravil točkovanja brez posega v programsko kodo, preko administrativnega vmesnika.

### 2.6 Upravljanje statusov lojalnosti

**FZ-19** Sistem mora podpirati statuse **osnovni**, **bronasti**, **srebrni** in **zlati**, z možnostjo kasnejše razširitve na dodatne statuse.

**FZ-20** Ob včlanitvi mora biti članu dodeljen status **osnovni**.

**FZ-21** Sistem mora pred dodelitvijo mesečnih točk najprej preveriti pogoje za spremembo statusa in šele nato izračunati ter dodeliti točke.

**FZ-22** Sistem mora pri spremembi statusa upoštevati naslednja pravila:
- prvi presežek nad 499 EUR v preteklem mesecu povzroči status srebrni,
- po še dveh presežkih nad 500 EUR član napreduje v status zlati,
- za ohranitev srebrnega statusa mora mesečni znesek znašati vsaj 200 EUR,
- za ohranitev zlatega statusa mora mesečni znesek znašati vsaj 500 EUR,
- če član ne ohrani zlatega statusa, preide v srebrni status,
- če član dva meseca zapored ne izpolni pogojev za srebrni status, preide v bronasti status,
- iz bronastega statusa lahko preide po dveh zaporednih mesecih z nakupi najmanj 200 EUR ali v osnovni status, če opravi nakup pod 50 EUR.

**FZ-23** Sistem mora omogočiti spremembo mejnih vrednosti in pravil prehodov med statusi preko administrativnega vmesnika.

### 2.7 Administrativne funkcije

**FZ-24** Administrativni portal mora omogočati pregled statusov strank za poljubno obdobje.

**FZ-25** Administrativni portal mora omogočati pregled statistike nakupov.

**FZ-26** Administrativni portal mora omogočati izvajanje poizvedb po podatkovni bazi skladno z dodeljenimi pravicami uporabnika.

**FZ-27** Administrativni portal mora omogočati upravljanje nagradnega programa.

**FZ-28** Administrativni portal mora omogočati upravljanje pravil za točkovanje in prehode med statusi.

**FZ-29** Sistem mora voditi revizijsko sled sprememb pravil, statusov, točk in administrativnih posegov.

---

## 3. Tehnične zahteve

### 3.1 Arhitektura in zmogljivost

**TZ-1** Sistem mora biti zasnovan kot večslojna spletna rešitev z ločenimi plastmi za uporabniški vmesnik, poslovno logiko, integracije in podatkovno bazo.

**TZ-2** Sistem mora podpirati najmanj 500.000 članov in biti pripravljen na rast obsega zaradi širitve izven Slovenije.

**TZ-3** Sistem mora omogočati horizontalno in/ali vertikalno skaliranje aplikacijskega sloja ter visoko razpoložljivost podatkovne baze.

**TZ-4** Mesečni obračun točk mora biti izveden kot ločen paketni proces ali razporejeno opravilo, ki ne sme bistveno motiti delovanja portala.

### 3.2 Podatkovna baza

**TZ-5** Sistem mora uporabljati podatkovno bazo Oracle, ker podjetje že razpolaga z licencami in obstoječo infrastrukturo.

**TZ-6** Podatkovni model mora podpirati:
- člane,
- uporabniške račune,
- statuse lojalnosti,
- nakupne transakcije,
- mesečne obračune,
- transakcije točk,
- nagrade,
- pravila točkovanja,
- pravila prehodov statusov,
- revizijske zapise.

### 3.3 Varnost

**TZ-7** Vsa komunikacija med odjemalcem in strežnikom mora potekati po zaščitenem kanalu TLS.

**TZ-8** Gesla uporabnikov se ne smejo hraniti v čisti obliki, temveč v obliki varnih kriptografskih zgoščenk.

**TZ-9** Sistem mora preprečevati zlorabe pri registraciji, prijavi in obnovi gesla, vključno z omejevanjem poskusov, zaščito pred enumeracijo računov in varnim potrjevanjem identitete.

**TZ-10** Sistem mora imeti vloge in pravice dostopa najmanj za:
- člana programa,
- administratorja programa,
- analitika oziroma pooblaščenega uporabnika za poizvedbe,
- sistemskega skrbnika.

**TZ-11** Za administrativni dostop je priporočljiva večfaktorska avtentikacija.

### 3.4 Večjezičnost in uporabnost

**TZ-12** Sistem mora podpirati najmanj slovenski in angleški jezik.

**TZ-13** Uporabniški vmesnik mora biti intuitiven, pregleden in zasnovan s sodobnimi tehnologijami.

**TZ-14** Uporabniški vmesnik mora biti skladen z osnovnimi načeli dostopnosti po WCAG 2.2, zlasti glede berljivosti, navigacije s tipkovnico, kontrasta, jasnih oznak obrazcev in razumljivosti interakcij.

### 3.5 Vzdrževanje in konfigurabilnost

**TZ-15** Pravila točkovanja in pravila prehodov statusov morajo biti konfigurabilna brez spremembe izvorne kode.

**TZ-16** Sistem mora omogočati beleženje napak, operativni nadzor ter spremljanje ključnih kazalnikov delovanja.

**TZ-17** Sistem mora podpirati varnostne kopije in obnovo podatkov v primeru napake ali izpada.

---

## 4. Vmesniki

### 4.1 Uporabniški vmesnik za člane

Portal za člane mora omogočati:
- registracijo in aktivacijo računa,
- prijavo,
- pregled točk,
- pregled statusa,
- pregled nakupov,
- pregled nagradnega programa,
- koriščenje točk,
- upravljanje osnovnih podatkov uporabniškega računa.

### 4.2 Administrativni vmesnik

Administrativni portal mora omogočati:
- pregled statusov po obdobjih,
- pregled statistike nakupov,
- upravljanje nagradnega programa,
- upravljanje pravil točkovanja in statusov,
- izvajanje poizvedb nad podatkovno bazo glede na pravice uporabnika.

### 4.3 Integracijski vmesniki

**VI-1** Sistem mora imeti integracijski vmesnik do poslovnega informacijskega sistema za uvoz podatkov o nakupih.

**VI-2** Sistem mora imeti integracijski vmesnik do e-poštnega sistema za pošiljanje aktivacijskih in sistemskih obvestil.

**VI-3** Sistem mora imeti vmesnik do sistema za pripravo oziroma evidenco pošiljanja fizičnih kartic članom.

**VI-4** Po potrebi mora sistem omogočati izvoz poročil in statistik za poslovne uporabnike v standardne formate.

---

## 5. Slovar izrazov

| Izraz | Pomen |
|---|---|
| Program lojalnosti | Program zvestobe, s katerim trgovska veriga nagrajuje stranke za nakupe. |
| Član | Stranka, ki je vključena v program lojalnosti. |
| Kartica lojalnosti | Fizična kartica, izdana članu programa za identifikacijo v programu. |
| Uporabniški račun | Digitalni račun člana za prijavo v spletni portal. |
| Točke zvestobe | Enote nagrajevanja, ki jih član pridobi glede na vrednost nakupov in status. |
| Status lojalnosti | Stopnja članstva v programu: osnovni, bronasti, srebrni, zlati. |
| Osnovni status | Začetni status člana ob včlanitvi. |
| Bronasti status | Status člana, ki ga sistem dodeli ob neizpolnjevanju pogojev za višje statuse. |
| Srebrni status | Višji status, dosežen po določenih pravilih nakupov. |
| Zlati status | Najvišji predvideni status v obstoječi zasnovi programa. |
| Obračun točk | Periodični proces izračuna in dodelitve točk za preteklo obdobje. |
| Poslovni IS | Obstoječi poslovni informacijski sistem trgovske verige, iz katerega se pridobijo podatki o nakupih. |
| Nagradni program | Seznam nagrad ali ugodnosti, ki jih član lahko koristi s točkami. |
| Administrativni portal | Del sistema za zaposlene oziroma skrbnike za upravljanje programa. |
| Pravila točkovanja | Poslovna pravila, ki določajo število dodeljenih točk glede na znesek nakupov in status. |
| Pravila prehoda statusov | Poslovna pravila, ki določajo napredovanje ali nazadovanje med statusi. |
| Oracle | Sistem za upravljanje podatkovne baze, predviden za uporabo v rešitvi. |
| TLS | Protokol za zaščiten prenos podatkov med uporabnikom in strežnikom. |
| MFA | Večfaktorska avtentikacija za dodatno zaščito uporabniških računov. |
| WCAG | Smernice za dostopnost spletnih vsebin in aplikacij. |
| Revizijska sled | Evidenca sprememb in dejanj v sistemu za nadzor in sledljivost. |

---

## 6. Opombe in predpostavke

- Nabor statusov se lahko v prihodnje spremeni, zato mora biti seznam statusov konfigurabilen in ne trdo vgrajen v kodo.
- Pravila točkovanja in prehodov med statusi morajo biti nastavljiva preko administrativnega vmesnika.
- Zaradi zahtevane velikosti sistema in načrtovane širitve izven Slovenije je priporočena arhitektura, ki podpira visoko razpoložljivost, skaliranje in obnovljivost sistema.
