# Sami Kulonpää

## Lähtötilanne ja työympäristö

|                 |                                                                                                      |
| :---            | :-----------------------------------------------------------------------------------------------------|
|Tehtävät         |[h3 - terokarvinen.com](https://terokarvinen.com/2021/configuration-management-systems-palvelinten-hallinta-ict4tn022-spring-2021/#h3-versionhallinta)         |
|Kurssisivu       |[ICT4TN022-3011](https://terokarvinen.com/2021/configuration-management-systems-palvelinten-hallinta-ict4tn022-spring-2021/)|
|Tietokone        |Lenovo ThinkPad T495                                                                                  |
|Käyttöjärjestelmä|Windows 10 64-bit                                                                                     |
|Työympäristö     |Oracle VM VirtualBox 6.1.18 & [debian-live-10.8.0-amd64-xfce+nonfree.iso](https://cdimage.debian.org/images/unofficial/non-free/images-including-firmware/current-live/amd64/iso-hybrid/debian-live-10.8.0-amd64-xfce+nonfree.iso)                  |

Tehtävässä käytetty [ohjemateriaali](http://terokarvinen.com/2016/publish-your-project-with-github/) (Tero Karvinen, 2016).
[Git-sanastoa suomeksi](https://book.sovelluskontti.com/versionhallinta/sanasto) (Turo Nylud, 2020).

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

[Yhdellä komennolla](http://terokarvinen.com/2016/publish-your-project-with-github/)(Tero Karvinen, 2016) voidaan toteuttaa versiohallinnan peruskäyttöä.
	
	$ git add . && git commit; git pull && git push


`git add .` lisää tehdyt muutokset paikalliselta varastolta valmistelualueelle. Looginen operaattori `&&` tarkastaa
sitä edeltävän komennon loppustatuksen ja suorittaa seuraavan komennon `git commit`, mikäli edellinen komento toteutui
onnistuneesti.

Puolipiste ` ; ` tarkoittaa rivinvaihtoa. Seuraavaksi ajetaan vetokäsky `git pull`, jonka onnistuttua ajetaan
työntökäsky `git push`, joka vie paikallisesti tehdyt muutokset Githubin versiohallintaan.  

## d) Näytä omalla git-varastollasi esimerkit komennoista ‘git log’, ‘git diff’ ja ‘git blame’. Selitä tulokset.

Komento `git log` tulostaa komentoriville varaston muutoshistorian. Tulosteessa näkyy kuka, mitä ja milloin.
- Muutoksen id ja mitä varaston haaraa muutos koskee
- Author: tekijä
- Date: muutosajankohta
- muutosviesti

![kuva](https://user-images.githubusercontent.com/58463139/114847784-c189bb00-9de6-11eb-892b-7c3724f77a7f.png)

Komento `git diff` näyttää muutokset.
Muokkasin tiedostoa `README.md` ja työnsin muutokset versiohallintaan.

	$ git add . && git commit; git pull && git push

Syötin `git diff README.md` komennon. Komentoriville tulostui värikoodattuna tekemäni muutos.

![kuva](https://user-images.githubusercontent.com/58463139/114858494-3282a000-9df2-11eb-9f64-c2742d0f319a.png)

Komennolla `git blame` voidaan tarkastella kunkin tiedoston metatietoja. Komennolla voidaan selvittää rivikohtaisesti, että kuka ja miten riviä on muokattu sekä mihin lähetykseen (commit) rivi kuuluu.

![kuva](https://user-images.githubusercontent.com/58463139/114857570-15999d00-9df1-11eb-81f2-83861b600494.png)

## e) Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset –hard’. Huomaa, että tässä toiminnossa ei ole peruutusnappia.

Lisäsin poistettavan tekstin `README.md` tiedostoon

![55](https://user-images.githubusercontent.com/58463139/115264154-b7e1b980-a13e-11eb-9f4f-e334f71c8f30.JPG)

Komennolla `git status` näyttää muokatun tiedoston ja sen, ettei tiedostoa ole lisätty valmistelualueelle.

```git
sami@kuja:~/palvelintenhallinta/cms-h3$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

```
$ git reset --hard
HEAD is now at c053a6e edit readme
```

- [HEAD](https://stackoverflow.com/questions/2304087/what-is-head-in-git) viittaa varastoon ja sen haaraumaan
- `c053a6e` viittaa viimeisimpään versiohallintaan työnnetyn varaston haarauman muutokseen
- `edit readme` on em. muokkauksen tarkenne


## f) Tee uusi salt-moduli. Voit asentaa ja konfiguroida minkä vain uuden ohjelman: demonin, työpöytäohjelman tai komentokehotteesta toimivan ohjelman. Käytä tarvittaessa ‘find -printf “%T+ %p\n”|sort’ löytääksesi uudet asetustiedostot. (Tietysti eri ohjelma kuin aiemmissa tehtävissä, tarkoitushan on harjoitella Salttia)
