# Alap AI példa Azure-ban

Manapság a Mesterséges Intelligencia az egyik legfelkapottabb témakör. Emellett minden felhőszolgáltató igyekszik a saját AI szolgáltatásait minél jobban népszerűsíteni. Az Azure is ezen cégek közé tartozik, így én is úgy gondoltam, hogy érdemes lenne egy kis bevezetőt írni az Azure AI szolgáltatásairól.

## Azure AI

Az Azure AI egy olyan felhőalapú szolgáltatás, amely lehetővé teszi a fejlesztők számára, hogy könnyedén integrálják az AI-t a saját alkalmazásaikba. Az Azure AI szolgáltatások között megtalálhatóak a következők:

- Azure Cognitive Services
- Azure Machine Learning
- Azure Bot Service
- Azure Databricks
- Azure OpenAI
- Azure OpenAI Studio

Ezen szolgáltatások segítségével a fejlesztők képesek lehetnek például beszéd- és képfelismerésre, valamint gépi tanulásra alapozott alkalmazásokat készíteni.

Mi jelenleg az Azure OpenAI-t fogjuk megvizsgálni. Ez az amivel a leggyorsabban és legkönnyebben lehet elkezdeni.

## Azure Cognitive Services

Az Azure Cognitive Services egy olyan felhőalapú szolgáltatás, amely lehetővé teszi a fejlesztők számára, hogy könnyedén integrálják az AI-t a saját alkalmazásaikba. Az Azure Cognitive Services szolgáltatások között megtalálhatóak a következők:

- Vision
- Speech
- Language
- Decision
- Web Search

Ezen szolgáltatások segítségével a fejlesztők képesek lehetnek például beszéd- és képfelismerésre, valamint gépi tanulásra alapozott alkalmazásokat készíteni.

## Hogyan kezdjük el?

Azure-ban a legegyszerűbb eszközünk, ahol el tudjuk kezdeni, az [Azure OpenAI Studio](https://oai.azure.com/).

Az Azure OpenAI Studio egy olyan felhőalapú szolgáltatás, amely lehetővé teszi a fejlesztők számára, hogy könnyedén integrálják az AI-t a saját alkalmazásaikba. Az Azure OpenAI Studio szolgáltatások.

Ez az Azure AI Foundry része, amely egy olyan platform, amely lehetővé teszi a cégek számára, hogy könnyedén integrálják az AI-t a saját alkalmazásaikba. Itt találunk nagy nyelvi modelleket (LLM) és egyéb AI eszközöket, amelyek segítségével a fejlesztők képesek lehetnek például beszéd- és képfelismerésre, valamint gépi tanulásra alapozott alkalmazásokat készíteni.

A teljes felület már magyarul is elérhető, így könnyedén navigálhatunk rajta.

Itt néhány egyszerű beállítást követően már el is kezdhetjük az AI modellek fejlesztését. Az Azure OpenAI Studio egy teljesen ingyenes eszköz, amely lehetővé teszi a fejlesztők számára, hogy könnyedén készítsenek és teszteljenek AI modelleket.

Megjegyzés: Az AI stúdióban hasznélt erőforrások és szolgáltatások naghyrésze fizetsetős, így figyeljün kazok áraira és használatára.

Tehát az Azure OpenAI Studio-ban találjuk a különböző OpenAI modelleket, amelyeket az Azure Cognitive Services nyújt. Az egyes modellek használatához csak egy kattintásra van szükség, és már használhatjuk is azokat.

Ahhoz, hogy ezeket a modelleket használni tudjiuk, létre kell hoznunk egy Deployment-et. Ezt a Deployment-et aztán egy API-n keresztül tudjuk elérni, és használni a kiválasztott modelleket.

### Deployment (üzemelő példányok) létrehozása

1. Az Azure OpenAI Studio-ban kattintsunk a Üzemelő példányok menüpontra.
2. Kattintsunk a **+ Modell üzembe helyezése**, majd a **Alapmodell üzembe helyezése** gombra.
3. Válasszuk ki a kívánt modelt (pl.: gpt-4o), majd kattintsunk a **Megerősítése** gombra.

![Deployment létrehozása 1](./images/deploy-model.png)

4. Adjunk neki egy nevet.
5. Állítsuk be az egyéb paramétereket.
6. Kattintsunk a **Üzembe helyezés** gombra.

![Deployment létrehozása 2](./images/create-deployment.png)

![Minden Deployment](./images/all-deployment.png)

### Chat játszótér

Ha van egy Deploymentünk, akkor már használhatjuk is az adott modelt. Az Azure OpenAI Studio-ban található egy Chat játszótér, ahol kipróbálhatjuk az adott modelleket.

Ez így használhatjuk:

1. Az Azure OpenAI Studio-ban kattintsunk a Chat menüpontra.
2. Jobb oldalon, a **Üzembe helyezés** részben válasszuk ki a a modellt.
3. A képernyő közepén lévő chat ablakban írjuk be a kérdéseinket.

![Chat játszótér](./images/chat-playground.png)

#### Több stílusú beszélgetés

Több beszélgetési stílusban is kommunikálhatunk az AI-val. Ehhez a **Give the model instructions and context** részben adnunk kell instrukciókat a nyelvi modell számára. Ez esetben ugyanazon kérdésre különböző válaszokat kaphatunk.

**Kérdés:** Hogyan kezdjem el az Azure tanulást?

**Stílus lerások**

- Te egy tapasztalt informatikai szakértő vagy. Csak a tényekre támaszkodj.
- Te egy egyetemi hallgató vagy, aki szinte csak szlengekben válaszol.
- Te egy pesszimista ember vagy, aki már nem hajlandó újat tanulni.

Most próbáljuk ki!

## Saját adatforrás használata

Az Azure Cognitive Services lehetőséget ad arra, hogy saját adatforrásokat is használjunk. Ehhez az Azure OpenAI Studio-ban a **Data** menüpontra kell kattintanunk, és ott tudjuk hozzáadni a saját adatforrásainkat. Ez azért lehet nekünk hasznos, mivel ez esetben nem kell 100%-ban az AI által talált adatokra hagyatkoznunk, illetve egyéb előnyei is vannak:

- Az AI a mi adatainkon dolgozik, így nem kell aggódnunk a biztonság miatt.
- Az AI a mi adatainkon dolgozik. (Ez lehet a saját dokumentációnk, vagy akár a saját képeink.)
- Csökkenthetjük az AI-ra jellemző hallucinációt.
- Az AI válaszai a mi adatainkon alapulnak, így pontosabbak lehetnek.

Ez lehet akár md fájl is, ami a kódunk, alkalmazásunk dokumentációját tartalmazza. Az AI így könnyedén válaszolhat a felhasználó kérdéseire.

## Példa Azure OpenAI használatára

Az alábbi példában egy egyszerű chatbotot fogunk készíteni, amely képes válaszolni a felhasználó kérdéseire.

Ehhez az alábbi erőforrások szükségesek:

- Azure OpenAI
- Azure tárfiók (Azure Storage account)
- Azure AI keresőszolgáltatás (Azure AI Search)

### 1. Azure OpenAI létrehozása

1. Lépjünk be az Azure Portalba.
2. Kattintsunk a **Erőforrás létrehozása** gombra.
3. Keressük ráa az **Azure OpenAI** lehetőségre.
4. Kattintsunk a **Létrehozás** gombra.
5. Töltsük ki a szükséges mezőket.
   - Tarifacsomag: Standard S0
6. A **Felülvizsgálat és létrehozás** oldalon kattintsunk a **Létrehozás** gombra kattintva hozzuk létre az erőforrást.

### 2. Azure tárfiók létrehozása

1. Lépjünk be az Azure Portalba.
2. Kattintsunk a **Erőforrás létrehozása** gombra.
3. Keressük meg az **Tárolás** kategóriát.
4. Válasszuk ki a **Tárfiók** lehetőséget.
5. Kattintsunk a **Létrehozás** gombra.
6. Töltsük ki a szükséges mezőket.
   - Redundancia: LRS
7. A **Felülvizsgálat és létrehozás** oldalon kattintsunk a **Létrehozás** gombra kattintva hozzuk létre az erőforrást.
8. Nyissuk meg a tárfiókunkat, és kattintsunk a **Tárolók** menüpontra.
9. Hozzunk létre egy új tárolót.
   - Név: ai-forras
   - Névtelen hozzáférés: Privát
10. Kattintsunk az `ai-forras` tárolóra, majd töltsük fel a jsonl fájlt, amelyet az AI szolgáltatásunknak szeretnénk használni, mint adatforrás.

### 3. Azure AI keresőszolgáltatás létrehozása

1. Lépjünk be az Azure Portalba.
2. Kattintsunk a **Erőforrás létrehozása** gombra.
3. Keressünk rá a **Azure AI Search** lehetőségre.
4. Kattints a **Létrehozás** gombra.
5. Töltsük ki a szükséges mezőket.
   - Név: mentor-ai-search
   - Hely legyen ugyanaz, mint a tárfiókunknak
   - Tarifacsomag: B (Alap)
6. Megjegyzés: Az AI Search ezen tarifa csomagja nagyjából **havi 27 000 Forint**ba kerül. (Ezért csak akkor érdemes használni, ha valóban szükségünk van rá.)
7. A **Felülvizsgálat és létrehozás** oldalon kattintsunk a **Létrehozás** gombra kattintva hozzuk létre az erőforrást.

### 4. Saját adatforrás használata Chatbothoz Azure OpenAI Studio-ban

1. Lépjünk be az Azure OpenAI Studio-ba.
2. Kattintsunk a **Csevegés** menüpontra.
3. A jobb oldalon, a **Beállítás** részben válasszuk ki a Modellt.
4. A bal olalon, a **Beállítás** részben válasszuk ki a **Saját adatok hozzáadása** lehetőséget.
5. Kattintsunk az **Adatforrás hozzáadása** gombra.
6. Select a data source: **Azure Blob Storage**
7. Blob storage account: Válasszuk ki az előbb létrehozott tárfiókunkat.
8. Container: Válasszuk ki az `ai-forras` tárolót.
9. Azure AI Search-nél válasszuk ki a **mentor-ai-search**-t.
10. Enter the index name: dokumentum
11. Indexelő ütemezése: **Hourly**
12. Vektor keresés hozzáadása ehhez a keresési erőforráshoz:

- **Igen**
- Modell beágyazása: **text-embedding-ada-002**

13. Kattintsunk a **Következő** gombra.
14. Keresés típusa: **Vektor**
15. Válasszon méretet: **1024**
16. Kattintsunk a **Következő** gombra.
17. A **Azure-erőforrás hitelesítésének típusa** résznél válasszuk az **API Key** lehetőséget.
18. Kattintsunk a **Következő** gombra.
19. Várjuk meg amíg a beállítások ellenőrzésre kerülnek.
20. Összegző képernyőn kattintsunk a **Mentés és bezárás** gombra.
21. Pár perc múlva az adatforrásunk elérhető lesz a Chatben.

### 5. Webalkalmazás létrehozása Chatbothoz Azure-ban

1. Az előző pontban létrehozott Chat játszótérben kattintsunk a **Üzembe helyezés** gombra.
2. Válasszuk a **...webalkalmazásként** lehetőséget.
3. Töltsük ki a szükséges mezőket.
   - Name: mentor-chatbot
   - Subscription: Válasszuk ki a megfelelő előfizetésünket.
   - Resource group: Válasszuk ki a megfelelő erőforrás csoportunkat.
   - Location: Válasszuk ki a megfelelő régiót.
   - Pricing plan: B1
   - Csevegési előzmények engedélyezése a webalkalmazásban: Igen (Ekkor egy Cosmos DB is létrejön a háttérben, amelyben tárolni fogjuk a csevegési előzményeket. - Ez költséges lehet, így ha nem szeretnénk, akkor válasszuk a **Nem** lehetőséget.)
4. Kattintsunk a **Üzembe helyezés** gombra. (nagyjából 10-15 perc alatt elkészül)
   ![Webalkalmazás üzembe helyezése](./images/webalkalmazas-deploy.png)

### 6. Felhasználói azonosítás beállítása

Amíg a webalkalmazásunk készül, addig beállíthatjuk a felhasználói azonosítást. Ez azért fontos, mert így csak azok férhetnek hozzá a webalkalmazásunkhoz, akiknek engedélyeztük.

1. Lépjünk be az Azure Portalba.
2. Kattintsunk a **Webalkalmazások** menüpontra.
3. Kattintsunk a **mentor-chatbot** webalkalmazásunkra.
4. A bal oldalon válasszuk a **Beállítások** menüpontot.
5. Kattintsunk a **Hitelesítés** menüpontra.
6. Kattintsunk a **Identitásszolgáltató hozzáadása** gombra.
7. Válasszuk ki a **Microsoft** lehetőséget.
8. Itt az alábbi beállításokat kell megadnunk:
   - Munkaerő-konfiguráció (aktuális bérlő) Alkalmazottak és üzleti vendégek kezelése
   - Alkalmazásregisztráció típusa: **Adja meg egy meglévő alkalmazás-regisztráció részleteit**
   - Client ID: Adjuk meg a megfeleő alkalmazás Client ID-ját.
   - Client Secret: Adjuk meg a megfeleő alkalmazás Client Secret-jét.
   - Kiállító URL-címe: https://sts.windows.net/{tenant id}/v2.0
   - Ügyfélalkalmazási követelmény: Csak magából az alkalmazásból érkező kérelmek engedélyezése
   - Identitáskövetelmény: Bármely identitásból érkező kérelmek engedélyezése
   - Bérlői követelmény: Csak a kibocsátó bérlőről érkező kérelmek engedélyezése
   - Hozzáférés korlátozása: Hitelesítés megkövetelése
   - Nem hitelesített kérelmek: HTTP 302 Found átirányítása: webhelyek esetén ajánlott
   - Jogkivonat-tároló: Igen
9. Kattintsunk a **Következő: Engedélyek** gombra.

### 7. Alkalmazás tesztelése

1. Lépjünk be az Azure Portalba.
2. Kattintsunk a **Webalkalmazások** menüpontra.
3. Kattintsunk a **mentor-chatbot** webalkalmazásunkra.
4. Kattintsunk a **Webalkalmazás URL** linkre.
5. A megnyíló ablakban kattintsunk a **Sign in with Microsoft** gombra.
6. Kezdjünk el beszélgetni az AI-val.

![AI Chat Webapp](./images/ai-chat-webapp.png)

### 8. Példa kérdések 'prompt'

1. Ma már minden a mesterséges intelligenciáról (AI) szól: Mit jelent ez számunkra?
2. Hogyan telepítek NodeJs 20-at Linuxra?
3. Hogyan telepítek Python3-at Windowsra?
4. Mi az LLM és milyen LLM-eket ismerünk?
5. Milyen eszközöket használhatunk LLM-alapú megoldások fejlesztésére?
6. Mi a Webhook alkalmazási területei?
7. Hogyan néz ki egy Cloud Administrator első napja?
8. Milyen segédanyagokat találok az Azure témájú képzésekhez?
9. Hogyan tudok kapcsolatot létesíteni az Azure Pipeline és a GitHub között?
10. Hasonlítsd össze a következő eszközöket: Azure DevOps és GitHub?

## Asszisztens létrehozása saját adatforrással

Azure OpenAI Studio-ban lehetőségünk van saját adatforrások használatára. Ezt az előző pontokban már részleteztük, most pedig egy példán keresztül mutatjuk be, hogyan hozhatunk létre egy chat alkalmazást, amely képes válaszolni a felhasználó kérdéseire.

A jelenleg nagyon divatos asszisztenst it is létrehozhatjuk, amely képes válaszolni a felhasználó kérdéseire. Ezt még egyszerűbben is megtehetjük, mint a Chat esetében. Ráadásul dokumentumainkat is felhasználhatjuk az AI válaszainak kialakításához. Ezeket a dokumentumokat az Azure OpenAI Studio-ban a **Data Files** menüpontban tudjuk feltölteni. Majd egy vektor adatbázist hozhatunk létre, amelyben az AI keresni fogja a válaszokat.

Most nézzük ennek lépéseit:

1. Lépjünk be az Azure OpenAI Studio-ba. https://oai.azure.com/
2. Kattintsunk a **Assistant** menüpontra.
3. A jobb oldalon, a **Configuration** részben válasszuk ki a Deploymentet. (Pl.: alap-gpt35-turbo)
4. Majd kattintsunk a **+ Create an assistant** gombra.
5. Adjunk neki egy nevet. (Pl.: mentor-asszisztens)
6. Instructions részben adhatunk instrukciókat az AI-nek. (Pl.: Te egy tapasztalt informatikai szakértő vagy. Csak a tényekre támaszkodj.)
7. Tools részben kapcsoljuk be a **File search** lehetőséget.
8. Kattintsunk a **+ Add vector store** gombra.
9. Adjunk neki egy nevet. (Pl.: mentor-vektor)
10. görgessünk lejjebb és kapcsoljuk be a **Select local files** lehetőséget.
11. Keressük meg a dokumentációinkat, és jelöljük ki azokat. Majd kezdjük meg a feltöltést.
12. Kattintsunk a **Upload and add** gombra.
13. Várjuk meg amíg a feltöltés befejeződik.
14. Vektor adatbázis állapotának ellnőrzése: A bal oldalon, a **Vector stores** részben ellenőrizzük, hogy a vektor adatbázisunk állapota **Completed**-re változott-e.
15. Navigéljunk vissza az **Assistant** menüpontra.
16. Teszteljük az asszisztenst.

**Példa kérdések 'prompt'**

1. Ma már minden a mesterséges intelligenciáról (AI) szól: Mit jelent ez számunkra?
2. Hogyan telepítek NodeJs 20-at Linuxra?
3. Hogyan telepítek Python3-at Windowsra?
4. Mi az LLM és milyen LLM-eket ismerünk?
5. Milyen eszközöket használhatunk LLM-alapú megoldások fejlesztésére?
6. Mi a Webhook alkalmazási területei?
7. Hogyan néz ki egy Cloud Administrator első napja?
8. Milyen segédanyagokat találok az Azure témájú képzésekhez?
9. Hogyan tudok kapcsolatot létesíteni az Azure Pipeline és a GitHub között?
10. Hasonlítsd össze a következő eszközöket: Azure DevOps és GitHub?
