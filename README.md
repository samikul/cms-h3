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

## a) MarkDown. Tee tämän tehtävän raportti MarkDownina. Helpointa on tehdä raportti GitHub-varastoon, jolloin md-päätteiset tiedostot muotoillaan automaattisesti. Tyhjä rivi tekee kappalejaon, risuaita ‘#’ tekee otsikon, sisennys merkitsee koodinpätkän. Vinkkinä artikkelini [Publish Your Project with GitHub](http://terokarvinen.com/2016/publish-your-project-with-github/index.html).

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
  - GNU General Public Licence v3.0 antaa muille hyvin vapaat kädet, mutta vaatii GPL v3.0 lisenssin käyttämistä niissä tuotteissa ja projekteissa, jotka ovat toteutettu GPL v3.0 lisenssin alaisuudessa.

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

- [HEAD](https://book.sovelluskontti.com/versionhallinta/sanasto) viittaa varaston ja haaraumaan viimeisimpään versiohallintaan lähetettyyn muutokseen.
- `c053a6e` viittaa viimeisimpään versiohallintaan työnnetyn varaston haarauman muutokseen
- `edit readme` on em. muokkauksen tarkenne


## f) Tee uusi salt-moduli. Voit asentaa ja konfiguroida minkä vain uuden ohjelman: demonin, työpöytäohjelman tai komentokehotteesta toimivan ohjelman. Käytä tarvittaessa ‘find -printf “%T+ %p\n”|sort’ löytääksesi uudet asetustiedostot. (Tietysti eri ohjelma kuin aiemmissa tehtävissä, tarkoitushan on harjoitella Salttia)

Tehtävän tekoon saatiin luennolla lisäaikaa. Tehtävä tehty määräajan umpeutumisen jälkeen.

Tein tilan, jolla kloonataan githubista määritelty varasto. Käsin tehtynä toimenpide on hyvin suoraviivainen

```
$ git clone https://github.com/samikul/cms-h3.git
Cloning into 'cms-h3'...
remote: Enumerating objects: 35, done.
remote: Counting objects: 100% (35/35), done.
remote: Compressing objects: 100% (27/27), done.
remote: Total 35 (delta 8), reused 24 (delta 6), pack-reused 0
Unpacking objects: 100% (35/35), done.
```
Poistin gitin, jotta voin asentaa sen Saltin avulla
```
$ sudo apt-get purge git
$ sudo apt-get autoremove
```
Loin Saltille uuden hakemiston
```
$ sudo mkdir /srv/salt/git
```
Hakemistoon loin ajettavan tilan
```salt
$ sudo nano init.sls 

git:
  pkg.installed

```
Ajoin tilan ja Salt asensi koneelleni versiohallinan
```salt
$ sudo salt '*' state.apply git
sami:
----------
          ID: git
    Function: pkg.installed
      Result: True
     Comment: The following packages were installed/updated: git
     Started: 20:34:38.001466
    Duration: 8823.758 ms
     Changes:   
              ----------
              git:
                  ----------
                  new:
                      1:2.20.1-2+deb10u3
                  old:
              git-completion:
                  ----------
                  new:
                      1
                  old:
              git-core:
                  ----------
                  new:
                      1
                  old:
              git-man:
                  ----------
                  new:
                      1:2.20.1-2+deb10u3
                  old:
              liberror-perl:
                  ----------
                  new:
                      0.17027-2
                  old:

Summary for sami
------------
Succeeded: 1 (changed=1)
Failed:    0
------------
Total states run:     1
Total run time:   8.824 s
```
Muokkasin tilaa ja lisäsin säännön kansion luomiselle.
```salt
$ sudo nano /srv/salt/git/init.sls

git:
  pkg.installed

create directory for git repos:
  file.directory:
    - name: /git-repos

```
Otin tilan käyttöön
```salt
$ sudo salt '*' state.apply git
sami:
----------
          ID: git
    Function: pkg.installed
      Result: True
     Comment: All specified packages are already installed
     Started: 20:52:27.544526
    Duration: 390.923 ms
     Changes:   
----------
          ID: create directory for git repos
    Function: file.directory
        Name: /git-repos
      Result: True
     Comment: Directory /git-repos updated
     Started: 20:52:27.937315
    Duration: 0.924 ms
     Changes:   
              ----------
              /git-repos:
                  New Dir

Summary for sami
------------
Succeeded: 2 (changed=1)
Failed:    0
------------
Total states run:     2
Total run time: 391.847 ms
```
Muokkasin tilaa siten, että komentoriville syötetään komento, joka vie haluttuun hakemistoon, jossa ajetaan komento, joka kloonaa halutun git-varaston.
```salt
$ sudo nano /srv/salt/git/init.sls

git:
  pkg.installed

create directory for git repos:
  file.directory:
    - name: /git-repos'

'cd /git-repos':
  cmd.run:
    - name: git clone https://github.com/samikul/cms-h3.git
```
Otin tilan käyttöön.
```salt
$ sudo salt '*' state.apply git
sami:
----------
          ID: git
    Function: pkg.installed
      Result: True
     Comment: All specified packages are already installed
     Started: 21:01:49.295838
    Duration: 396.302 ms
     Changes:   
----------
          ID: create directory for git repos
    Function: file.directory
        Name: /git-repos'
      Result: True
     Comment: Directory /git-repos' updated
     Started: 21:01:49.693993
    Duration: 0.935 ms
     Changes:   
              ----------
              /git-repos':
                  New Dir
----------
          ID: cd /git-repos
    Function: cmd.run
        Name: git clone https://github.com/samikul/cms-h3.git
      Result: True
     Comment: Command "git clone https://github.com/samikul/cms-h3.git" run
     Started: 21:01:49.695647
    Duration: 736.31 ms
     Changes:   
              ----------
              pid:
                  14138
              retcode:
                  0
              stderr:
                  Cloning into 'cms-h3'...
              stdout:

Summary for sami
------------
Succeeded: 3 (changed=2)
Failed:    0
------------
Total states run:     3
Total run time:   1.134 s
```
Hakemisto `/git-repos` oli kuitenkin tyhjä. Johonkin varasto kloonattiin, mutta ei ainakan oikeaan paikkaan.
Etsin [ohjeet](https://www.cyberciti.biz/faq/howto-find-a-directory-linux-command/) miten etsiä hakemistoa. Komennon `find` jälkeen haetaan koko järjestelmästä hakemistoa, jonka nimi on "cms-h3".
```
$ sudo find / -type d -name "cms-h3"
/home/sami/palvelintenhallinta/cms-h3
/home/sami/git-testit/cms-h3
/root/cms-h3
```
Varasto kloonattiin `/root/cms-h3` hakemistoon. Se ei missään nimessä ole oikea paikka hakemistolle. Tältä erää ongelmanratkonta jää kesken ja palaan tähän myöhemmin uudelleen.
