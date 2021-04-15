# cms-h3
Answers to cms-course's excercise 3

## a) MarkDown. Tee tämän tehtävän raportti MarkDownina. Helpointa on tehdä raportti GitHub-varastoon, jolloin md-päätteise$

### Uuden varaston luonti
Kirjauduin [Githubiin](https://github.com) sisään ja loin uuden varaston valitsemalla "New".

- Owner
  - "samikul"
- Repository name
  - "cms-h3"
- Description
  - "Answers to cms-course's excercise 3"

- Public: yes
  - jotta kaikki voivat tarkastella varastoa
- Add a README file: yes
  - Github generoi tyhjän README.md tiedoston, johon (tässä tapauksessa) kirjoitan vastaukseni tehtävänantoon.
- Add .gitignore: no
  - .gitignore tiedostolla määritellään ne tiedostopäätteet, joita versionhallintaan ei lähetetä. Nyt tälle ei ole tarvetta.
- Choose a licence: GNU General Public Licence v3.0
  - GPL v3.0 antaa muille hyvin vapaat kädet, mutta vaatii GPL v3.0 lisenssin käyttämistä niissä tuotteissa ja projekteissa$

Valitsin "Create repository".

1. KUVA

### Versiohallinan asentaminen ja käyttöönotto

Olin jo aiemmin käyttänyt versiohallintaa. Raportoinnin vuoksi poistin ja asensin sen uudelleen.

        # Gitin poisto
        $ sudo apt-get purge git
        # Gitin mukana asentuneiden riippuvuuksien poisto
        $ sudo apt-get autoremove
        # Gitin asennus
        $ sudo apt-get install -y git

        # Määritin tietoni, jotka näkyvät versiohallinnassa päivitysteni yhteydessä.
        $ git config --global user.email "bgh296@myy.haaga-helia.fi"
        $ git config --global user.name "Sami Kulonpää"
        # Versiohallinta muistaa syöttämäni salasanan tunnin ajan (60*60)
        $ git config --global credential.helper "cache --timeout=3600"

### Varaston kloonaus

Valitsin "Code" -> "HTTPS" ja kopioin URL-osoitteen `https://github.com/samikul/cms-h3.git`

2. KUVA

        # Kloonasin varaston tietokoneelleni
        $ git clone https://github.com/samikul/cms-h3.git
        # Siirryin hakemistoon
        $ cd cms-h3/

Nyt GitHubissa luomani varasto tiedostoineen on järjestelmälläni.
- README.md
  - markdown-tiedosto mahdollistaa yksinkertaisen ja helpon tavan muotoilla tekstiä.
  - `.md` on valmis käytettäväksi esim. html-julkaisuun
- LICENCE
  - Pitää sisällään GNU GPL v3.0 lisenssin tiedot

3. KUVA

### Versiohallintaan työntäminen

Tein muokkauksia tekstieditorillani `README.md` tiedostoon

	$ nano README.md

Tallensin ja suljin tiedoston.


