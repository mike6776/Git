# Mi az a GIT és GITHub?

# Néhány fogalom
    - Baseline egy fájl/dokumentum jováhagyott verziója
    - Branch (ág) egy fájlnak több verzója is fejlődhet egyszerre
    - Check-out lokális másolat
    - Check-in, Commit vagy Submit lokális másolat feltöltése
    - Conflict két egymást kiütő módosítás
    - Change változtatás
    - Change list cáltozások listája commito-on belül
    - Export check-out metaadatok nélkül
    - Head legutóbbi commit
    - Import lokális adatok felmásolása és verziókontroll alá helyezése
    - Mainline Egy branch fő ága
    - Merge két változás összefűzése
    - Repository verziók tárolóhelye
    - Reverse integration egyes ágak összefüzése
    - Revision verzió
    - Trunk a fejlesztés olyan vonala ami nem ág
    - Resolve változási konfliktusok feloldásának művelete
    - Update a legutolsó szinkronizáció óta történt változtatások frissítése
    - Working copy munkamásolat, lokális gépen


## Git
A git egy elosztott verziokezelő rendser, amelyet Linus Torvald fejlesztett 2005-ben. Lehetővé teszi:
- Kódválátozások nyomon követését.
- Korábibbi kódverziókhoz való visszatérést
- Párhuzamos fejlesztést branch-eken
- Offline munka a teljes projekt történelmével

## GitHub
A GitHub egy felhőalapú platform Git repository-k tárolására és kezelésére. Funkciói:
- Repository hosting
- Egyműködési eszközök (Issue, Pull Request)
- CI/CD Integráció (GitHub Actions)
- Projektmenedzsment (Projects, Milestones)
- Kód review és biztonság

> Összefoglalva</br>
**Git** = verziókezelő eszköz a gépeden **GitHub** = onlene platform a repository-k tárolására


## Miért érdemes megtanulni?

| Szempont | Előny |
| :--- | :--- |
| Csapatmunka |	Több fejlesztő dolgozhat ugyanazon a projekten |
| Biztonság | A kód biztonságosan tárolva, nem vész el |
| Történet |	Minden változás visszakövethető |
| Visszaállítás |	Bármikor visszatérhetsz korábbi verzióhoz |
| Iparági standard |	A legtöbb cég elvárja a Git ismeretét |


 # Telepítés és beállítás

 ## 1. Windows

 Töltsd le a telepítőt: [Letöltés](https://github.com/git-for-windows/git/releases/download/v2.52.0.windows.1/Git-2.52.0-64-bit.exe)

 ## 2. Linux (ubuntu / debian)

 ```
    sudo apt update
    sudo apt install git
 ```
 

 ### Ellenörzés

```
    git --version
    git version
```
 
## 2. GitHub fiók létrehozása
1. Látogass el a github.com/signup oldalra
2. Add meg az email címed (vagy használd a google fiókod és akkor az utóbbiak nem szükségesek)
3. Válassz felhasználónevet és jelszót
4. Erősítsd meg az email címed
 

## 3. Git konfiguráció (Ezeket érdemes beállítani mi nem csináltuk meg)
A GitHub fiókod összekapcsolása a Git-tel:
```
    # Felhasználónév beállítása
    git config --global user.name "Felhasználóneved"

    # Email beállítása (ugyanaz, mint a GitHub-on)
    git config --global user.email "email@example.com"

    # Alapértelmezett branch neve
    git config --global init.defaultBranch main

    # Alapértelmezett editor
    git config --global core.editor "code"

    # Beállítások ellenőrzése
    git config --list
```
 
# Git alapvető parancsok

 Repository létrehozása (lokális)
```
    # Új repository inicializálása
    git init

    # Meglévő repository klónozása
    git clone https://github.com/user/repo.git

    # SSH-val klónozás
    git clone git@github.com:user/repo.git

```

- ## Alapvető műveletek
```
 # 1. Állapot ellenőrzése
git status

# 2. Fájlok hozzáadása a staging area-hoz
git add .                    # Minden fájl
git add filename.php         # Egy fájl
git add src/                 # Egy mappa

# 3. Változások commitolása
git commit -m "Add: új funkció leírása"
git commit -am "Funkció leírás"

# 3.a Változások elküldése és hozzáadása a commithoz,
     ebben az esetben a default editort használja a coommit szövegének elkészítéséhez
git commit -a 

# 4. Feltöltés GitHub-ra
git push origin main
```

- ##  Létező lokális repo hozzárendelése egy távoli repository-hoz
```
    git remote add origin https://github.com/szilasii/git.git
    git branch -M main
    git push -u origin main
```
> CTRL + SHIFT + P code parancsok megnyítása<br>
> CTRL + SHIFT + V Markdown file előnézete


## Branch kezelés
```
    # Branch-ek listázása
    git branch
    # Branch átnevezése
    git branch (-m|-M) [<old-branch>] <new-branch>
    # Branch léterhozása
    git branch (-c|-C) [<old-branch>] <new-branch>
    # Branch törlése
    git branch (-d|-D) [-r] <branch-name>…​
    
    # Branch váltás
    git checkout main

    # Új branchlétrehozása és váltás
    git checkout -b program



```
# Néhány hasznos parancs
```
    #Változások megtekintése
    git diff
    #Commitok története
    git log --oneline
    # Utolsó commit visszavonása (lokálisan)
    git reset --soft HEAD~1
    # utolso commit visszaállítása (minden változtatás is törlödik)
    git reset HEAD~1
    #fájl visszaállítása
    git checkout <fájlnév>
    #Stash változások ideiglenes félretétele
    git stash
    git stash pop
```
# Git Commit üzenet konvenciók

```
<tipus>: <rövid leírás>
# Típusok
feat: új funkció
fix: Hibajavítás
docs: Dokumentáció
style: Formázás (nem változik a kód)
refactor: Refaktorálás
test: Tesztek
chore: Build, konfiguráció
# Példa
git commit -m "feat: add user Autentication"
```
# .gitignore
Ez a ***.gitignore*** fájl meghatározza, hogy mely fájlokat ne kövesse a git.

