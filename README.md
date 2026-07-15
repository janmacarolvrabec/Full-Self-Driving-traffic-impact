# Vrh avtomobilov — vpliv deljene avtonomije na promet

Interaktivna simulacija in temeljna analiza vprašanja: **kdaj svetovni vozni park
doseže vrh, ko se uveljavi deljena avtonomna mobilnost — in ali obstoječe ceste
zdržijo promet, ki iz tega sledi.**

## Vsebina

| Datoteka | Kaj je |
|---|---|
| [`index.html`](index.html) | Interaktivna simulacija (samostojna spletna stran, en file). |
| [`docs/temeljna-analiza.md`](docs/temeljna-analiza.md) | Temeljni dokument — argumentacija, enačbe in viri, ki jih simulacija uresniči. |

## Kaj simulacija pokaže

- **Regionalni vrh voznega parka.** Štiri regije (Razviti/OECD, Kitajska, ostala
  Azija + Lat. Amerika + Bl. vzhod, Afrika + Južna Azija), vsaka s svojo
  motorizacijsko nasičenostjo in svojo krivuljo uveljavitve. Svetovni vrh je
  njihova vsota — razviti svet doseže vrh v 2030. letih, Afrika in J. Azija ga
  dvigata še po 2050.
- **Dve ločeni krivulji.** *Lastništvo* (število vozil) doseže vrh in upade;
  *cestna obremenitev* (kilometri / prepustnost) je lahko drugačna. To razlikovanje
  je jedro poštene analize.
- **Poštena infrastrukturna teza.** Prevoženi kilometri lahko narastejo (prazne
  vožnje), a prepustnost obstoječih cest raste hitreje (platooning) — kazalnik
  obremenitve pade pod 1,0 (zeleno). Z drsnikoma *prazne vožnje* in *pridobitev
  prepustnosti* ga je mogoče obrniti v rdeče: teza ni zajamčena, ampak pogojena.

## Uporaba

Odpri `index.html` v brskalniku. Trije scenariji (Konzervativni / Srednji /
Agresivni po Sebi) in osem drsnikov; preklop med pogledoma *Vozni park* in
*Cestna obremenitev*; svetla/temna tema; podatkovna tabela za dostopnost.

## Model

```
N(t) = Σᵣ N₀ᵣ · Dᵣ(t) · [1 − φᵣ(t)·(1 − 1/m)]        (vozni park)
L(t) = Σ wᵣ·VKTᵣ(t) / Σ wᵣ·Capᵣ(t)                    (cestna obremenitev)
```

Podrobnosti, predpostavke in viri (ITF/OECD Lizbona, RethinkX/Seba, S&P Global
Mobility, PATH/Berkeley, Litman/VTPI) so v [temeljnem dokumentu](docs/temeljna-analiza.md).

> Simulacija je *mis, ne napoved*. Parametri so negotovi in namenoma nastavljivi;
> namen je pokazati občutljivost izida na predpostavke.
