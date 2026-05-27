# sPg-Blueprint-Extractor-Recept-anyagok

**Star Citizen Blueprint Extractor – Használati útmutató / User Guide**

Ez az eszköz arra való, hogy a Star Citizen logfájljaidból kiszedje, milyen **Blueprintjeid** vannak meg, majd összevesse őket a Star Citizen Wiki blueprint adatbázisával.

This tool extracts your owned **Blueprints** from your Star Citizen log files, then compares them with the Star Citizen Wiki blueprint database.

**Fájl neve / File name:**
`sc_blueprint_log_extractor_recipe_materials_quest_details_clean.html`

---

## Magyar útmutató

**1. Megnyitás**

Nyisd meg a HTML fájlt böngészőben.

Ajánlott böngésző:

* Chrome
* Edge

Nem kell telepíteni semmit. Ez egy sima HTML fájl.

---

**2. Log mappa kiválasztása**

Kattints a **Mappa kiválasztása** gombra.

Válaszd ki ezt a mappát:

`Roberts Space Industries\StarCitizen\LIVE\logbackups`

Példa teljes útvonalra:

`D:\Roberts Space Industries\StarCitizen\LIVE\logbackups`

---

**3. Mit csinál automatikusan?**

A mappa kiválasztása után a program:

* átnézi a `.log` fájlokat,
* megkeresi a `Received Blueprint` sorokat,
* kiszedi a megtalált Blueprint neveket,
* kiszűri a duplikációkat,
* letölti a Star Citizen Wiki blueprint adatbázist,
* összeveti a saját listáddal,
* megmutatja a recepthez szükséges anyagokat,
* kiírja, melyik anyag mire kell az adott blueprinten belül,
* ha az API tudja, megmutatja, melyik quest / mission adja a Blueprintet.

---

**4. Mit látsz a táblában?**

A fő táblában ezek a fontos oszlopok vannak:

* Blueprint név
* Wiki státusz
* Elkészülő item
* Típus
* Anyagok / mennyiség
* Mire kell
* Craft idő
* Unlock
* Log találat

Ha egy sorra rákattintasz, felül megnyílik a **Blueprint részletek** panel.

Ott láthatod:

* mit craftol a Blueprint,
* milyen alapanyagok kellenek hozzá,
* mennyi kell belőlük,
* az anyag melyik alkatrészhez / részhez kell,
* melyik quest adhatja,
* hol vehető fel, ha az API tudja,
* milyen rendszerhez / factionhöz / reputációhoz tartozik, ha van ilyen adat.

Fontos: ha valahol azt írja, hogy nincs adat, az nem azt jelenti, hogy biztosan nincs ilyen feltétel. Csak azt jelenti, hogy a Wiki API nem adott vissza hozzá adatot.

---

**5. Mentés és betöltés**

A program tud helyi mentést készíteni.

* **Helyi mentés:** elmenti az aktuális listát a böngésződbe.
* **Mentés betöltése:** visszatölti a korábban mentett listát.

Ez a mentés a böngésző `localStorage` részébe kerül.

Nem a Star Citizen mappába ír.

---

**6. Ha nem tölt be a Wiki adatbázis**

Ha a böngésző blokkolja az API lekérést, indítsd helyi szerverről.

A HTML fájl mappájában nyiss parancssort, majd írd be:

`python -m http.server 8000`

Ezután böngészőben nyisd meg:

`http://localhost:8000/sc_blueprint_log_extractor_recipe_materials_quest_details_clean.html`

---

**7. Biztonság**

A program:

* csak logfájlokat olvas,
* nem törli a logokat,
* nem ír a Star Citizen mappába,
* nem módosít játékfájlokat,
* nem nyúl a játék memóriájához,
* nem futtat cheat jellegű műveletet,
* nem küldi el a logjaidat sehova.

A Wiki API-t csak a blueprint adatbázis lekérésére használja.

Ha teljesen biztosra akarsz menni, másold ki a `logbackups` mappát külön helyre, és a programban azt válaszd ki.

---

## English Guide

**1. Open the file**

Open the HTML file in your browser.

Recommended browsers:

* Chrome
* Edge

No installation is required. It is just a single HTML file.

---

**2. Select your log folder**

Click the **Select Folder** button.

Select this folder:

`Roberts Space Industries\StarCitizen\LIVE\logbackups`

Example full path:

`D:\Roberts Space Industries\StarCitizen\LIVE\logbackups`

---

**3. What does it do automatically?**

After selecting the folder, the tool will:

* scan your `.log` files,
* search for `Received Blueprint` lines,
* extract the Blueprint names,
* remove duplicates,
* download the Star Citizen Wiki blueprint database,
* compare your list against the Wiki data,
* show the required crafting materials,
* show what each material is used for inside the blueprint,
* show which quest / mission can unlock the Blueprint, if the API has that data.

---

**4. What will you see in the table?**

The main table shows:

* Blueprint name
* Wiki status
* Crafted item
* Type
* Materials / amount
* Used for
* Craft time
* Unlock
* Log match

If you click a row, the **Blueprint Details** panel opens at the top.

There you can see:

* what the Blueprint crafts,
* which materials are required,
* how much material is required,
* what each material is used for,
* which quest may unlock it,
* where the quest can be accepted, if the API knows it,
* which system / faction / reputation level is connected to it, if available.

Important: if something says “no data”, it does not mean the condition definitely does not exist. It only means the Wiki API did not return data for that field.

---

**5. Save and load**

The tool supports local saving.

* **Local Save:** saves the current list into your browser.
* **Load Save:** loads the previously saved list.

This uses your browser’s `localStorage`.

It does not write into the Star Citizen folder.

---

**6. If the Wiki database does not load**

If the browser blocks the API request, run it through a local server.

Open a command prompt in the same folder as the HTML file and run:

`python -m http.server 8000`

Then open this in your browser:

`http://localhost:8000/sc_blueprint_log_extractor_recipe_materials_quest_details_clean.html`

---

**7. Safety**

The tool:

* only reads log files,
* does not delete logs,
* does not write into the Star Citizen folder,
* does not modify game files,
* does not touch game memory,
* does not perform cheat-like actions,
* does not upload your logs anywhere.

The Wiki API is only used to download blueprint database information.

For extra safety, copy your `logbackups` folder somewhere else first, then select that copied folder in the tool.
