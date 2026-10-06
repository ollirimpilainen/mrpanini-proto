# Mr. Panini – Jälleenmyyjäksi-sivun prototyyppi

Klikattava HTML-prototyyppi uudistetusta sivusta https://mrpanini.fi/jalleenmyyjaksi/. Avaa `index.html` suoraan selaimessa. Prototyyppi ei vaadi build-vaihetta, ja CSS ja JS ovat inline.

## Mitä tehtiin

- Sisältö on edelleen yhdellä sivulla, mutta se on jaettu kolmeen myyntitapaan: **Tarjoilu myyntipisteessä**, **Lämmitettävät pitat** ja **Kaupan hyllyyn**. Jokaisella on sama runko: sopii sinulle, jos… / mitä tarvitset / näin valmistat tai myyt / kuva / oma CTA.
- Yhteiset asiat (hyödyt, tilaus ja toimitus, markkinointimateriaalit) näytetään vain kerran, eikä niitä toisteta segmenteissä.
- Hajallaan olleet sähköpostiosoitteet on korvattu yhdellä yhteydenottolomakkeella. Asiakaspalvelun sähköposti ja puhelin näkyvät lomakkeen vieressä.
- Toiminnallisuus (briefin sticky-ankkurinavi poistettiin jälkikäteen erillisestä pyynnöstä):
  - Smooth scroll ja `scroll-margin-top`.
  - Segmentin CTA esivalitsee myyntipisteen tyypin lomakkeeseen (`data-segment` tai URL `#yhteydenotto?segmentti=tarjoilu|pitat|kauppa`). Myös suora linkki tällä hashilla toimii.
  - "Kysy parilan hintaa" esivalitsee tarjoilun ja esitäyttää viestin.
  - Materiaalikortteja voi suodattaa (kaikki / myyntipiste / kauppa).
  - Lomakkeessa on validointi ja kiitosviesti. Mitään ei lähetetä.
  - Yläpalkin napilla voi piilottaa ⚠-merkinnät, kun prototyyppiä esitellään "puhtaana".
- Sivu on tarkistettu Playwrightilla leveyksillä 1440, 390 ja 360 px: vaakaylivuotoa ei ole eikä JS-virheitä, ja hash-esivalinta ja lomake toimivat. Kuvakaappaukset ovat kansiossa `screenshots/`.

## Tokenit ja fontit

Värit ja mitat ovat briefin tokenit sellaisenaan (`--mp-yellow`, `--mp-light-yellow`, `--mp-cream`, `--mp-maroon`, `--mp-red`, `--mp-espresso` …, `--content-width`, `--wide-width`). Lisäksi käytin kolmea apumuuttujaa: `--gutter`, `--section-y` ja `--subnav-h`.

| Käyttö | Fontti | Fallback |
|---|---|---|
| H1–H2 | Monaz (teeman polusta) | Arial Rounded MT Bold, Trebuchet MS, cursive |
| Napit, eyebrow, navi | Gelica (teeman polusta) | Georgia, serif |
| Leipäteksti, H3–H6 | Poppins 500/600/700 (Google Fonts) | system-ui |

Monaz ja Gelica latautuvat teeman palvelimelta (CORS sallittu), joten vaihtofonttia ei tarvittu. Niitä käytetään vain sisäisessä esittelyssä. Teemassa on Gelicasta vain regular-leikkaus, joten napeissa ja eyebrow'ssa selain lihavoi fontin itse samalla tavalla kuin nykyisellä sivustolla.

Kontrasti: keltaisissa napeissa teksti on aina espresso. Big numbers -osion keltaisella pohjalla eyebrow on maroon eikä punainen, koska punainen keltaisella ei läpäise AA-vaatimusta.

## ⚠-kohdat (vahvistettava asiakkaalta)

1. **Pitat, kenelle sopii.** Nykyisellä sivulla tätä ei ole. Prototyypissä on ehdotus: myyntipisteet, joissa on airfryer mutta ei parilaa.
2. **Pitat, tilantarve ja esillepano.** Onko pitoille omia materiaaleja?
3. **Pitat, tarjoilutapa.** Onko tarjoilupussi tai muu tapa?
4. **Pitat, ingressi.** Osio on ohut. Nyt mukana on vain "helppo ja nopea lämmitys airfryerissa" ja paistoaika.
5. **Kaupan hylly, säilytysvaatimus.** Tarvitaanko kylmähylly?
6. **Kaupan hylly, kuva.** Hyllytarjottimesta tai myymälästä ei ole kuvaa. Käytössä on etusivun pakkauskuva (`mr.-panini-fiiliskuva-pakkaukset-suuri`).
7. **Hinta ja kate.** Koko osio on paikkamerkki (X € / Y €). Se on suositeltu lisäys.
8. **Lomakkeen vastaanottaja** ja tietosuojateksti.

## Poikkeamat briefistä ja tulkinnat

- **Muotoilin copya ilman uusia faktoja.** Esimerkiksi "Sopii sinulle, jos…" tarjoilulle ja kaupalle on kirjoitettu briefin segmenttikuvauksista (kahvilat, huoltoasemat, kioskit; vähittäiskaupat ja myymälät).
- **"4 min paistoaika parilassa"** big numbersissa tulee nykyisen sivun lauseesta "pariloida niitä 4 minuuttia". Segmenttiosiossa käytetään tarkempaa muotoa "3–4 minuutissa parilasta riippuen".
- **Parilan hinta:** briefin "Hintatiedot: ota yhteyttä" näkyy muodossa "Kysy tarjous", ja siihen liittyy nappi, joka vie lomakkeeseen.
- **Myyntiedustajan nimi ja sähköposti** (markkinointi- ja myyntiedustaja nykyisellä sivulla) jätettiin pois, koska briefissä lomakkeen viereen pyydettiin vain asiakaspalvelu. Materiaaleja ohjataan tilaamaan lomakkeella, asiakaspalvelusta tai alueen vähittäiskaupan edustajalta.
- **Materiaalikorttien lyhyet kuvaukset** lattiatarroille ja hyllyvipoille ("Tehostavat tuotteiden näkyvyyttä") on johdettu nykyisestä lauseesta "näkyvyyttä voidaan tehostaa lattiatarroilla ja hyllyvipoilla".
- **Lisäsin prototyyppipalkin** sivun yläreunaan. Se ei kuulu lopulliseen sivuun.
