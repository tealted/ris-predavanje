# Specifikacija zahtev za informacijski sistem programa lojalnosti Maestro

## 1. Kratek opis sistema

Informacijski sistem programa lojalnosti Maestro je namenjen podpori programu zvestobe za stranke trgovske verige Maestro. Njegov namen je omogočiti upravljanje članstva, spremljanje nakupov, izračun točk zvestobe, določanje statusov članov ter koriščenje nagrad.

Sistem uporabljata dve glavni skupini uporabnikov:

- **člani programa lojalnosti**, ki preko uporabniškega portala spremljajo svoje točke, statuse in nagrade,
- **administratorji oziroma pooblaščeni zaposleni**, ki preko administrativnega portala upravljajo pravila programa, nagrade in pregledujejo podatke o delovanju sistema.

Rešitev vključuje:

- uporabniški spletni portal,
- administrativni portal,
- povezavo z obstoječim poslovnim informacijskim sistemom za pridobivanje podatkov o nakupih,
- podatkovno bazo Oracle za hrambo podatkov.

Sistem mora biti zasnovan tako, da podpira veliko število uporabnikov, najmanj 500.000 članov, ter omogoča nadaljnjo širitev in podporo več jezikom.

---

## 2. Funkcionalne zahteve

Funkcionalne zahteve opisujejo, kaj mora sistem omogočati.

### 2.1 Upravljanje članstva

**FZ-1** Sistem mora omogočati spletno registracijo novega člana v program lojalnosti.

**FZ-2** Ob registraciji mora uporabnik vnesti zahtevane osebne podatke, vključno z elektronskim naslovom.

**FZ-3** Sistem mora preveriti, ali elektronski naslov še ni uporabljen pri drugem računu.

**FZ-4** Sistem mora pred aktivacijo računa preveriti veljavnost elektronskega naslova.

**FZ-5** Po uspešni registraciji mora sistem ustvariti uporabniški račun, članu dodeliti enolično identifikacijo in začetni status **osnovni**.

**FZ-6** Sistem mora omogočati evidenco izdaje kartice lojalnosti in pripravo podatkov za njeno pošiljanje.

---

### 2.2 Prijava in uporabniški račun

**FZ-7** Sistem mora registriranemu uporabniku omogočiti prijavo v uporabniški portal.

**FZ-8** Sistem mora ob prijavi preveriti pravilnost prijavnih podatkov.

**FZ-9** Sistem ne sme dovoliti prijave neaktiviranemu uporabniškemu računu.

**FZ-10** Sistem mora omogočati varen postopek obnove gesla.

**FZ-11** Sistem mora uporabniku omogočati pregled in urejanje osnovnih podatkov računa.

---

### 2.3 Pregled podatkov člana

**FZ-12** Član mora imeti vpogled v trenutno stanje svojih točk zvestobe.

**FZ-13** Član mora imeti vpogled v zgodovino pridobljenih in porabljenih točk.

**FZ-14** Član mora imeti vpogled v svoj trenutni status lojalnosti in zgodovino sprememb statusa.

**FZ-15** Član mora imeti vpogled v svoje nakupe oziroma skupne zneske nakupov po posameznih obdobjih.

**FZ-16** Član mora imeti vpogled v aktualni nagradni program.

---

### 2.4 Koriščenje točk

**FZ-17** Sistem mora članu omogočati koriščenje točk za nagrade iz aktivnega nagradnega programa.

**FZ-18** Pred koriščenjem mora sistem preveriti, ali ima član zadostno število razpoložljivih točk.

**FZ-19** Sistem ne sme dovoliti koriščenja, če član nima dovolj točk ali nagrada ni več na voljo.

**FZ-20** Po uspešnem koriščenju mora sistem zmanjšati stanje točk, zabeležiti transakcijo in uporabniku prikazati potrditev.

---

### 2.5 Obračun točk

**FZ-21** Sistem mora enkrat mesečno izvesti obračun točk za pretekli mesec.

**FZ-22** Sistem mora pri obračunu uporabiti podatke o nakupih iz obstoječega poslovnega informacijskega sistema.

**FZ-23** Sistem mora točke obračunati na podlagi mesečnega zneska nakupov in statusa člana.

**FZ-24** Sistem mora podpirati pravila točkovanja za naslednje razrede porabe:
- do 200 EUR,
- od 200 EUR do 1000 EUR,
- nad 1000 EUR.

**FZ-25** Sistem mora po zaključku obračuna shraniti rezultat obračuna in novo stanje točk.

**FZ-26** Pravila točkovanja morajo biti nastavljiva preko administrativnega vmesnika.

---

### 2.6 Upravljanje statusov lojalnosti

**FZ-27** Sistem mora podpirati statuse **osnovni**, **bronasti**, **srebrni** in **zlati**.

**FZ-28** Ob registraciji mora član prejeti status **osnovni**.

**FZ-29** Sistem mora pred mesečno dodelitvijo točk preveriti pogoje za spremembo statusa.

**FZ-30** Sistem mora pri spremembi statusa upoštevati poslovna pravila programa lojalnosti.

**FZ-31** Sistem mora zabeležiti vsako spremembo statusa skupaj z datumom, prejšnjim in novim statusom.

**FZ-32** Pravila za prehode med statusi morajo biti nastavljiva preko administrativnega vmesnika.

---

### 2.7 Administrativne funkcije

**FZ-33** Administrativni portal mora omogočati pregled statusov članov za izbrano obdobje.

**FZ-34** Administrativni portal mora omogočati pregled statistike nakupov.

**FZ-35** Administrativni portal mora omogočati upravljanje nagradnega programa.

**FZ-36** Administrativni portal mora omogočati upravljanje pravil točkovanja in pravil za prehode med statusi.

**FZ-37** Administrativni portal mora omogočati izvajanje poizvedb nad podatkovno bazo glede na pravice uporabnika.

**FZ-38** Sistem mora voditi revizijsko sled pomembnih administrativnih in poslovnih sprememb.

---

## 3. Nefunkcionalne zahteve

Nefunkcionalne zahteve opisujejo, kako mora sistem delovati.

### 3.1 Arhitektura in vzdrževanje

**NFZ-1** Sistem mora biti zasnovan kot večslojna spletna aplikacija.

**NFZ-2** Arhitektura mora ločevati uporabniški vmesnik, poslovno logiko, integracije in podatkovni sloj.

**NFZ-3** Sistem mora biti zasnovan modularno, tako da omogoča enostavno nadgradnjo in vzdrževanje.

**NFZ-4** Poslovna pravila za točkovanje in prehode med statusi ne smejo biti trdo vgrajena v programsko kodo.

---

### 3.2 Zmogljivost in razširljivost

**NFZ-5** Sistem mora podpirati najmanj 500.000 članov.

**NFZ-6** Sistem mora zagotavljati stabilno delovanje tudi pri večjem številu sočasnih uporabnikov.

**NFZ-7** Sistem mora omogočati širitev na nove trge in dodatne jezikovne različice.

**NFZ-8** Mesečni obračun točk mora biti izveden kot ločen proces, ki ne sme bistveno vplivati na delovanje uporabniškega portala.

---

### 3.3 Varnost

**NFZ-9** Vsa komunikacija med odjemalcem in strežnikom mora potekati po varnem komunikacijskem kanalu.

**NFZ-10** Gesla uporabnikov se ne smejo hraniti v čitljivi obliki.

**NFZ-11** Sistem mora omogočati upravljanje uporabniških vlog in pravic dostopa.

**NFZ-12** Administrativni del sistema mora biti dostopen samo pooblaščenim uporabnikom.

**NFZ-13** Sistem mora beležiti varnostno pomembne dogodke.

---

### 3.4 Podatki in zanesljivost

**NFZ-14** Sistem mora uporabljati podatkovno bazo Oracle.

**NFZ-15** Sistem mora zagotavljati integriteto podatkov pri zapisovanju, spreminjanju in brisanju.

**NFZ-16** Sistem mora omogočati varnostno kopiranje podatkov in obnovo ob napakah ali izpadih.

**NFZ-17** Revizijski podatki morajo omogočati sledljivost poslovnih in administrativnih sprememb.

---

### 3.5 Uporabnost

**NFZ-18** Sistem mora podpirati najmanj slovenski in angleški jezik.

**NFZ-19** Uporabniški vmesnik mora biti pregleden, razumljiv in enostaven za uporabo.

**NFZ-20** Administrativni portal mora omogočati učinkovito in pregledno delo zaposlenih.

**NFZ-21** Uporabniški vmesniki morajo biti konsistentni glede navigacije, poimenovanja in prikaza podatkov.

---

## 4. Vmesniki

### 4.1 Uporabniški vmesnik za člane

Uporabniški portal mora članom omogočati:

- registracijo v program lojalnosti,
- prijavo v sistem,
- pregled trenutnega stanja točk,
- pregled zgodovine točk,
- pregled trenutnega statusa,
- pregled zgodovine statusov,
- pregled nakupov,
- pregled nagradnega programa,
- koriščenje točk,
- upravljanje osnovnih podatkov računa.

---

### 4.2 Administrativni vmesnik

Administrativni portal mora omogočati:

- pregled statusov članov po časovnih obdobjih,
- pregled statistike nakupov,
- upravljanje nagradnega programa,
- upravljanje pravil točkovanja,
- upravljanje pravil za spremembo statusov,
- izvajanje poizvedb nad podatkovno bazo v skladu s pravicami uporabnika.

---

### 4.3 Integracijski vmesniki

**VI-1** Sistem mora omogočati povezavo z obstoječim poslovnim informacijskim sistemom za prevzem podatkov o nakupih.

**VI-2** Sistem mora omogočati povezavo z e-poštnim sistemom za pošiljanje aktivacijskih sporočil in drugih obvestil.

**VI-3** Sistem mora omogočati povezavo s sistemom za pripravo oziroma evidenco pošiljanja fizičnih kartic lojalnosti.

**VI-4** Sistem mora po potrebi omogočati izvoz poročil in statistik v standardne formate.

---

## 5. Slovar izrazov

| Izraz | Pomen |
|---|---|
| Program lojalnosti | Program zvestobe, s katerim podjetje nagrajuje stranke za njihove nakupe. |
| Član | Stranka, vključena v program lojalnosti. |
| Kartica lojalnosti | Fizična kartica, ki jo prejme član programa. |
| Uporabniški račun | Digitalni račun člana za dostop do spletnega portala. |
| Točke zvestobe | Enote nagrajevanja, ki jih član prejema glede na nakupe in status. |
| Status lojalnosti | Stopnja članstva v programu lojalnosti. |
| Osnovni status | Začetni status, ki ga član prejme ob registraciji. |
| Bronasti status | Eden izmed statusov programa lojalnosti. |
| Srebrni status | Višji status programa lojalnosti. |
| Zlati status | Najvišji status v trenutno določenem programu lojalnosti. |
| Obračun točk | Proces mesečnega izračuna in dodelitve točk. |
| Poslovni informacijski sistem | Obstoječi sistem podjetja, iz katerega se pridobivajo podatki o nakupih. |
| Nagradni program | Seznam nagrad ali ugodnosti, ki jih član lahko koristi s točkami. |
| Administrativni portal | Del sistema, namenjen zaposlenim in skrbnikom. |
| Pravila točkovanja | Pravila za določitev števila točk glede na nakupe in status. |
| Pravila prehoda statusov | Pravila, ki določajo napredovanje ali nazadovanje med statusi. |
| Revizijska sled | Evidenca sprememb in dejanj v sistemu za namen sledljivosti in nadzora. |

---

## 6. Opombe in predpostavke

- Sistem mora biti zasnovan tako, da omogoča prihodnje spremembe poslovnih pravil brez večjih sprememb v programski kodi.
- Ključne poslovne in administrativne spremembe morajo biti sledljive.
- Pri razvoju je treba posebno pozornost nameniti varnosti podatkov, zanesljivosti delovanja in preglednosti uporabniških vmesnikov.
