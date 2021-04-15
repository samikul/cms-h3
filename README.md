# cms-h3
Answers to cms-course's excercise 3


Tehtävässä käytetty [ohjemateriaali](http://terokarvinen.com/2016/publish-your-project-with-github/) (Tero Karvinen, 2016).

## a) MarkDown. Tee tämän tehtävän raportti MarkDownina. Helpointa on tehdä raportti GitHub-varastoon, jolloin md-päätteise$

### Uuden varaston luonti
Kirjauduin [Githubiin](https://github.com) sisään ja loin uuden varaston valitsemalla "New".

- Owner
  - samikul
- Repository name
  - cms-h3
- Description
  - Answers to cms-course's excercise 3

- Public
  - Varasto on näkyvissä julkisessa internetissä
- Add a README file
  - Github generoi tyhjän README.md tiedoston, johon kirjoitetaan projektin dokumentaatiota. Tässä tapauksessa dokumentaation on vastaukseni tehtävänantoon.
- Add .gitignore
  - .gitignore tiedostolla määritellään ne tiedostopäätteet, joita versionhallintaan ei lähetetä. Nyt tälle ei ole tarvetta.
- Choose a licence
  - GNU General Public Licence v3.0 antaa muille hyvin vapaat kädet, mutta vaatii GPL v3.0 lisenssin käyttämistä niissä tuotteissa ja projekteissa$

Valitsin "Create repository".

![1](https://user-images.githubusercontent.com/58463139/114843219-46260a80-9de2-11eb-891a-e6e669ea518b.JPG)

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

![2](https://user-images.githubusercontent.com/58463139/114843222-46bea100-9de2-11eb-8d3a-8ab49c18d4a7.JPG)

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

![3](https://user-images.githubusercontent.com/58463139/114843225-46bea100-9de2-11eb-8a4e-a5473625007d.JPG)

### Versiohallintaan työntäminen

Tein muokkauksia tekstieditorillani `README.md` tiedostoon

	$ nano README.md

Tallensin ja suljin tiedoston.

	# Lisätään muutokset paikalliselta varastolta valmistelualueelle
	$ git add .
	
	# Lisäsin muutoksia kuvaavan rivin, jonka tulisi olla
	# lyhyt ja määräysmuodossa oleva englanninkielinen kommentti
	$ git commit
	# CTRL - X, y, enter

	# Konfliktien varalta vedetään (mahdolliset ja muiden tekemät) muutokset omalle tietokoneelle
	$ git pull

	# Työnnetään tehdyt muutokset versiohallintaan
	$ git push

![4](https://user-images.githubusercontent.com/58463139/114843227-47573780-9de2-11eb-9e18-4b67e53da55b.JPG)

	$ git add . && git commit; git pull && git push
