# Threat Intelligence Essentials — študijné poznámky

Poznámky spracúvajú všetkých 10 modulov kurzu TIEv1. Sú určené na učenie, preto sa sústreďujú na význam pojmov, vzťahy medzi nimi a praktické použitie, nie na doslovný prepis slidov.

## Rýchla mapa kurzu

1. Základy threat intelligence (TI), životný cyklus a zrelosť
2. Typy TI a ich použitie
3. Kybernetické hrozby, aktéri, APT, Kill Chain a IoC
4. Zber, normalizácia a obohacovanie dát
5. Threat Intelligence Platform (TIP)
6. Analýza, prioritizácia, profilovanie a atribúcia
7. Threat hunting a detekcia
8. Zdieľanie a spolupráca
9. TI v incident response (IR)
10. Budúce trendy a kontinuálne vzdelávanie

---

# Modul 1 — Úvod do Threat Intelligence

## Čo je Threat Intelligence

**Threat intelligence (TI, spravodajstvo o hrozbách)** je kontextový proces založený na dátach: zhromažďuje, analyzuje a interpretuje informácie o potenciálnych hrozbách tak, aby organizácia vedela uprednostniť riziká a konať.

Najdôležitejšie slovo je **actionable — použiteľná na rozhodnutie alebo akciu**. Samotný zoznam škodlivých IP adries ešte nemusí byť inteligencia.

### Dáta → informácia → inteligencia

- **Dáta:** surové fakty bez dostatočného kontextu, napr. IP adresa alebo hash.
- **Informácia:** dáta usporiadané tak, že niečo opisujú, napr. IP bola spojená s phishingovou kampaňou.
- **Inteligencia:** analyzovaná a pre organizáciu relevantná informácia, ktorá vedie ku konkrétnej akcii, napr. IP komunikuje s naším serverom a patrí aktérovi útočiacemu na naše odvetvie — spojenie zablokujeme a preveríme hostiteľa.

## Kľúčové pojmy

- **Threat actor:** jednotlivec alebo skupina schopná spôsobiť škodu; môže ísť aj o neúmyselného insidera.
- **TTP (Tactics, Techniques and Procedures):** ciele, metódy, správanie a konkrétne postupy aktéra.
- **IoC (Indicator of Compromise):** stopa možnej kompromitácie, napr. IP, doména, URL, hash, súbor či neobvyklý záznam v registri.
- **APT (Advanced Persistent Threat):** dobre financovaný, sofistikovaný a vytrvalý aktér, ktorý sa snaží dlhodobo zostať neodhalený.
- **Dark web:** časť internetu prístupná špeciálnymi nástrojmi; aktéri ju používajú na komunikáciu, predaj dát a plánovanie.
- **Threat landscape:** meniaci sa súbor hrozieb, rizík a technológií relevantných pre konkrétnu organizáciu alebo odvetvie.

## Prečo je TI dôležitá

- umožňuje proaktívne opravovať zraniteľnosti a zmenšovať attack surface,
- zrýchľuje detekciu, containment a obnovu pri incidente,
- zlepšuje rozhodovanie, rozpočet a plánovanie bezpečnosti,
- pomáha prioritizovať riziká podľa reálnej hrozby,
- zdieľaním vytvára včasné varovanie aj pre iné organizácie.

Tradičná bezpečnosť a TI sa dopĺňajú. Tradičné kontroly predovšetkým chránia systémy; TI dodáva širší a dopredu orientovaný kontext, podľa ktorého sa kontroly upravujú.

## Životný cyklus TI

1. **Plánovanie:** zistenie potrieb stakeholderov, vytvorenie intelligence requirements a pridelenie zdrojov.
2. **Zber:** výber relevantných interných a externých zdrojov a príjem surových dát.
3. **Spracovanie:** čistenie, normalizácia, deduplikácia a štruktúrovanie.
4. **Analýza:** doplnenie kontextu, korelácia, tvorba záverov a odporúčaní.
5. **Diseminácia:** doručenie správneho výstupu správnemu publiku a v správnom čase.
6. **Spätná väzba:** overenie využitia a zlepšenie ďalšieho cyklu.

Cyklus nezačína feedom, ale **otázkou organizácie**. Bez nej sa tím ľahko utopí v dátach.

### Intelligence requirements a kvalita výstupu

Požiadavka má pomenovať rozhodnutie, publikum, časový horizont a hranice zberu. Príklad: „Ktoré ransomware skupiny pravdepodobne zaútočia na naše zdravotnícke pracoviská v najbližšom štvrťroku a aké kontroly máme posilniť?“ Je lepšia než neurčité „zistite niečo o ransomware“.

Pri každom závere uveď:

- **zdroj a čas** získania informácie,
- **relevanciu** pre aktíva, región a odvetvie,
- **confidence** (nízka/stredná/vysoká) a čo ju ovplyvňuje,
- **pravdepodobnosť** udalosti — nie je to to isté ako confidence analytika,
- predpoklady, informačné medzery a alternatívne vysvetlenia,
- odporúčanú akciu, prioritu, vlastníka a čas na vykonanie.

Inteligencia môže byť presná, ale doručená neskoro; aktuálna, ale nerelevantná; relevantná, ale bez odporúčania. Vo všetkých troch prípadoch má nízku operačnú hodnotu.

## Model zrelosti

1. **Initial:** reaktívne a nekonzistentné aktivity bez formálnych procesov.
2. **Foundational:** štandardné postupy a jednoduchá interná analýza.
3. **Defined:** formálne politiky, integrácia do hlavných bezpečnostných funkcií, znalosť relevantných TTP.
4. **Managed:** špecializovaný tím, široká integrácia, organizácia TI prijíma, tvorí aj zdieľa.
5. **Optimized:** pokročilá automatizácia/ML, predikcia a aktívny prínos komunite.

## Roly a použitia

- **TI analytik:** zbiera a analyzuje dáta, tvorí profily a actionable výstupy.
- **Threat researcher:** skúma nové kampane, aktérov, malware a zraniteľnosti.
- **Threat hunter:** aktívne hľadá skryté hrozby, ktoré obišli existujúce kontroly.

Použitia: obrana pred phishingom a ransomware, ochrana dodávateľského reťazca, detekcia finančných podvodov a sledovanie zero-day zraniteľností.

## Frameworky, štandardy a meranie

- **MITRE ATT&CK:** vedomostná báza taktík a techník zo skutočných útokov.
- **Cyber Kill Chain:** lineárne fázy útoku; dobrá na pochopenie, kde útok prerušiť.
- **STIX:** štruktúrovaný formát reprezentácie TI.
- **TAXII:** protokol na automatizovanú výmenu TI (často prenáša STIX).
- **ODNI Cyber Threat Framework:** spoločná terminológia na opis aktérov a aktivít.

KPI: podiel odhalených/zmiernených hrozieb, mean time to decision, false-positive rate, využitie inteligencie, úspešnosť huntov, nové IoC/TTP/detekcie, incidenty spustené inteligenciou a zraniteľnosti opravené vďaka TI.

---

# Modul 2 — Typy Threat Intelligence

## Štyri základné typy

| Typ | Horizont a publikum | Obsah | Príklad použitia |
|---|---|---|---|
| **Strategická** | dlhodobý; vedenie | minimum technických detailov, biznis a geopolitické riziká | rozhodovanie o akvizícii alebo vstupe na trh |
| **Operatívna** | krátky až stredný; bezpečnostné tímy | konkrétni aktéri, kampane, ciele a úmysly | sledovanie kampane a tvorba profilu aktéra |
| **Taktická** | krátkodobý; SOC/obrana | TTP a okamžité úpravy kontrol | zmena firewallu alebo detekčných pravidiel |
| **Technická** | technickí špecialisti | malware, exploity, IP, domény, hash hodnoty | malware analýza a výskum zraniteľnosti |

Pozor: slidy používajú pri časových horizontoch miestami nejednotné označenia. Na skúške je podstatnejšie **publikum, miera technického detailu a rozhodnutie**, ktoré výstup podporuje.

## Zdroje a tvorba TI

Všeobecné OSINT zdroje: bezpečnostné médiá, vládne weby, výskumníci a služby ako urlscan.io, ANY.RUN či OPSWAT. Veľkí producenti (napr. Mandiant, CrowdStrike, Unit 42, Cisco Talos) spájajú globálnu telemetriu, incidenty, automatizáciu a ľudský výskum.

Proces: **široký zber → agregácia → analýza → vytvorenie TI → distribúcia → spätná väzba a iterácia**.

## Regulácia, vulnerability management a risk management

- GDPR a podobné pravidlá obmedzujú zber, uchovávanie a zdieľanie osobných dát.
- Breach-reporting pravidlá určujú, čo a dokedy treba oznámiť.
- Organizácia musí preukázať due care, data governance, zákonný účel a primeranú retenciu.
- TI dopĺňa CVSS o realitu: je zraniteľnosť zneužívaná, existuje exploit, používa zasiahnutý produkt naša organizácia a cieli aktér na naše odvetvie?
- V risk managemente umožňuje presnejšie vyhodnotiť dodávateľské riziko, priority patchovania, monitorovanie a poistné krytie.

**Geopolitická TI** skúma vplyv politiky, ekonomiky a regiónov, najmä nation-state aktérov. **Odvetvová TI** sa sústreďuje na špecifiká sektora, napr. kritickú infraštruktúru alebo zdravotné údaje.

### Ako zvoliť správny typ výstupu

- Vedenie potrebuje krátky scenár, pravdepodobnosť, finančný/prevádzkový dopad a možnosti rozhodnutia.
- Risk alebo compliance tím potrebuje väzbu na riziká, reguláciu, vlastníkov a termíny nápravy.
- SOC potrebuje aktuálne IoC/TTP, detekčný postup, confidence, kritickosť a eskalačné pravidlo.
- Malware analytik potrebuje technické artefakty, behaviorálne pozorovania, vzorku a reprodukovateľný postup.

Rovnaké zistenie preto treba diseminovať vo viacerých podobách. Preklad technického rizika do biznis dopadu je základnou úlohou analytika, nie „zjednodušovaním“ inteligencie.

---

# Modul 3 — Cyber Threat Landscape

## Aktéri a motivácie

- **Nation-state:** geopolitická alebo ekonomická výhoda, špionáž a narušenie.
- **Kyberzločinci:** finančný zisk.
- **Hacktivisti:** politická alebo spoločenská zmena a publicita.
- **Insideri:** zisk, pomsta, zverejnenie dát alebo neúmyselná chyba.
- **Script kiddies:** zvedavosť, zábava alebo sociálne uznanie.

Aktuálne smery zahŕňajú AI malware a phishing, quishing cez QR kódy, TOAD/vishing, deepfakes, útoky na IoT a budúce riziko kvantového prelomenia dnešnej kryptografie.

## APT

APT vykonáva dlhý prieskum, cielene získava foothold, pohybuje sa laterálne, udržiava persistence, exfiltruje alebo ničí dáta a maskuje stopy. Používa phishing, zero-day, supply-chain kompromitáciu, credential theft a **living off the land** (zneužitie legitímnych nástrojov systému).

Obrana: threat hunting, behaviorálna analytika, kvalitný incident response, penetračné testy a robustné, otestované zálohy.

## Cyber Kill Chain

1. **Reconnaissance** — zber informácií o cieli.
2. **Weaponization** — príprava exploitu/payloadu.
3. **Delivery** — doručenie payloadu.
4. **Exploitation** — zneužitie chyby a získanie footholdu.
5. **Installation** — malware, backdoor, rootkit alebo iná persistence.
6. **Command and Control (C2)** — komunikačný kanál útočníka.
7. **Actions on Objectives** — krádež, šifrovanie, sabotáž či ďalšie šírenie.

Cloudová varianta často začína chybnou konfiguráciou, verejným úložiskom alebo ukradnutým access key. Mobilná varianta využíva smishing, SIM swap, škodlivú aplikáciu či kompromitovaný MDM.

## IoC a vulnerability management

IoC sú digitálne stopy po aktivite aktéra. Majú sa korelovať s kontextom, nie slepo blokovať. Vulnerability management potrebuje úplný inventár, logické skupiny aktív, pravidelné a autentizované skeny, úplný rozsah sietí a prioritizáciu podľa reálneho zneužívania.

Emerging tech rozširuje attack surface: blockchain a smart kontrakty, 5G a DDoS, edge bez dostatočnej telemetrie, robotika s fyzickým dopadom, AR/VR, biometria a automatizované APT.

### Príklady aktérov zo slidov

- **Fancy Bear:** nation-state profil; prieskum sietí, zneužívanie zariadení a persistence cez špecializovaný malware.
- **Scattered Spider:** sociálne inžinierstvo, SIM swapping/MFA manipulácia, legitímne RMM nástroje a ransomware partnerstvá.
- **OilRig:** phishing/BEC alebo supply-chain vektor, credential theft, lateral movement a DNS tunneling pre C2 či exfiltráciu.

Názvy a atribúcie skupín sa medzi vendormi líšia. Pri profile preto ukladaj **aliases** a oddeľuj potvrdené fakty od analytického odhadu.

---

# Modul 4 — Zber dát a zdroje TI

## Výber feedu

Hodnoť:

- relevanciu a kvalitu pred množstvom,
- reputáciu a transparentnosť zdroja,
- frekvenciu aktualizácie (denne je minimum, real-time je vhodnejší),
- veľkosť a rozmanitosť senzorickej siete,
- vlastný výskum a partnerstvá poskytovateľa,
- dostupnosť, latenciu, duplicity a mieru false positives.

Príklady zdrojov: CIS/MS-ISAC, AlienVault OTX a VirusTotal.

## Spôsoby zberu

- **E-mail/RSS:** jednoduché, ale skôr manuálne.
- **API:** automatické dotazy na domény, IP, URL či hash.
- **TAXII:** štandardizovaný obojsmerný push/pull medzi platformami.
- **OSINT:** verejné weby, sociálne siete, fóra, paste sites a registre.
- **Bulk collection:** scraping/crawling, API odbery, sieťové senzory, logy, cloud storage a databázové exporty.

### Aktívny vs. pasívny zber

- **Aktívny:** honeypoty alebo priame zapojenie; bohatšie a rýchlejšie dáta, ale vyššie právne, technické a operačné riziko a možnosť odhalenia aktérom.
- **Pasívny:** pozorovanie verejných zdrojov a analýza vzoriek; nižšie riziko, ale menej detailov a často slabší kontext.

## Spracovanie dát

1. **Normalizácia:** jednotné formáty dátumu, IP, domén, názvov a schém.
2. **Deduplikácia a filtrácia:** odstránenie opakovaní, šumu a nerelevantných položiek.
3. **Enrichment:** reputácia, geolokácia, WHOIS/DNS, malware family, CVE, actor a MITRE mapping.
4. **Korelácia:** spájanie udalostí a zdrojov do kampane alebo profilu.
5. **Extrakcia actionable intelligence:** priorita, dôvera, dopad, odporúčaná akcia a vlastník.

Riziká bulk zberu: náklady na storage/compute, slabá kvalita, bias, poškodené dáta, bezpečnosť úložiska a porušenie podmienok služby alebo súkromia. Rešpektuj suverenitu štátov, súhlas, rozdiel medzi verejnými a súkromnými dátami a konflikt záujmov.

### Bulk collection — detailný checklist

- **Úložisko a lokalita:** právne pravidlá môžu určovať, v ktorej krajine možno dáta uložiť; osobné údaje anonymizuj a chráň RBAC.
- **Sieť a výkon:** odhadni bandwidth, rýchlosť ingestion, API rate limits, latenciu, kapacitu fronty a obdobie výpadku.
- **Data hoarding:** zbieraj iba to, čo odpovedá na požiadavku; nastav retenciu a automatické vymazanie.
- **Provenance:** zachovaj zdroj, čas, licenciu, TLP/sharing obmedzenia a históriu transformácií.
- **Integrita:** validuj schému, typy polí, timestamp a hash; poškodený vstup nemá potichu prejsť pipeline.
- **Bezpečnosť:** neotváraj vzorky na produkčnom zariadení, používaj sandbox a oddelené úložisko.

### Normalizácia a enrichment — príklad

Surový záznam `evil.example` sa normalizuje ako doménový objekt so štandardným časom. Enrichment pridá DNS/WHOIS, reputáciu, TLS certifikát, súvisiace IP, pasívny DNS, malware family, kampane a ATT&CK techniky. Korelácia zistí komunikáciu interného hostiteľa s doménou. Až záver „hostiteľ X môže byť kompromitovaný; izolovať a preveriť proces Y“ je actionable intelligence.

Enrichment je iteratívny: **požiadavky → korelácia/obohatenie → ďalšia analýza → integrácia do SIEM/TIP → spätná väzba**. Príliš agresívna normalizácia môže odstrániť kontext, preto uchovaj aj pôvodnú hodnotu.

---

# Modul 5 — Threat Intelligence Platforms (TIP)

## Úloha a funkcie TIP

TIP centralizuje zber, ingestion feedov, normalizáciu, enrichment, koreláciu, prioritizáciu, vizualizáciu, reporting a zdieľanie TI. Integruje sa so SIEM, SOAR, EDR, firewally, vulnerability scannermi a ticketingom.

Tok: **collection → filtering → enrichment → processing → prioritization → trends/prediction → report/visualization → syndication → sharing/feedback**.

## Automation vs. orchestration

- **Automatizácia:** jedna úloha sa vykoná bez človeka, napr. obohatenie IP alebo blokovanie potvrdenej domény.
- **Orchestrácia:** koordinuje viac automatizovaných krokov a systémov v správnom poradí podľa playbooku.

Výsledkom má byť jednotný kontext incidentov, lepší situational awareness a rýchla náprava. Citlivé alebo deštruktívne rozhodnutia si majú ponechať human oversight.

## Výber a bezpečné nasadenie TIP

Hodnoť total cost of ownership, výkon a presnosť, podporu vendora, jednoduchú integráciu, customizáciu, škálovanie, cloud/on-prem kompatibilitu a kvalitu školenia. Proof of value testuj na reálnych scenároch a získaj spätnú väzbu viacerých tímov.

TIP má privilegovaný prístup, preto potrebuje RBAC, segmentáciu, audit, penetračné testy, change management a pravidelné integračné/health testy.

Riziká: echo chamber, chybná analýza, nedôvera, nesprávne priority, alert fatigue a automatická reakcia na false positive. Pomáha rozmanitosť zdrojov, quality control, tuning, spätná väzba a reverzibilné zmeny.

TIP podporuje hunting cez pokročilé vyhľadávanie, behaviorálnu analýzu, watchlisty, actor profiling a retrospektívnu analýzu. Reporting prispôsob publiku a rozprávaj jasný príbeh: čo sa deje, prečo je to relevantné, dopad a odporúčaná akcia.

### Praktický TIP use case

1. TIP prijme škodlivú doménu cez TAXII a deduplikuje ju.
2. Obohatí ju o reputáciu, passive DNS, certifikát a súvisiaci malware.
3. Koreluje ju s proxy/SIEM telemetriou a zistí interný kontakt.
4. Podľa confidence a kritickosti aktíva vytvorí incident v SOAR.
5. Playbook môže doménu zablokovať, izolovať endpoint a vyžiadať schválenie analytika.
6. Analytik potvrdí incident, pridá TTP/ATT&CK mapping a výsledok sa vráti do TIP.
7. Sanitizovaná inteligencia sa podľa pravidiel zdieľa partnerom.

**MISP** pracuje s events, attributes, objects, tags a galaxies; umožňuje feedy, korelácie a zdieľanie medzi inštanciami. **AlienVault OTX** združuje IoC do „pulses“ a poskytuje API/TAXII. Nástroj nie je náhradou za intelligence requirements ani ľudskú validáciu.

---

# Modul 6 — Analýza Threat Intelligence

## Analytické metódy

- **Text analysis:** získava vzory z neštruktúrovaného textu.
- **Exploratory analysis (EDA):** skúma dáta, anomálie a predpoklady pred modelovaním.
- **Diagnostic analysis:** vysvetľuje, prečo minulosť nastala.
- **Inferential analysis:** zo vzorky odvodzuje vlastnosti väčšej populácie.
- **Descriptive analysis:** sumarizuje priemer, medián, frekvencie a odchýlky.
- **Predictive analysis:** z histórie odhaduje budúce javy.
- **Network/graph analysis:** odhaľuje nezvyčajné spojenia, toky a vzťahy.

Praktický tok: **zber → čistenie → deskriptívna analýza → inferencia/korelácia → predikcia → actionable záver**.

## Analysis of Competing Hypotheses (ACH)

ACH porovnáva niekoľko alternatívnych vysvetlení voči rovnakým dôkazom. Analytik má aktívne hľadať dôkazy, ktoré hypotézu **vyvracajú**, zoradiť hypotézy podľa konzistencie a uviesť mieru istoty. Viac analytikov znižuje confirmation bias.

## IoC a TTP analýza

IoC analyzuj podľa frekvencie, času, lokality, reputácie, vzťahov a odľahlých hodnôt. TTP sa identifikujú z behaviorálnych vzorov, korelujú s minulými udalosťami, obohacujú cez TIP/MITRE a vedú k protiopatreniu.

Analytické hypotézy validuj emuláciou protivníka. Psychologická bezpečnosť a spolupráca s inými tímami znižujú bias a dopĺňajú biznis kontext.

## Prioritizácia rizík

- **CVSS:** technická závažnosť 0–10; base, temporal a environmental faktory.
- **OWASP risk rating:** pravdepodobnosť + technický/biznis dopad pre web/mobile.
- **FAIR:** scenár → frekvencia stratovej udalosti → veľkosť straty → celkové riziko.
- **VPR:** dynamická priorita nad CVSS podľa veku, exploit maturity, pokrytia produktov a threat contextu.

Samotné vysoké CVSS neznamená automaticky najvyššiu organizačnú prioritu.

## Profilovanie a atribúcia

Profil aktéra obsahuje cieľové odvetvia/regióny, motiváciu, TTP, používané nástroje, malware, IoC, infraštruktúru a časový pattern. Atribúcia využíva lingvistiku a štýl kódu, code reuse, opakované domény/servery a pattern of life. Výsledok vyjadruj s mierou dôvery; rovnaké nástroje môže používať viac skupín.

### Predictive vs. proactive TI

- **Prediktívna:** pozerá na historické dáta a modeluje pravdepodobný budúci útok.
- **Proaktívna:** už teraz aktívne hľadá a odstraňuje možné hrozby — scanning, audit, threat hunting, bug bounty.

Modely priebežne validuj, používaj interné aj externé dáta, krížovo overuj predikcie a nespoliehaj sa iba na automatizáciu.

### Pokročilé analytické doplnenia

- **Isolation Forest a One-Class SVM:** algoritmy na odhaľovanie odľahlých pozorovaní; výsledok závisí od kvalitného baseline a môže mať veľa false positives.
- **Sentiment/text mining:** môže zachytiť náladu, úmysel, dezinformačnú kampaň alebo skorú diskusiu o exploite na verejných kanáloch.
- **Graph analytics:** uzly predstavujú aktérov, infraštruktúru, malware či obete a hrany ich vzťahy; odhalí zdieľanú infraštruktúru a skryté kampane.
- **Prescriptive analysis:** po opise, vysvetlení a predikcii navrhuje, čo má organizácia urobiť.

### Minimálny profil aktéra

| Oblasť | Čo zachytiť |
|---|---|
| Identita | názov, aliases, možné väzby, confidence atribúcie |
| Motivácia | financie, špionáž, sabotáž, ideológia |
| Ciele | odvetvia, regióny, typy organizácií a aktív |
| Správanie | ATT&CK taktiky/techniky, attack paths, pracovný čas |
| Arzenál | malware, legitímne nástroje, exploity a infraštruktúra |
| Indikátory | IP, domény, URL, hash a host/network artefakty s časom platnosti |
| Obrana | dátové zdroje, detekčné pravidlá, mitigácie a hunt hypotézy |

---

# Modul 7 — Threat Hunting a detekcia

## Definícia a typy huntov

Threat hunting je proaktívne hľadanie skrytých hrozieb, ktoré unikli tradičným kontrolám, spojením technológie a ľudského úsudku.

- **Structured hunt:** vedený známymi TTP a frameworkom.
- **Indicator hunt:** spustený IoC alebo incidentom; reaktívnejší.
- **Situational hunt:** vychádza z konkrétneho rizikového profilu organizácie a aktuálnej situácie.

## Proces huntovania

1. Urči cieľ, rozsah, zdroje dát, nástroje a úspešný výsledok.
2. Zhromaždi telemetriu a vytvor baseline normálneho správania.
3. Reaguj na trigger alebo vytvor testovateľnú hypotézu: „Myslím si, že X sa deje prostredníctvom Y, preto očakávam dôkaz Z.“
4. Koreluj dáta a hľadaj TTP/anomálie naprieč prostredím.
5. Hypotézu potvrď, vyvráť alebo spresni a test opakuj.
6. Pri potvrdení vykonaj containment, eradication a recovery.
7. Zdokumentuj výsledky; vytvor nové detekcie a odporúčania.

Metriky: incidenty a kompromitované aktíva podľa kritickosti, dwell time, nové detekcie, opravy logovania, nové zraniteľnosti a odporúčania na zlepšenie biznis procesov.

## Pyramid of Pain

Od najľahšieho po najťažšie zmeniteľné pre útočníka:

**hash → IP → doména → host/network artefakt → nástroj → TTP**

Preto sú TTP-based detekcie trvácnejšie než blokovanie hashov. IoC sú stále užitočné na rýchlu reakciu a koreláciu.

## Frameworky a nástroje

- **PEAK (Prepare, Execute, Act with Knowledge):** príprava, vykonanie a premena poznatku na detekciu/automatizáciu/zmenu procesu.
- **MITRE hunting:** charakterizuj škodlivé správanie a hypotézu → analyzuj medzery a nasaď senzory/analytiku → triage, tuning a report.

Nástroje: SIEM na logy; EDR/MDR na endpoint visibility a response; honeypoty/honey credentials na deception; ML/štatistika na anomálie. Konkrétne príklady: YARA, Snort, ELK, Velociraptor, Sysinternals, Snyk, Maltego, Shodan, Ghidra a osquery.

Tool vyberaj podľa cieľa, pokrytia prostredia, škálovania a KPI (detection rate, false positives, MTTD/response). Proaktívny hunt sa orientuje na neznáme hrozby a správanie, je kontinuálny a viac závisí od človeka než od alertov.

### Predpoklady úspešného huntu

Pred huntingom over centralizovaný zber a časovú synchronizáciu logov, dostatočnú retenciu, endpoint/network/cloud visibility, znalosť normálneho správania, prístupové oprávnenia, IR eskaláciu a schopnosť bezpečne vykonať containment. Bez telemetrie sa hypotéza nedá vyvrátiť — „nič sme nenašli“ nie je to isté ako „hrozba tam nie je“.

Dobrá hypotéza: „Keďže skupina používa PowerShell na discovery, na Windows serveroch očakávame neobvyklé parent-child procesy, encoded commands a následné spojenie na novú doménu.“ Z nej priamo vyplývajú potrebné dáta, dotaz a kritérium potvrdenia.

---

# Modul 8 — Zdieľanie TI a spolupráca

## Modely spolupráce

- **ISAC:** výmena spravodajstva v konkrétnom odvetví.
- **ISAO:** širšie organizácie, ktoré nemusia byť viazané na jeden sektor.
- **Vendor–customer sharing:** vendor poskytuje telemetriu a TI; spätná väzba klientov zlepšuje produkty.
- **Public–private, medzinárodné, akademické a cross-sector partnerstvá:** rozširujú perspektívu a včasné varovanie.

Príklady rámcov/platforiem: CISA critical-infrastructure sharing, ENISA, PRIDA, MISP, AlienVault OTX, Cyber Threat Alliance, Anomali STAXX a Celerium CTIR.

## Dôvera a bezpečný kanál

Dôveru buduje transparentný pôvod, čas a dôkazy; validácia pred zdieľaním; reciprocita; konzistentná kvalita a príspevok nástrojmi či výskumom.

Súkromný kanál: **cieľ a scope → interné schválenie → partneri a metóda → MOU/data agreement → zabezpečený štruktúrovaný kanál**.

Verejný kanál: **cieľ → schválenie → vhodná komunita → validácia a sanitizácia → bezpečné a pravidelné zdieľanie**.

Ochrany: end-to-end encryption, anonymizácia/pseudonymizácia, sanitizácia, access control, klasifikácia a need-to-know. Dohoda musí riešiť vlastníctvo, právo ďalšieho zdieľania, retenciu, zodpovednosť a breach notification.

Použiť možno **Traffic Light Protocol (TLP)** ako označenie rozsahu povoleného zdieľania; treba sa riadiť konkrétnou dohodou a aktuálnou verziou štandardu.

## Problémy

- information overload a zlá správa dát,
- priveľká závislosť od cudzej inteligencie,
- únik citlivých údajov alebo prezradenie vlastnej obrany,
- slabá validácia a false positives,
- nedostatok zdrojov a nekompatibilné formáty,
- rozdielne jurisdikcie, zamestnanecké súkromie a prebiehajúce vyšetrovania,
- vendor konsolidácia, finančná životaschopnosť a zastaranie platformy.

Zdieľaj aj detekčné a response postupy (napr. Splunk/YARA rules), nielen IoC. Pred odoslaním vždy over, či dataset neumožňuje sekundárne odvodiť osobné alebo citlivé informácie.

### Hodnotenie zdieľacej platformy

Platforma má podporovať bezpečný prenos a šifrovanie, sanitizáciu, zrozumiteľné rozhranie, validáciu/prioritizáciu príspevkov, STIX/TAXII kompatibilitu, granular access control, audit a aktívny vývoj komunity. Skontroluj aj vlastníctvo dát, export pri ukončení služby a finančnú životaschopnosť vendora.

### Následky neopatrného zdieľania

- **Sekundárne zneužitie:** dáta zozbierané na obranu sa použijú na profiling, marketing alebo škodlivú činnosť.
- **Nesprávna atribúcia:** človek alebo organizácia sa chybne spojí s útokom, čo môže poškodiť povesť a psychiku.
- **Nečakaná inferencia:** kombinácia neškodných polí odhalí návyky, identitu alebo interné procesy.
- **Právny zásah:** zverejnenie indikátora môže narušiť vyšetrovanie alebo porušiť GDPR, zmluvu či retenčné pravidlo.
- **Dlhodobá erózia súkromia:** opakované nadmerné zdieľanie normalizuje zásahy do súkromia.

Pred zdieľaním použi štvoricu: **validate → classify → sanitize → authorize**. Po zdieľaní eviduj príjemcu, účel, čas a povolené ďalšie použitie.

---

# Modul 9 — TI v Incident Response

## Integrácia do životného cyklu IR

1. **Preparation:** actor profily, relevantné IoC/TTP, scenáre, playbooky a investície do nástrojov.
2. **Detection & analysis:** TI v SIEM/EDR zvyšuje skorú detekciu, koreláciu a kontext triage.
3. **Containment, eradication & recovery:** reakcia sa prispôsobí známym TTP a správaniu aktéra.
4. **Post-incident:** artefakty sa premenia na novú TI, detekcie, hunt hypotézy a aktualizované playbooky.

Pozor na analysis paralysis, nekvalitné feedy, chýbajúce priority a nedostatok odborníkov.

## Workflow a playbook

- **Workflow** je automatizovaný tok podmienok a akcií (ak threat score > prah, izoluj endpoint a založ incident).
- **Playbook** je štruktúrovaný návod pre konkrétny scenár, zahŕňa technické aj komunikačné kroky a rozhodovacie body.

Pri ransomware sa zisťuje variant, aktér, známe dešifrovacie možnosti, rozsah, persistence a lateral movement; výsledok riadi containment, eradication a obnovu.

## Triage, forenzika a adaptácia

TI pomáha určiť rozsah zero-day, korelovať IoC, identifikovať malware variant, pôvod infraštruktúry, botnet a historické vzory. Pri každej automatickej reakcii treba zohľadniť confidence, kritickosť aktíva a možný biznis dopad.

IR plány aktualizuj podľa nových ekonomických/geopolitických signálov, zdravotných rizík, kryptomenových tokov a hrozieb voči dodávateľom. Intelligence musí byť operacionalizovaná: kto reaguje, na čo, dokedy a akým postupom.

## Externí partneri

Polícia rieši vyšetrovanie a dôkazy; poisťovňa krytie a podmienky; MDR detekciu a technickú reakciu; externý právnik zákonnosť, privilege a oznamovanie; cloud/vendor partner vlastné systémy a nápravu. Vopred stanov bezpečné komunikačné kanály, kontakty, rozsah zdieľania a právne dohody.

## Recovery a lessons learned

- porovnaj obnovu s podobnými incidentmi,
- splň reporting/retention povinnosti,
- sprav reputačnú komunikáciu,
- prispôsob školenie reálnemu útoku,
- huntuj latentné IoC/TTP a skontroluj reinfekciu,
- aktualizuj risk assessment, detekcie, playbooky a komunikáciu.

KPI: detection rate, false-positive rate, incident volume/recurrence/escalation, **MTTD**, čas reakcie a vyriešenia (termín MTTR vždy v reporte jednoznačne definuj), frekvencia aktualizácie TI a cost per incident.

### TI podľa typu incidentu

- **Supply chain:** sleduj advisories, SBOM/závislosti, vendor kompromitácie a rovnaké TTP u partnerov.
- **BEC/phishing:** look-alike domény, reputácia odosielateľa, URL, ukradnuté účty; stiahni správy a blokuj doménu.
- **IoT/OT:** nové exploity, firmware, neobvyklé príkazy a fyzický dopad; containment nesmie vytvoriť väčšie prevádzkové riziko.
- **Insider:** neobvyklý čas prístupu, mass storage, cloud sharing a objem prenosu; rešpektuj pracovné právo a súkromie.
- **IP theft:** profil aktéra, cielené repozitáre, archívy a exfiltračné kanály.
- **Deepfake:** pôvod média, campaign context, komunikačný kanál a out-of-band overenie identity.

### Obsah lessons-learned výstupu

Časová os; root cause; prvotný vektor; zasiahnuté aktíva a dáta; IoC/TTP; actor attribution s confidence; čo fungovalo/nefungovalo; chýbajúca telemetria; právne a komunikačné povinnosti; nápravné úlohy s vlastníkom a termínom; nové detekcie, playbooky a hunt hypotézy.

---

# Modul 10 — Budúcnosť a kontinuálne učenie

## Nové prístupy

- **ATOM (Account Takeover Monitoring):** sleduje uniknuté účty a heslá spojené s doménou organizácie.
- **VINT (Vulnerability Intelligence):** pridáva k zraniteľnosti exploitability, výskyt exploitu, dopad na konkrétne prostredie a mitigáciu.
- **ASM (Attack Surface Management):** priebežne mapuje externý aj interný digitálny footprint, cloud, endpointy a IoT.

VINT zapoj do SDLC, ASM pravidelne aktualizuj a pre rôzne technológie vytvor osobitné IR plány. AI/ML pomáhajú s objemom dát, ale vyžadujú kvalitné vstupy, validáciu, vysvetliteľnosť a human oversight.

Nové riziká: integrita 3D tlačových súborov, kvantové ohrozenie slabých algoritmov, AR phishing/malicious overlays, biometrické spoofingy, 5G/edge/IoT visibility a automatizované útoky.

## Prepojenie TI a risk managementu

Najprv vytvor spoločný slovník, potom vlož TI do risk procesov a nakoniec vybuduj spoločné workflowy.

**FARM:**

1. **Frame:** urč kontext a smer riadenia rizika.
2. **Assess:** porovnaj zraniteľnosti s relevantnými hrozbami.
3. **Respond:** koordinuj mitigáciu podľa rizika.
4. **Monitor:** overuj účinnosť kontrol voči meniacim sa hrozbám.

## Učenie a kariéra

Krátkodobo: blogy, webináre, konferencie a fóra. Dlhodobo: OSINT challenges, certifikácie, vlastný výskum, príspevky do OTX/MISP, laby, mentoring, stáž a projekty. Gamifikácia a AR/VR dopĺňajú klasické učenie.

Kľúčové zručnosti: stakeholder communication, analytické myslenie, systémy a siete, scripting a dátová analýza, intelligence gathering, riešenie problémov, IoC/TTP profiling, komunita a nepretržité učenie.

Výzvy: explózia dát, obmedzené rozpočty, geopolitické zmeny, adaptabilita protivníkov, bias modelov a regulácia. Príležitosti: vyšší dopyt po odborníkoch, lepšie rozhodovanie a prepojenie TI s biznis rizikom.

TI sa používa aj v národnej bezpečnosti na terorizmus, country assessment, vojenské kapacity a kritickú infraštruktúru. Pri tvorbe regulácie pomáha adaptovať pravidlá na reálne hrozby, ale priveľmi úzka alebo rigidná regulácia rýchlo zastará a môže narušiť dôveru verejnosti.

### Praktický plán kontinuálneho učenia

- **Týždenne:** prečítaj jednu kvalitnú správu a namapuj správanie na ATT&CK.
- **Mesačne:** vytvor actor profile, hunt hypotézu alebo krátku analýzu kampane.
- **Štvrťročne:** precvič incident/tabletop, aktualizuj portfólio a zhodnoť vlastné skill gaps.
- **Priebežne:** pracuj v labe s MISP/SIEM, publikuj bezpečne sanitizované poznatky a žiadaj peer review.

Chráň aj vlastnú udržateľnosť: time blocking, krátke sústredené bloky (napr. Pomodoro), spánok, pohyb a vedomé prestávky. Kontinuálne učenie má byť dlhodobo opakovateľné, nie jednorazový nápor.

---

# Najdôležitejšie porovnania

| Dvojica | Rozdiel |
|---|---|
| Threat data vs. TI | surový údaj vs. analyzovaný, relevantný a actionable záver |
| IoC vs. TTP | konkrétna stopa, ktorú možno ľahko zmeniť vs. správanie/metóda aktéra |
| STIX vs. TAXII | formát obsahu vs. protokol jeho výmeny |
| Strategic vs. technical TI | biznis rozhodnutie a dlhý horizont vs. detail exploitu/malware |
| Active vs. passive collection | priama interakcia a bohatšie dáta vs. pozorovanie s menším rizikom |
| Automation vs. orchestration | automatický krok vs. koordinovaný sled krokov a systémov |
| Predictive vs. proactive TI | predpoveď z histórie vs. aktívne hľadanie a prevencia teraz |
| Threat hunting vs. incident response | proaktívne hľadanie skrytej hrozby vs. reakcia na zistený incident |
| Kill Chain vs. MITRE ATT&CK | lineárne fázy útoku vs. detailná matica správania a techník |
| CVSS vs. organizačné riziko | technická závažnosť vs. závažnosť v kontexte aktív, hrozieb a dopadu |

# Kontrolné otázky

1. Kedy sa surový IoC stáva actionable threat intelligence?
2. Prečo sa životný cyklus TI začína požiadavkou stakeholdera?
3. Aký výstup potrebuje CEO a aký SOC analytik?
4. Prečo je TTP-based detekcia odolnejšia než detekcia podľa hashu?
5. Aký je rozdiel medzi STIX a TAXII?
6. Aké riziká prináša aktívny zber dát?
7. Prečo vysoké CVSS samo osebe neurčuje prioritu patchovania?
8. Ako ACH obmedzuje confirmation bias?
9. Aký je rozdiel medzi automatizáciou a orchestráciou v TIP/SOAR?
10. Ako má vyzerať testovateľná threat-hunting hypotéza?
11. Ako threat hunting zlepšuje incident response a naopak?
12. Čo treba sanitizovať pred zdieľaním TI?
13. Kde sa TI zapája v každej fáze IR lifecycle?
14. Akými KPI sa dá preukázať, že TI reálne pomáha?
15. Ako sa líšia ATOM, VINT a ASM?

# Mini ťahák na opakovanie

**TI lifecycle:** plánuj → zbieraj → spracuj → analyzuj → distribuuj → získaj feedback.

**Kill Chain:** recon → weaponize → deliver → exploit → install → C2 → objective.

**Hunt:** scope/baseline → hypotéza → zber a korelácia → test → response → report a nová detekcia.

**Pyramid of Pain:** hash → IP → doména → artefakt → tool → TTP.

**IR:** príprava → detekcia/analýza → containment/eradication/recovery → lessons learned.

**Dobrá inteligencia:** relevantná, aktuálna, presná, dôveryhodná, kontextová, včasná a actionable.
