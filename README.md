# Mi az a Git és GitHub?

## A Git

A Git egy elosztott verziókezelő rendszer, amit Linus Torvalds fejlesztett 2005-ben.

**Lehetővé teszi:**

- a kódváltozások nyomonkövetését gitben
- a korábbi kódverziókhoz visszatudjunk térni
- Párhuzamos fejlesztés a brancheken
- Offline munka a teljes projekt historyjával

## A GitHub

A GitHub egy felhőalapú platform, ahová feltöltheted a Git repóidat, hogy másokkal megoszd őket.

- Repo hosting (tárhely)
- Együttműködési eszközök (Pull Request, Issue tracking, Code Review)

> **Git** az egy verziókezelő eszköz (szoftver), amit a **GitHub** szolgáltatás használ a repositoryk tárolására és vizualizálására.

# Telepítés és Konfiguráció

## Telepítés ellenőrzése

```bash
git --version
```

## Alapbeállítások (User)

Telepítés után kötelező beállítani, hogy ki vagy (ez látszik majd a commitokban):

```bash
git config --global user.name "Te Neved"
git config --global user.email "email@cim.com"
```

## Egyéb hasznos beállítások

```bash
# Alapértelmezett szövegszerkesztő
# Ha VS Code-ot használsz, érdemes így beállítani:
git config --global core.editor "code --wait"

# Sorvégződések kezelése (Windows vs Linux/Mac eltérések kiküszöbölése)
git config --global core.autocrlf true
```

## Hasznos Git Aliasok (Gyorsítás)

Beállíthatsz rövidítéseket a gyakran használt parancsokhoz, hogy gyorsabban gépelj:

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

*Így a `git status` helyett elég beírni: `git st`.*

# Miért érdemes megtanulni a Git-et?

- **Ipari szabvány:** Szinte minden szoftverfejlesztő cég ezt használja, elvárja ezt.
- **Biztonság:** Bármikor visszaállíthatsz egy korábbi, működő verziót a kódodban.
- **Csapatmunka:** Többen dolgozhattok ugyanazon a projekten anélkül, hogy zavarnátok egymást (merge konfliktusok kezelése).
- **Dokumentáció:** A Git history önmagában egy dokumentáció arról, hogy mi, mikor és miért változott.
- **Offline munka:** A teljes history-t is letöltheted a gépedre, így internet nélkül is tudsz commitolni.

# Parancsok Gyűjteménye

## 10 Alapvető Git Példa

1. **Repository létrehozása:** `git init`  
   Új Git projekt indítása a jelenlegi mappában. Létrehozza a rejtett `.git` mappát.
2. **Repository másolása:** `git clone [url]`  
   Egy távoli projekt (pl. GitHub) letöltése a saját gépedre.
3. **Állapot ellenőrzése:** `git status`  
   Megmutatja, mely fájlok változtak, mi van staging-en, és melyik branch-en vagy.
4. **Fájlok hozzáadása (Staging):** `git add [fájl]` vagy `git add .`  
   Változások előkészítése commit-hoz. A `git add .` mindent hozzáad.
5. **Változások mentése (Commit):** `git commit -m "[üzenet]"`  
   A staging-en lévő változások rögzítése a lokális history-ba. Az üzenet legyen leíró!
6. **Változások feltöltése:** `git push`  
   A helyi commit-ok küldése a távoli szerverre (pl. GitHub).
7. **Új változások letöltése:** `git pull`  
   A távoli változások frissítése a helyi gépen (fetch + merge egyben).
8. **Előzmények megtekintése:** `git log`  
   A korábbi commit-ok listázása (hash, szerző, dátum, üzenet).
   *Tipp: `git log --oneline` a tömörebb nézetért.*
9. **Új ág létrehozása:** `git branch [ág_neve]`  
   Új fejlesztési ág nyitása a kísérletezéshez.
10. **Átváltás másik ágra:** `git checkout [ág_neve]` vagy `git switch [ág_neve]`  
   Munkaterület váltása a branchek között.

## 10 Haladó Git Példa

1. **Változások ideiglenes elmentése:** `git stash`  
   Félkész munka "zsebbe rakása" ágváltás előtt, commit nélkül.
2. **Stash visszatöltése:** `git stash pop`  
   Az elmentett félkész munka visszahozása és törlése a stash-ből.
3. **Commit módosítása:** `git commit --amend`  
   Az utolsó commit javítása (pl. rossz üzenet vagy kifelejtett fájl hozzáadása után).
4. **Visszaállítás (Soft):** `git reset --soft HEAD~1`  
   Az utolsó commit visszavonása, de a fájl módosítások megmaradnak (staging-en).
5. **Visszaállítás (Hard):** `git reset --hard HEAD~1`  
   Az utolsó commit és a változások **teljes és végleges** törlése. (Vigyázz!)
6. **Rebase (Előzmények tisztítása):** `git rebase [ág_neve]`  
   A saját commit-jaid "átmozgatása" egy másik ág végére a tisztább, lineáris history-ért.
7. **Cherry-pick:** `git cherry-pick [commit_hash]`  
   Egyetlen konkrét commit átemelése egy másik ágról a jelenlegire.
8. **Keresés a kódban (history-ban):** `git grep "[keresett_szó]"`  
   Gyors keresés a verziózott fájlok tartalmában.
9. **Ki írta ezt a sort?:** `git blame [fájl]`  
   Soronként megmutatja, ki és mikor módosította utoljára a fájlt.
10. **Törölt dolgok keresése:** `git reflog`  
    A "láthatatlan" history, minden fejmozgást naplóz. Életmentő, ha véletlenül töröltél egy commitot.

# Részletes Témakörök

## .gitignore - Mit ne töltsünk fel?

A `.gitignore` egy egyszerű szöveges fájl a projekt gyökerében. Megadja azokat a fájlokat, amiket a Git-nek **SOHA** nem szabad követnie.

**Mi kerüljön ide?**

- Érzékeny adatok (jelszavak, API kulcsok, `.env`)
- Build fájlok és mappák (`dist/`, `build/`, `bin/`)
- Csomagkezelő mappák (`node_modules/`, `venv/`, `__pycache__/`)
- Operációs rendszerfájlok (`.DS_Store`, `Thumbs.db`)

## Konfliktuskezelés (Merge Conflicts)

Ha ketten ugyanazt a sort módosítjátok, a Git nem tud automatikusan dönteni. Ekkor **konfliktus** keletkezik.

1. A `git merge` vagy `git pull` hibát jelez.
2. Nyisd meg a hibás fájlt.
3. Keresd a `<<<<<<<`, `=======`, `>>>>>>>` jelöléseket.
4. Döntsd el, melyik kód maradjon (vagy írd át teljesen).
5. Töröld ki a Git jelöléseit.
6. Mentsd a fájlt, majd futtasd: `git add [fájl]` és `git commit`.

## Távoli Tárolók (Remotes)

Kapcsolat a helyi géped és a GitHub között.

- `git remote -v`: Listázza a beállított kapcsolatokat (általában 'origin').
- `git remote add origin [url]`: Hozzáadja a GitHub repo címét a helyi mappához.
- `git fetch origin`: Letölti az infókat a szerverről, de nem nyúl a fájljaidhoz.

## Verziók Jelölése (Tagging)

A commitok elnevezése stabil pontokként (pl. v1.0).

- **Létrehozás:** `git tag -a v1.0 -m "Verzió 1.0 kiadás"`
- **Listázás:** `git tag`
- **Feltöltés:** `git push origin v1.0` (A `git push` alapból nem küldi a tageket!)

## Különbségek Vizsgálata (Diff)

Mielőtt commitolsz, érdemes megnézni, mit írtál át pontosan.

- **Még nem addolt fájlok:** `git diff`
- **Már addolt (staged) fájlok:** `git diff --staged`
- **Két commit között:** `git diff [commit_hash_1] [commit_hash_2]`

# Csapatmunka (Workflow)

Egy fejlesztői csapatban nem dolgozhat mindenki egyszerre a `main` ágon. Íme a profi munkafolyamat:

1. **Frissítés:** Mindig a legfrissebb állapotból indulj:

   ```bash
   git checkout main
   git pull origin main
   ```

2. **Feature Branch:** Hozz létre egy új ágat a feladatodnak:

   ```bash
   git checkout -b feature/uj-login-oldal
   ```

3. **Munka:** Dolgozz, commitolj, amíg kész nem vagysz.
4. **Push:** Töltsd fel a saját ágad:

   ```bash
   git push origin feature/uj-login-oldal
   ```

5. **Pull Request (PR):** Kérj engedélyt (a GitHub-on), hogy az ágad bekerüljön a `main`-be.

# GitHub Pull Request (PR)

A Pull Request az a hely, ahol a kollégák átnézik (Code Review) a kódodat, mielőtt élesítenék.

1. Menj fel a GitHub repository oldalára.
2. Látni fogsz egy sárga sávot: "feature/uj-login-oldal had recent pushes". Kattints a **"Compare & pull request"** gombra.
3. Adj címet és leírást (mit csináltál, hogyan tesztelted).
4. Kattints a **"Create pull request"** gombra.
5. Várj a visszajelzésekre (Review). Ha javítani kell valamit, azt a *saját gépeden* javítsd, commitold és pushold ugyanerre az ágra. A PR automatikusan frissül!
6. Ha elfogadták, kattints a **"Merge pull request"** gombra.

# Commit Üzenet Konvenciók

A jól megírt commit üzenetek segítenek abban, hogy hónapok múlva is értsd (és a csapattársaid is értsék), mi miért történt.

## Conventional Commits

Ez a legnépszerűbb szabvány. Segítségével automatikusan generálható a changelog és könnyebb keresni a history-ban.

**Formátum:** `<típus>(<hatókör>): <leírás>`

- `feat`: Új funkció (Feature)
- `fix`: Hibajavítás (Bug fix)
- `docs`: Dokumentáció (pl. README bővítése)
- `style`: Formázás (space, pontosvessző, kód működését nem érinti)
- `refactor`: Kód átszervezése (se hiba, se új feature)
- `perf`: Teljesítmény javítás (Performance)
- `test`: Tesztek hozzáadása
- `chore`: Karbantartás, build folyamat (Dependencies, config)

**Példa:** `feat(auth): login oldal validáció hozzáadása`

## A Jó Commit 7 Aranyszabálya

1. Legyen üres sor az üzenet címe és a törzse között.
2. A cím ne legyen hosszabb 50 karakternél.
3. A címe nagybetűvel kezdődjön.
4. Ne tegyél pontot a cím végére.
5. Használj **felszólító módot** (pl. „Fix bug” és nem „Fixed bug”).
6. A törzs sorai ne legyenek hosszabbak 72 karakternél.
7. A törzsben fejtsd ki a **MIÉRT**-et, ne azt, hogy **HOGYAN**.

# "Baj van!" - Hibaelhárítás

Ne pánikolj, a Git-ben (szinte) mindent vissza lehet csinálni.

**Probléma: "Véletlenül töröltem/módosítottam egy fájlt, de még nem commitoltam."**
Megoldás (Visszaállítás):

```bash
git restore [fájl]
# vagy minden módosítás eldobása a jelenlegi mappában:
git restore .
```

**Probléma: "Rossz commitot csináltam, de még nem pusholtam."**
Megoldás (Commit visszavonása, de a munka megmarad):

```bash
git reset --soft HEAD~1
```

**Probléma: "Teljesen elszúrtam mindent, vissza akarom kapni a legutolsó jó állapotot."**
Megoldás (Minden lokális változás törlése - ÓVATOSAN!):

```bash
git reset --hard HEAD
```

**Probléma: "Nem tudok pusholni, mert valaki más már pusholt előttem."**
Megoldás (Letöltés és összefésülés):

```bash
git pull origin [ág_neve]
# Oldd meg a konfliktusokat ha vannak, majd commit és push újra.
```
