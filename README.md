# Specifikacija zahtev za informacijski sistem programa lojalnosti Maestro

## 1. Kratek opis sistema

Informacijski sistem programa lojalnosti Maestro je namenjen podpori programu zvestobe za stranke trgovske verige Maestro. Glavni namen sistema je povečati zvestobo strank, spodbuditi pogostejše in vrednostno višje nakupe ter omogočiti učinkovito upravljanje članstva, točk zvestobe, statusov in nagrad.

Sistem mora omogočati včlanitev novih članov, spremljanje njihovih nakupov, samodejni izračun točk zvestobe, določanje statusa posameznega člana glede na poslovna pravila ter koriščenje zbranih točk. Poleg tega mora sistem članom omogočati pregled nad njihovim računom, administratorjem pa nadzor nad pravilnim delovanjem programa.

Rešitev bo sestavljena iz:
- spletnega portala za člane programa lojalnosti,
- administrativnega portala za zaposlene oziroma skrbnike,
- povezave z obstoječim poslovnim informacijskim sistemom za prevzem podatkov o nakupih,
- podatkovne baze Oracle za shranjevanje vseh ključnih podatkov.

Sistem mora biti zasnovan tako, da bo podpiral najmanj 500.000 članov in omogočal nadaljnjo širitev na tuje trge. Podpirati mora najmanj slovenski in angleški jezik.

---

## 2. Funkcionalne zahteve

### 2.1 Upravljanje članstva

**FZ-1** Sistem mora omogočati spletno registracijo novega člana v program lojalnosti.

**FZ-2** Ob registraciji mora uporabnik vnesti vse obvezne osebne podatke, ki jih določa podjetje za vključitev v program lojalnosti.

**FZ-3** Sistem mora pri registraciji obvezno zahtevati elektronski naslov uporabnika.

**FZ-4** Sistem ne sme dovoliti registracije z elektronskim naslovom, ki je že povezan z obstoječim uporabniškim računom.

**FZ-5** Sistem mora pred dokončno aktivacijo računa preveriti veljavnost in lastništvo elektronskega naslova.

**FZ-6** Sistem mora po uspešni registraciji samodejno ustvariti uporabniški račun in članu dodeliti začetni status **osnovni**.

**FZ-7** Sistem mora ob uspešni registraciji ustvariti enolično identifikacijo člana.

**FZ-8** Sistem mora omogočati evidentiranje izdaje kartice lojalnosti.

**FZ-9** Sistem mora omogočati pripravo podatkov za pošiljanje kartice lojalnosti po navadni pošti.

**FZ-10** Sistem mora preprečiti ustvarjanje podvojenih članov, kadar se ujemajo ključni identifikacijski podatki, določeni v poslovnih pravilih.

---

### 2.2 Prijava in dostop do portala

**FZ-11** Sistem mora registriranemu uporabniku omogočiti prijavo v spletni portal z veljavnim uporabniškim računom.

**FZ-12** Sistem mora ob prijavi preveriti pravilnost uporabniškega imena oziroma elektronskega naslova in gesla.

**FZ-13** Sistem ne sme dovoliti prijave uporabniku, katerega račun ni aktiviran.

**FZ-14** Sistem mora uporabniku omogočiti varno obnovo gesla.

**FZ-15** Sistem mora ob spremembi gesla zahtevati ustrezno preverjanje identitete uporabnika.

**FZ-16** Sistem mora uporabniku omogočati pregled in urejanje osnovnih podatkov njegovega računa.

**FZ-17** Sistem mora beležiti prijave in pomembne varnostne dogodke, povezane z uporabniškim računom.

---

### 2.3 Pregled podatkov člana

**FZ-18** Član mora imeti v portalu vpogled v trenutno stanje svojih točk zvestobe.

**FZ-19** Sistem mora prikazovati samo veljavno in trenutno stanje razpoložljivih točk.

**FZ-20** Član mora imeti vpogled v zgodovino pridobljenih točk.

**FZ-21** Član mora imeti vpogled v zgodovino porabljenih točk.

**FZ-22** Sistem mora za vsako spremembo stanja točk prikazati najmanj datum, vrsto dogodka in spremembo števila točk.

**FZ-23** Član mora imeti vpogled v svoj trenutni status lojalnosti.

**FZ-24** Član mora imeti vpogled v zgodovino sprememb svojega statusa.

**FZ-25** Član mora imeti vpogled v svoje nakupe oziroma skupne zneske nakupov po posameznih obdobjih.

**FZ-26** Sistem mora članu omogočati pregled nagradnega programa in razpoložljivih nagrad.

**FZ-27** Sistem mora pri vsaki nagradi prikazati najmanj naziv nagrade, opis in število potrebnih točk.

---

### 2.4 Koriščenje točk

**FZ-28** Sistem mora članu omogočati koriščenje zbranih točk za izbrane nagrade iz nagradnega programa.

**FZ-29** Pred koriščenjem točk mora sistem preveriti, ali ima član zadostno število razpoložljivih točk.

**FZ-30** Sistem ne sme dovoliti koriščenja točk, če član nima zadostnega števila točk.

**FZ-31** Sistem ne sme dovoliti koriščenja nagrade, ki ni več aktivna ali ni več na voljo.

**FZ-32** Po uspešnem koriščenju mora sistem zmanjšati stanje točk in zabeležiti transakcijo koriščenja.

**FZ-33** Sistem mora za vsako koriščenje zabeležiti najmanj datum, člana, izbrano nagrado in število porabljenih točk.

**FZ-34** Sistem mora članu po uspešnem koriščenju prikazati potrditev izvedene transakcije.

---

### 2.5 Izračun točk zvestobe

**FZ-35** Sistem mora enkrat mesečno izvesti obračun točk za pretekli mesec.

**FZ-36** Sistem mora podatke o nakupih prevzeti iz obstoječega poslovnega informacijskega sistema.

**FZ-37** Sistem mora pred izvedbo obračuna preveriti, ali so bili prevzeti vsi potrebni podatki za izračun.

**FZ-38** Sistem mora obračun točk izvesti na podlagi mesečnega zneska nakupov posameznega člana.

**FZ-39** Sistem mora pri obračunu upoštevati trenutni status člana, ki velja v trenutku obračuna.

**FZ-40** Sistem mora podpirati pravila točkovanja za naslednje razrede mesečne porabe:
- do 200 EUR,
- od 200 EUR do 1000 EUR,
- nad 1000 EUR.

**FZ-41** Sistem mora število dodeljenih točk določiti glede na status člana: **osnovni**, **bronasti**, **srebrni** ali **zlati**.

**FZ-42** Sistem mora omogočati spremembo pravil točkovanja brez posega v programsko kodo.

**FZ-43** Sistem mora po zaključku obračuna shraniti rezultat obračuna in novo stanje točk.

**FZ-44** Sistem mora omogočati ponovno izvedbo obračuna v primeru napake ali popravka vhodnih podatkov, pri čemer mora biti zagotovljena sledljivost sprememb.

---

### 2.6 Upravljanje statusov lojalnosti

**FZ-45** Sistem mora podpirati naslednje statuse članov:
- osnovni,
- bronasti,
- srebrni,
- zlati.

**FZ-46** Sistem mora omogočati možnost kasnejšega dodajanja novih statusov.

**FZ-47** Ob včlanitvi mora biti vsakemu novemu članu dodeljen status **osnovni**.

**FZ-48** Sistem mora pred mesečno dodelitvijo točk obvezno preveriti pogoje za spremembo statusa člana.

**FZ-49** Sistem mora pri spremembi statusa upoštevati poslovna pravila programa lojalnosti.

**FZ-50** Sistem mora pri napredovanju ali nazadovanju statusa zabeležiti datum spremembe, prejšnji status in novi status.

**FZ-51** Sistem mora upoštevati naslednja pravila za spremembo statusa:
- ob prvem presežku nad 499 EUR mesečnih nakupov član pridobi status **srebrni**,
- po še dveh presežkih nad 500 EUR član napreduje v status **zlati**,
- za ohranitev srebrnega statusa mora član v posameznem mesecu opraviti vsaj 200 EUR nakupov,
- za ohranitev zlatega statusa mora član v posameznem mesecu opraviti vsaj 500 EUR nakupov,
- če član ne izpolni pogojev za zlati status, preide v status **srebrni**,
- če član dva meseca zapored ne izpolni pogojev za srebrni status, preide v status **bronasti**,
- član iz bronastega statusa lahko napreduje po dveh zaporednih mesecih z nakupi v vrednosti najmanj 200 EUR,
- član iz bronastega statusa lahko preide v osnovni status, če opravi nakup v vrednosti manj kot 50 EUR.

**FZ-52** Sistem mora omogočati spreminjanje mejnih vrednosti in pravil prehodov med statusi preko administrativnega vmesnika.

---

### 2.7 Administrativne funkcije

**FZ-53** Administrativni portal mora omogočati pregled statusov članov za izbrano časovno obdobje.

**FZ-54** Administrativni portal mora omogočati pregled statistike nakupov.

**FZ-55** Administrativni portal mora omogočati upravljanje nagradnega programa.

**FZ-56** Administrativni portal mora omogočati dodajanje, spreminjanje in deaktivacijo nagrad.

**FZ-57** Administrativni portal mora omogočati upravljanje pravil točkovanja.

**FZ-58** Administrativni portal mora omogočati upravljanje pravil za prehode med statusi.

**FZ-59** Administrativni portal mora omogočati izvajanje poizvedb nad podatkovno bazo v skladu s pravicami uporabnika.

**FZ-60** Sistem mora voditi revizijsko sled vseh pomembnih sprememb, kot so spremembe pravil, statusov, točk in administrativnih posegov.

**FZ-61** Sistem mora za vsako administrativno spremembo zabeležiti najmanj uporabnika, datum, vrsto spremembe in staro ter novo vrednost, kadar je to smiselno.

---

## 3. Tehnične zahteve

### 3.1 Arhitektura sistema

**TZ-1** Sistem mora biti zasnovan kot večslojna spletna aplikacija.

**TZ-2** Arhitektura mora ločevati uporabniški vmesnik, poslovno logiko, integracijski sloj in podatkovno bazo.

**TZ-3** Sistem mora biti zasnovan modularno, tako da omogoča nadgradnjo posameznih delov brez večjih posegov v celotno rešitev.

---

### 3.2 Zmogljivost in razširljivost

**TZ-4** Sistem mora podpirati najmanj 500.000 članov.

**TZ-5** Sistem mora omogočati učinkovito delovanje tudi pri večjem številu sočasnih uporabnikov.

**TZ-6** Sistem mora biti zasnovan tako, da omogoča razširitev na tuje trge.

**TZ-7** Mesečni obračun točk mora biti izveden kot ločen proces, ki ne sme bistveno motiti normalnega delovanja sistema.

**TZ-8** Sistem mora omogočati povečanje zmogljivosti brez spremembe osnovne poslovne logike.

---

### 3.3 Podatkovna baza

**TZ-9** Sistem mora uporabljati podatkovno bazo Oracle.

**TZ-10** Podatkovna baza mora hraniti vse ključne podatke, povezane s člani, uporabniškimi računi, nakupi, točkami, statusi, nagradami, pravili in revizijskimi zapisi.

**TZ-11** Podatkovni model mora zagotavljati enoličnost ključnih poslovnih entitet.

**TZ-12** Podatkovni model mora biti zasnovan tako, da omogoča enostavno nadgradnjo in vzdrževanje sistema.

**TZ-13** Sistem mora zagotavljati varnostne kopije podatkovne baze in možnost obnove podatkov.

---

### 3.4 Varnost

**TZ-14** Vsa komunikacija med uporabnikom in sistemom mora potekati po varnem komunikacijskem kanalu.

**TZ-15** Gesla uporabnikov se ne smejo hraniti v nešifrirani obliki.

**TZ-16** Sistem mora zagotavljati varno prijavo, varno obnovo gesla in zaščito pred nepooblaščenim dostopom.

**TZ-17** Sistem mora omogočati upravljanje uporabniških vlog in pravic dostopa.

**TZ-18** Administrativni del sistema mora biti dostopen samo pooblaščenim uporabnikom.

**TZ-19** Sistem mora beležiti varnostno pomembne dogodke.

**TZ-20** Sistem mora preprečevati nepooblaščene spremembe poslovnih pravil in podatkov članov.

---

### 3.5 Večjezičnost in uporabnost

**TZ-21** Sistem mora podpirati najmanj slovenski in angleški jezik.

**TZ-22** Uporabniški vmesnik mora biti pregleden, razumljiv in enostaven za uporabo.

**TZ-23** Sistem mora zagotavljati enotno uporabniško izkušnjo v vseh ključnih delih portala.

**TZ-24** Administrativni vmesnik mora omogočati učinkovito in pregledno delo zaposlenih.

---

### 3.6 Vzdrževanje in konfigurabilnost

**TZ-25** Pravila točkovanja in prehodi med statusi morajo biti nastavljivi brez spremembe izvorne kode.

**TZ-26** Sistem mora omogočati beleženje napak in spremljanje delovanja sistema.

**TZ-27** Sistem mora omogočati osnovni operativni nadzor nad ključnimi procesi.

**TZ-28** Sistem mora omogočati obnovo delovanja po napaki ali izpadu.

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
| Bronasti status | Nižji status v programu lojalnosti. |
| Srebrni status | Višji status, dosežen ob izpolnjevanju določenih pogojev. |
| Zlati status | Najvišji status v programu lojalnosti. |
| Obračun točk | Proces izračuna in dodelitve točk za določeno obdobje. |
| Poslovni informacijski sistem | Obstoječi sistem podjetja, iz katerega se prevzemajo podatki o nakupih. |
| Nagradni program | Seznam nagrad ali ugodnosti, ki jih član lahko koristi s točkami. |
| Administrativni portal | Del sistema, namenjen zaposlenim in skrbnikom. |
| Pravila točkovanja | Pravila, ki določajo, koliko točk član prejme glede na svoje nakupe in status. |
| Pravila prehoda statusov | Pravila, ki določajo napredovanje ali nazadovanje med statusi. |
| Oracle | Sistem za upravljanje podatkovne baze, uporabljen v rešitvi. |
| Revizijska sled | Evidenca pomembnih sprememb in dejanj v sistemu. |

---

## 6. Opombe in predpostavke

- Sistem mora biti zasnovan dovolj prilagodljivo, da bo omogočal prihodnje spremembe pravil programa lojalnosti.
- Poslovna pravila za točkovanje in statuse ne smejo biti fiksno zapisana v programski kodi, temveč morajo biti nastavljiva preko administrativnega dela sistema.
- Pri načrtovanju sistema je treba upoštevati možnost dolgoročne rasti števila uporabnikov in funkcionalnosti.
- Posebno pozornost je treba nameniti varnosti uporabniških podatkov in zanesljivosti delovanja sistema.
