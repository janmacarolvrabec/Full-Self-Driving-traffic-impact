# Vrh avtomobilov: kako deljena avtonomija spremeni svetovni vozni park

**Temeljni dokument k simulaciji.** Ta zapis je intelektualna podlaga, ki jo
interaktivna simulacija (`index.html`) uresniči v številkah in grafih. Vsak
drsnik v simulaciji ustreza enemu vzvodu, opisanemu tukaj; vsak pregled
(readout) je posledica ene od spodnjih enačb.

---

## 1. Teza in povzetek

Trditev je preprosta in za mnoge nasprotno-intuitivna:

> **Ko avtonomna vozila začnemo deliti, se svetovni vozni park preneha večati in
> začne upadati — pri čemer za isto mobilnost ne potrebujemo več cest, ampak
> bolje izkoriščene obstoječe.**

Dve ločeni stvari se zgodita hkrati, in prav njuno ločevanje je jedro poštene
analize:

1. **Lastništvo (število vozil) doseže vrh in pade.** Deljeno vozilo, ki vozi
   24 ur na dan, opravi delo mnogih zasebnih avtomobilov, ki 95 % časa stojijo.
   Zato začne skupno število avtomobilov upadati — to je *vrh avtomobilov*
   (angl. *peak car*).
2. **Prevoženi kilometri (obremenitev cest) se lahko celo povečajo.** Manj vozil
   ne pomeni manj vožnje. Prazne vožnje (repozicioniranje, prevzemi) in nova
   povpraševanja po mobilnosti prevožene kilometre potisnejo navzgor.

Zakaj torej infrastruktura vzdrži? Ker **prepustnost obstoječih cest raste
hitreje kot promet** — povezana in avtonomna vozila vozijo v gostejših, bolje
usklajenih tokovih (platooning). Vrh avtomobilov je torej vrh *lastništva*, ne
nujno prometa; in kljub več kilometrom nova gradnja cest ni nujna, če
prepustnost pridobimo z boljšo izrabo obstoječega omrežja.

**Ključne številke (srednji scenarij simulacije):**

| Kazalnik | Vrednost |
|---|---|
| Svetovni vozni park danes (2025) | ~1,6 milijarde vozil |
| Vrh svetovnega parka (srednji scenarij) | pozna 2030. leta (~2037) |
| Vrh v razvitih regijah (OECD) | sredina 2030. let |
| Afrika + J. Azija | park raste še po 2050 |
| Delež cestnega parka ob konicah pri polni deljeni floti | ~1/3 današnjega |
| Pridobitev prepustnosti ceste pri ~50 % penetraciji | več kot podvojena |

---

## 2. Regulatorna realnost EU 2026 (pošten začetek)

Da analiza ostane verodostojna, začnimo z jasno mejo med tem, kar **že velja**,
in tem, kar model **predpostavlja za prihodnost**.

**Kar je res, danes:** nizozemski RDW je 10. aprila 2026 izdal začasno EU
homologacijo (type approval) za Teslin sistem FSD, po približno 18 mesecih
ocenjevanja, ki je vključevalo več kot 1,6 milijona kilometrov testiranja na
evropskih cestah. Sledile so nacionalne aktivacije: Nemčija 22. maja, Litva
20. maja, Estonija 29. maja, Danska in Belgija junija. Slovenija je na seznamu
v obravnavi.

**Kar je pošteni pridržek:** odobreno je **FSD Supervised** — sistem **stopnje 2
(Level 2)**, ki deluje na vseh vrstah cest, a **zahteva neprekinjeno pozornost
voznika**. To ni avtonomija, ki omogoča 24/7 deljeno floto brez voznika. Mercedes
in BMW sta se s stopnje 3 celo umaknila. Regulatorna vrata se torej odpirajo
hitro, a **prava avtonomija brez voznika (stopnja 4–5)** — tista, ki šele omogoča
deljeno floto — je še pred nami.

**Posledica za model:** »leto regulatorne odobritve prave avtonomije« obravnavamo
kot **spremenljivko**, ne kot že nastopljeno dejstvo iz leta 2026. V simulaciji ji
ustreza *prelomno leto uveljavitve* (sredina S-krivulje) in njegov *zamik*.

---

## 3. Krivulje uveljavitve tehnologij (zakaj S-krivulja)

Nove tehnologije se ne uveljavijo linearno, ampak po **logistični (S-) krivulji**:
počasen začetek, nato eksplozivna sredina, nato nasičenje. Zgodovinske analogije:

- **Konj → avtomobil:** ulice New Yorka so v ~15 letih (1900–1915) prešle od
  prevlade konj do prevlade avtomobilov.
- **Varnostni pasovi, katalizatorji, ABS:** vsakič S-krivulja, pospešena z
  regulacijo.
- **Pametni telefon:** od ~2007 do večinske penetracije v razvitem svetu v ~7
  letih.

**Zakaj danes hitreje kot nekoč, a ne kot pri telefonih:** difuzija je danes
strmejša (globalne dobavne verige, programske posodobitve na daljavo, omrežni
učinki platform za deljenje). A avto **ni** pametni telefon — je drag, dolgoživ
kapitalski dober (povprečna starost vozila v EU je nad 12 let) in vpet v
regulacijo, zavarovalništvo in infrastrukturo. Zato je realna strmina S-krivulje
**med** obema svetovoma.

V modelu to zajame parameter **hitrost sprejemanja (k)**: večji `k` pomeni
strmejšo krivuljo. Delež deljene avtonomije v regiji `r` ob letu `t`:

$$\varphi_r(t) = \frac{p^{\max}_r}{1 + e^{-k_r (t - t^0_r)}}$$

kjer je `p_max_r` zgornja meja deljenja v regiji, `t0_r` prelomno leto (sredina
krivulje) in `k_r` hitrost.

---

## 4. Dokaz »1/3 voznega parka« (in pošten pogoj)

Osrednja empirična opora je študija **ITF/OECD (Lizbona)** o skupnostno deljenih
samovozečih flotah:

- Skupna deljena samovozeča flota bi lahko naredila **~90 % konvencionalnih
  avtomobilov odvečnih**.
- Tudi **ob prometnih konicah** bi zadoščala **le okoli tretjina (≈35 %)**
  današnjih vozil.
- Simulacija **Helsinkov** je rezultat potrdila v drugem mestnem okolju.

**Ključni pogoj — vzvod je DELJENJE, ne avtonomija sama.** Zasebno avtonomno
vozilo, ki 95 % časa še vedno stoji na parkirišču, zniža park le za okoli
**desetino**. Šele deljenje (isto vozilo služi mnogim uporabnikom) sprosti
velikanski presežek. Zato je v modelu **delež deljenih voženj** glavni vzvod;
brez njega avtonomija skoraj ne zniža parka.

**Pošten protiutež iz iste študije:** skupni **prevoženi kilometri (VKT)
narastejo** — v enem scenariju se ob konicah več kot **podvojijo** — zaradi
obvozov za prevzeme, repozicioniranja praznih vozil in prestopa iz avtobusov v
deljene avtomobile. Prav zato simulacija loči **dve krivulji**: vozni park
(pade) in cestno obremenitev (lahko naraste).

Mehanizem v enačbi: vozilo v deljeni floti prevozi `m`-krat več kilometrov na
leto kot zasebni avto (24/7 izraba). Zato en deljeni avto nadomesti `m` zasebnih,
in število vozil v regiji je:

$$N_r(t) = N^0_r \cdot D_r(t) \cdot \left[\,1 - \varphi_r(t)\left(1 - \tfrac{1}{m}\right)\right]$$

kjer je `N0_r` izhodiščni park regije, `D_r(t)` rast povpraševanja po mobilnosti
in oglati oklepaj učinek deljene izrabe.

---

## 5. Vrh avtomobilov in neenakomeren razvoj

Svetovni vrh **ni** en sam dogodek — je **vsota regij, ki dosežejo vrh ob
različnih časih**. To je bistvo: brez regionalne razčlenitve model laže.

**Izhodišče brez preobrata (baseline).** Svetovni vozni park je bil ~1,31
milijarde (2020) in bi ob nespremenjenih trendih zrasel na ~2,21 milijarde do
2050. A rast ni enakomerna:

- **Razvite regije (OECD)** so konvencionalni vrh dosegle že okoli **2023**;
  motorizacija je nasičena.
- **Nerazvite regije** rastejo: prebivalstvo zunaj OECD raste več kot **trikrat
  hitreje**, motorizacija narašča s ~92 na ~173 vozil na 1000 prebivalcev.

Simulacija zato modelira **štiri regije**, vsaka s svojo motorizacijsko
nasičenostjo in svojo S-krivuljo uveljavitve deljene avtonomije:

| Regija | Vloga v modelu | Vrh (srednji scenarij) |
|---|---|---|
| **Razviti / OECD** | nasičen park, zgodnja uveljavitev | sredina 2030. let |
| **Kitajska** | velik park, hitra tehnološka adopcija | pozna 2030. let |
| **Ostala Azija + Lat. Amerika + Bl. vzhod** | še rastoč park, poznejša uveljavitev | okoli 2045 |
| **Afrika + J. Azija** | najhitreje rastoč, uveljavitev najpozneje | raste še po 2050 |

Svetovna krivulja je njihova vsota. Zato lahko razviti svet doseže vrh v sredini
2030. let, medtem ko Afrika in Južna Azija **še naprej dvigata svetovni skupek**
še po 2050. To je *neenakomeren razvoj*, prevzet naravnost iz podatkov.

---

## 6. Infrastruktura: zakaj obstoječa zadošča

To je Janova osrednja teza — in model jo prikaže **pošteno**, skupaj s
protiargumentom.

**Za tezo (prepustnost raste).** Povezana in avtonomna vozila vozijo v gostejših,
usklajenih tokovih:

- Pri **~50 % penetraciji** se izhodiščna prepustnost cest **več kot podvoji**.
- Starejše delo programa **PATH (Berkeley)** je pokazalo, da lahko prepustnost
  pasu naraste za **faktor 2–3** s platooningom (vozila v koloni z majhnimi
  varnostnimi razmiki).
- Literatura tezo izrecno uokvirja: **drago in okoljsko škodljivo je povečevati
  prepustnost z gradnjo novih cest, ko pa jo lahko povečamo z boljšo izrabo
  obstoječe infrastrukture** — skoraj parafraza Janovega argumenta.

**Protiutež (pošten rebound).** Boljša izraba ustvari novo povpraševanje:
avtonomija omogoči vožnjo tistim, ki prej niso vozili (starejši, mladoletni,
invalidi), prazne vožnje dodajo kilometre, cenejša vožnja spodbudi več vožnje.
To je **indukcijski učinek (rebound)**. Teza je močnejša, ker preživi to
protiutež — zato jo model odkrito prikaže.

**Kako model to izmeri.** Za vsako regijo:

- **Povpraševanje po kilometrih (VKT):** raste s povpraševanjem in dodatkom
  praznih voženj:
  $$\text{VKT}_r(t) = D_r(t)\,\big(1 + \varphi_r(t)\cdot \text{prazne\_vožnje}\big)$$
- **Efektivna prepustnost cest:** raste s penetracijo avtonomije:
  $$\text{Cap}_r(t) = 1 + a_r(t)\cdot \text{pridobitev\_prepustnosti}$$
  kjer je `a_r(t)` napredek uveljavitve (0→1).
- **Cestna obremenitev (indeks):** razmerje, normirano na 1,0 v letu 2025:
  $$L(t) = \frac{\sum_r w_r\,\text{VKT}_r(t)}{\sum_r w_r\,\text{Cap}_r(t)}$$

**Branje kazalnika:**
`L ≤ 1,0` → obstoječe ceste imajo rezervo (zeleno: gradnja ni nujna).
`L > 1,0` → promet raste hitreje od prepustnosti (potrebna nova infrastruktura).

Uporabnik lahko z drsnikoma *prazne vožnje* (gor) in *pridobitev prepustnosti*
(dol) kazalnik obrne v rdeče — teza torej **ni zajamčena**, ampak pogojena, in
to je poštenost modela.

---

## 7. Model in enačbe (kar simulacija dejansko računa)

**Časovni okvir:** leta 2025–2065. **Regije:** `r ∈ {OECD, Kitajska, Ostalo,
Afrika+J.Azija}`.

**(a) Povpraševanje / motorizacija** — multiplikator `D_r(t)` z rastjo, ki upada
proti nasičenju:
$$D_r(2025)=1,\quad D_r(t)=D_r(t-1)\,(1+g_r(t)),\quad g_r(t)\;\text{upada}\;g^0_r \to g^1_r$$

**(b) Uveljavitev deljene avtonomije** — S-krivulja na regijo:
$$\varphi_r(t) = \frac{p^{\max}_r}{1 + e^{-k_r (t - t^0_r)}}$$

**(c) Vozni park** — na regijo in svetovno:
$$N_r(t) = N^0_r\,D_r(t)\left[1 - \varphi_r(t)\left(1-\tfrac1m\right)\right],\qquad
N(t)=\sum_r N_r(t)$$
Izhodišče brez preobrata: $B(t)=\sum_r N^0_r D_r(t)$. Vrh: $\arg\max_t N(t)$.

**(d) Cestna obremenitev** — glej razdelek 6.

**Vzvodi (drsniki v simulaciji):**

| Drsnik | Simbol | Kaj počne |
|---|---|---|
| Krovni delež deljenja | `p_max` | zgornja meja deljenja (glavni vzvod) |
| Izkoriščenost deljenega vozila | `m` | kolikokrat več km/leto kot zasebni avto |
| Zamik uveljavitve | `Δt0` | premakne prelomna leta vseh regij |
| Hitrost sprejemanja | `k` | strmina S-krivulje |
| Rast povpraševanja | `×g` | motorizacija v vzponu (potiska vrh naprej) |
| Prazne vožnje | deadhead | dodatek h kilometrom (rebound) |
| Pridobitev prepustnosti | capGain | platooning (znižuje obremenitev) |
| Izhodišče 2025 | `N0` | skupni park danes (mrd) |

**Trije scenariji (presets):** *Konzervativni* (počasna uveljavitev, nizko
deljenje, visoke prazne vožnje), *Srednji* (uravnotežen), *Agresivni / Seba*
(hitra uveljavitev, visoko deljenje, velika pridobitev prepustnosti).

---

## 8. Viri

- **ITF/OECD**, *Urban Mobility System Upgrade: How shared self-driving cars
  could change city traffic* (t. i. Lizbonska študija), International Transport
  Forum, 2015. — izvor deleža »1/3 parka ob konicah« in »90 % odvečnih vozil« ter
  ugotovitve o naraslih VKT.
- **ITF/OECD**, ponovitev za **Helsinke** — potrditev v drugem mestnem okolju.
- **RethinkX**, Tony Seba & James Arbib, *Rethinking Transportation 2020–2030* —
  scenarij hitre uveljavitve deljene avtonomije (»Agresivni« preset).
- **S&P Global Mobility** — projekcije svetovnega voznega parka (izhodišče in
  baseline rasti do 2050).
- **California PATH Program (UC Berkeley)** — meritve povečanja prepustnosti pasu
  s platooningom (faktor 2–3).
- **T. Litman / VTPI**, *Autonomous Vehicle Implementation Predictions* —
  časovnice uveljavitve, indukcijski (rebound) učinki, previdnostni pridržki.
- **RDW (NL)** in nacionalni regulatorji EU — začasna EU homologacija FSD
  (Supervised), april–junij 2026; razmejitev stopnje 2 vs. prave avtonomije.

> **Opozorilo o negotovosti.** Simulacija je *mis, ne napoved*. Parametri so
> negotovi in namenoma nastavljivi; namen je pokazati **občutljivost** izida na
> predpostavke — predvsem na to, da vrh sproži *deljenje*, ne avtonomija sama, in
> da prihranek pri vozilih ne pomeni nujno prihranka pri kilometrih.
