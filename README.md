# Mi az a Git és GitHub?

## A Git

A Git egy elosztott verziókezelő rendszer, amit Linus Torvalds fejlesztett 2005-ben.

**Lehetővé teszi:**

- a kódváltozások nyomonkövetését gitben
- a korábbi kódverziókhoz visszatudjunk térni
- Párhuzamos fejlesztés a brancheken
- Offline munka a teljes projekt historyjával

## A GitHub

A GitHub egy felhőalapú platform, ahová feltöltheted a Git repóidat, hogy másokkal megoszd őket. Itt feltöltheted a git repository tárolására és kezelésére.

- repo hosting
- együttműködési eszközök (pull, push, request, Issue)

**Git** az egy verziókezelő rendszer, amit a **GitHub** használ a repository tárolására és kezelésére.

# Miért érdemes megtanulni a Git-et?

- **Ipari szabvány:** Szinte minden szoftverfejlesztő cég ezt használja, elvárja ezt.
- **Biztonság:** Bármikor visszaállíthatsz egy korábbi, működő verziót, a kódodban.
- **Csapatmunka:** Többen dolgozhattok ugyanazon a projekten anélkül, hogy zavarnátok egymást.
- **Karrier:** Alapvető elvárás a legtöbb IT munkahelynél.
- **Dokumentáció:** A Git dokumentációja elég részletes és könnyen elismert.
- **Történet:** Minden változás visszakövethető a history-ban.
- **Offline munka:** A teljes history-t is letöltheted a gépedre, offline munkára.

## 10 Egyszerű Git Példa

1. **Repository létrehozása:** `git init` - Új Git projekt indítása a jelenlegi mappában.
2. **Repository másolása:** `git clone [url]` - Egy távoli projekt letöltése a saját gépedre.
3. **Állapot ellenőrzése:** `git status` - Mely fájlok változtak, mi van staging-en.
4. **Fájlok hozzáadása:** `git add [fájl]` vagy `git add .` - Változások előkészítése commit-hoz.
5. **Változások mentése:** `git commit -m "[üzenet]"` - A staging-en lévő változások rögzítése.
6. **Változások feltöltése:** `git push` - A helyi commit-ok küldése a távoli szerverre (pl. GitHub).
7. **Változások letöltése:** `git pull` - A távoli változások frissítése a helyi gépen.
8. **Előzmények megtekintése:** `git log` - A korábbi commit-ok listázása.
9. **Új ág létrehozása:** `git branch [ág_neve]` - Új fejlesztési ág nyitása.
10. **Átváltás másik ágra:** `git checkout [ág_neve]` vagy `git switch [ág_neve]` - Munkaterület váltása.

## 10 Haladó Git Példa

1. **Változások ideiglenes elmentése:** `git stash` - Félkész munka elmentése ágváltás előtt.
2. **Stash visszatöltése:** `git stash pop` - Az elmentett félkész munka visszahozása.
3. **Commit módosítása:** `git commit --amend` - Az utolsó commit javítása (pl. üzenet vagy kifelejtett fájl).
4. **Visszaállítás (Soft):** `git reset --soft HEAD~1` - Az utolsó commit visszavonása, de a változások megmaradnak. 
5. **Visszaállítás (Hard):** `git reset --hard HEAD~1` - Az utolsó commit és a változások teljes törlése (Vigyázz!).
6. **Rebase (Előzmények tisztítása):** `git rebase [ág_neve]` - A commit-ok újraírása egy másik ág végére (lineáris history).
7. **Cherry-pick:** `git cherry-pick [commit_hash]` - Egyetlen konkrét commit átemelése egy másik ágra.
8. **Keresés a kódban (history-ban is):** `git grep "[keresett_szó]"` - Gyors keresés a verziózott fájlokban.
9. **Ki írta ezt a sort?:** `git blame [fájl]` - Megmutatja, melyik sort ki és mikor módosította utoljára.
10. **Törölt commit-ok keresése:** `git reflog` - A "láthatatlan" history, életmentő lehet, ha véletlenül töröltél valamit.

## Telepítés
git version
git -version

## Konfiguráció
git config --global user.name "mike6776"
git config --global user.email "kurthym2010@gmail.com"
git config --global core.editor "notepad"
git config --global core.autocrlf true





