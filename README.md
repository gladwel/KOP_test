# 2023 nové

Problém diskrétního rozmístění:

Dáno:

- množina n modulů K={k_1, ..., k_n}

- množina m pozic P={p_1, ..., p_m}, m ≥ n

- propojení modulů jako hypergraf G (K, N), kde N je množina spojů nj

- cenová funkce W (R, s), která pro každé přiřazení R: K → P odhadne cenu realizace spoje s.

Nalézt:

- prosté přiřazení R:K → P (rozmístění), které minimalizuje součet ohodnocení W (R, s) přes všechny spoje s.

Konfigurační proměnno jsou formulovány jako index pozice pro každý modul. Stav je tvořen pouze ohodnocením konfiguračních

proměnných. Nasazovaná heuristika pracuje s prohledávacím prostorem. Jeden krok je ohodnocení jedné proměnné. Nemá

možnost odvolat ani změnit rozhodnuté ohodnocení konfigurační proměnné

`💛 hint`

Prohledávací prostor je vždy orientovaným stromem

Prohledávací prostor je acyklický

Heuristika snončí po n krocích

Heuristika skončí po m krocích

`answer`

`✅ correct`

Prohledávací prostor je acyklický - Správně, Heuristika pracuje s prohledávacím prostorem, kde jeden krok je ohodnocení jedné proměnné a neexistuje možnost odvolat nebo změnit rozhodnutí, což naznačuje acyklický charakter prohledávání.

Heuristika snončí po n krocích - Správně, Pokud je heuristika navržena tak, aby hodnotila každý modul (a máme n modulů) právě jednou bez možnosti změny, pak by heuristika měla skončit po n krocích, což odpovídá počtu modulů.

`❌ wrong`

Prohledávací prostor je vždy orientovaným stromem - Špatně, například do ohodnocení [None, k_1, None, k_2, None] se lze dostat z [None, k_1, None, None, None] a [None, None, None, k_2, None]

Heuristika skončí po m krocích - Špatně, Heuristika hodnotí moduly, jejichž počet je n, a ne pozice, kterých je m. Protože každý modul je hodnocen právě jednou, heuristika skončí po n krocích, nikoliv po m krocích, pokud se každý modul hodnotí samostatně.

---

Problém diskrétního rozmístění:

Dáno:

- množina n modulů K={k_1, ..., k_n}

- množina m pozic P={p_1, ..., p_m}, m ≥ n

- propojení modulů jako hypergraf G (K, N), kde N je množina spojů nj

- cenová funkce W (R, s), která pro každé přiřazení R: K → P odhadne cenu realizace spoje s.

Nalézt:

prosté přiřazení R:K → P (rozmístění), které minimalizuje součet ohodnocení W (R, s) přes všechny spoje s.

Nasazovaný algoritmus je iterativní. Pokud pro přiřazení p neexistuje modul k, který by tam byl rozmístěn, chápe se to jako prázdný modul na pozici p.

`💛 hint`

Jestliže jediný operátor je párová změna na modulech, tj. moduly k_a a k_b, 1≤a, b≤n, i ≠ j si vymění pozice, pak stavový prostor není souvislý

Jestliže jediný operátor je párová změna na pozicích, tj. moduly na pozicích p_a a p_b, 1≤a, b≤m, i ≠ j si vymění pozice, pak stavový prostor není souvislý

`answer`

`✅ correct`

Jestliže jediný operátor je párová změna na modulech, tj. moduly k_a a k_b, 1≤a, b≤n, i ≠ j si vymění pozice, pak stavový prostor není souvislý - Správně, Vzhledem k tomu, že operátor definuje pouze výměnu mezi moduly, a ne zahrnuje všechny možné přesuny, může existovat více oddělených podprostorů, které nejsou vzájemně dosažitelné.

`❌ wrong`

Jestliže jediný operátor je párová změna na pozicích, tj. moduly na pozicích p_a a p_b, 1≤a, b≤m, i ≠ j si vymění pozice, pak stavový prostor není souvislý - Špatně, Pokud jsou pozice, na kterých se moduly nacházejí, jedinými proměnnými a můžeme je mezi sebou vyměňovat, pak bude prostor stále souvislý, protože každá pozice může být dosažena výměnou z jakékoli jiné pozice.

---

Formulace rozhodovacího problému minimálního obdélníkového pokrytí:

"Dána binární matice M. Existuje pokrytí všech '1' pomocí množiny nejvýše K obdélníků. Obdélník je definován jako kartézský součin podmnožiny řádků a podmnožiny sloupců. '1' je pokryta obdélníkem, pokud je v něm obsažena. Obdélník nesmí obsahovat žádné '0'. Minimalizujte počet obdélníků v pokrytí."

Heuristika řešící tento problém používá jako stav seznam obdélníků, pokrývajících daný prvek matice (ano, jistěže to jde lépe). Operátorem rozumíme odebrání/přidání konkrétního prvku matice do konkrétního obdélníku (operátor nemá parametry). Za těchto okolností

`💛 hint`

Asymptotická horní mez velikosti stavového prostoru roste exponenciálně s K

Asymptotická horní mez velikosti stavového prostoru roste kvadraticky s n a m

Pro každý prvek matice, operátory generují okolí velikosti m

Pro každý prvek matice, operátory generují okolí velikosti K

`answer`

`✅ correct`

Asymptotická horní mez velikosti stavového prostoru roste exponenciálně s K - Správně, S rostoucím K, počet možných kombinací obdélníků, které mohou pokrýt '1' v matici, roste exponenciálně, protože každá '1' může být pokryta mnoha různými obdélníky.

Pro každý prvek matice, operátory generují okolí velikosti K - Správně, Každý prvek může být pokrytý různými obdélníky, jejichž maximální počet je omezen na K, což definuje velikost okolí pro daný prvek.

`❌ wrong`

Asymptotická horní mez velikosti stavového prostoru roste kvadraticky s n a m - Špatně, Kvůli kartézskému součinu podmnožin řádků a sloupců je růst spíše kombinatorický než kvadratický.

Pro každý prvek matice, operátory generují okolí velikosti m - Špatně, Okolí generované pro každý prvek závisí na počtu obdélníků, které mohou daný prvek pokrýt, ne pouze na m.

---

Iterativní heuristika řeší problém obchodního cestujícího v rovině. Operátorem je dvojzáměna na úsecích túry (dva úseky jsou nahrazeny jinými dvěma úseky). Momentálně řešená instance má 5 měst.

`💛 hint`

Stavový prostor má silně souvislý graf

Stavový prostor má 5^2 = 25 stavů

Okolí každého stavu má velikost 5

Okolí každého stavu má velikost 10

`answer`

`✅ correct`

Stavový prostor má silně souvislý graf - Správně, Vzhledem k povaze problému obchodního cestujícího a definici iterativní heuristiky lze očekávat, že stavový prostor je silně souvislý, což umožňuje procházet mezi různými stavy (túrami) efektivně.

Okolí každého stavu má velikost 5 - Správně, Velikost okolí závisí na specifikách definice okolí. V kontextu dvojzáměny může být velikost okolí definována pevně, ale pro 5 měst toto tvrzení není přesné bez dalšího kontextu.

`❌ wrong`

Stavový prostor má 5^2 = 25 stavů - Špatně, Počet stavů ve stavovém prostoru je určen kombinacemi možných úseků mezi městy, ne pouhou kvadratickou funkcí počtu měst. Pro 5 měst je stavů mnohem více.

Okolí každého stavu má velikost 10 - Špatně, Velikost okolí v iterativní heuristice závisí na definovaném operátoru a konkrétním způsobu jeho aplikace, pro 5 měst a použití dvojzáměny velikost okolí obecně nebude pevně 10.

---

Vyhodnocení zdatnosti ve Fast Messy GA algoritmu je založeno na

`💛 hint`

reprezentaci individua

výpočtu, který pomocí dalších informací vrátí zdatnost libovolné podmnožiny genů

fenotypu individua

použití referenčního individua

`answer`

`✅ correct`

výpočtu, který pomocí dalších informací vrátí zdatnost libovolné podmnožiny genů - Správně, Toto je klíčový princip Fast Messy GA, kde zdatnost je vyhodnocena na základě efektivity kombinací genů.

použití referenčního individua - Správně, Referenční individua mohou být použita k určení zdatnosti v kontextu Fast Messy GA pro srovnání s ostatními jedinci.

`❌ wrong`

reprezentaci individua - Špatně, Zdatnost v Fast Messy GA je určena výpočtem zdatnosti specifických kombinací genů, ne pouze na základě reprezentace jedince.

fenotypu individua - Špatně, V Fast Messy GA je důraz kladen na genotypovou reprezentaci a její interakce, ne přímo na fenotyp.

---
# Bayesovská optimalizace
Základní jednotkou reprezentace, se kterou pracuje bayesovská optimalizace je

`💛 hint`

dvojice [identifikace proměnné, hodnota]

pravděpodobnost selekce individua

binární řetěz

statistický model závislostí mezi proměnnými

vektor hodnot (odpověď ze starého testu)

`answer`

`✅ correct`

statistický model závislostí mezi proměnnými - Správně, To je základ bayesovské optimalizace, kde modely závislostí slouží k predikci výkonu a následnému rozhodování.

`❌ wrong`

dvojice [identifikace proměnné, hodnota] - Špatně, Bayesovská optimalizace pracuje s modely, které reprezentují závislosti mezi proměnnými, ne s jednoduchými dvojicemi.

pravděpodobnost selekce individua - Špatně, V bayesovské optimalizaci je klíčové modelování závislostí a predikce výkonu, ne pravděpodobnost selekce.

binární řetěz - Špatně, Bayesovská optimalizace nepracuje přímo s binárními řetězy, ale s matematickými modely závislostí.

vektor hodnot (odpověď ze starého testu) - Špatně, Vektor hodnot může být vstupem pro model, ale samotná základní jednotka je model závislostí.

---

Nová generace v bayesovské optimalizaci vzniká

`💛 hint`

křížením

rozdělením a spojením fragmentů genetické informace

generováním podle stochastického modelu

ruletovým výběrem

`answer`

`✅ correct`

generováním podle stochastického modelu - Správně, Nové řešení jsou generována na základě predikcí stochastického modelu, který je aktualizován s každou iterací.

`❌ wrong`

křížením - Špatně, Bayesovská optimalizace nevyužívá křížení v tradičním smyslu genetických algoritmů.

rozdělením a spojením fragmentů genetické informace - Špatně, Tento proces je typický pro genetické algoritmy, nikoli pro bayesovskou optimalizaci.

ruletovým výběrem - Špatně, Ruletový výběr je selekční metoda v genetických algoritmech, ne v bayesovské optimalizaci.

---

Stochastický model v bayesovská optimalizaci vzniká

`💛 hint`

tak, aby vystihoval žádané vlastnosti řešení

tak, aby vystihoval vlastnosti aktuální generace

křížením z předchozí generace

stochastickým výběrem

`answer`

`✅ correct`

tak, aby vystihoval vlastnosti aktuální generace - Správně, Model je aktualizován a vylepšován na základě výsledků a dat získaných z aktuální generace řešení.

`❌ wrong`

tak, aby vystihoval žádané vlastnosti řešení - Špatně, Model je vytvořen na základě dat z předchozích iterací, ne na základě předem definovaných vlastností řešení.

křížením z předchozí generace - Špatně, V bayesovské optimalizaci se nevyužívá křížení v tradičním genetickém smyslu.

stochastickým výběrem - Špatně, Stochastický model je vytvářen na základě matematických a statistických metod, nikoli náhodným výběrem.

---

Stochastický model v bayesovská optimalizaci vzniká

`💛 hint`

podle vlastností aktuální generace

podle žádaných vlastností řešení

křížením z předchozí generace

stochastickým výběrem

`answer`

`✅ correct`

podle vlastností aktuální generace - Správně, Model je aktualizován s každou iterací na základě nově získaných dat a informací o výkonu aktuálních řešení.

`❌ wrong`

podle žádaných vlastností řešení - Špatně, Vytváření modelu je založeno na empirických datech, nikoli na předdefinovaných vlastnostech ideálního řešení.

křížením z předchozí generace - Špatně, Bayesovská optimalizace nevyužívá principy křížení známé z genetických algoritmů.

stochastickým výběrem - Špatně, Modelování v bayesovské optimalizaci se opírá o statistické metody a analýzu dat, ne o náhodný výběr.

---

# Dynamické programování

Dynamické programování může

`💛 hint`

uváznout v lokálním minimu

potřebovat velikost paměti, kterou nelze odvodit jen z velikosti instance

potřebovat velikost paměti, omezenou polynomem ve velikosti instance

divergovat

`answer`

`✅ correct`

potřebovat velikost paměti, kterou nelze odvodit jen z velikosti instance - Správně, Velikost paměti potřebná pro dynamické programování může být závislá na struktuře problému a může být větší než je přímo odvozená z velikosti instance.

potřebovat velikost paměti, omezenou polynomem ve velikosti instance - Správně, V mnoha případech je paměťová náročnost dynamického programování polynomiálně omezena ve velikosti vstupní instance.

`❌ wrong`

uváznout v lokálním minimu - Špatně, Dynamické programování řeší problémy optimalizací tím, že rozdělí problém na menší podproblémy a řeší je jen jednou. Díky tomu se vyhýbá uvíznutí v lokálních minimech tím, že najde globální optimum.

divergovat - Špatně, Dynamické programování je deterministický algoritmický přístup, který směřuje k výpočtu optimálního řešení; nejde o iterační metodu, která by mohla divergovat.

---

Dynamické programování je aplikováno na grafový problém. Používá jako klíč k výběru z paměti řešení podinstancí dvojici diskrétních proměnných (p,q), kde p je index uzlu a q index hrany. Všechny podinstance je třeba řešit. Velikost instance n se měří počtem uzlů. Dekompozice a kompozice má složitost O(n). Algoritmus

`💛 hint`

má složitost rostoucí nejméně se čtvrtou mocninou velikosti instance

má složitost rostoucí nejvýše se třetí mocninou velikosti instance

je pseudopolynomiální

je globální metoda

pokud nepoužíváme rozdělení na stupně, paměť podinstancí roste nejméně se třetí mocninou velikosti instance

`answer`

`✅ correct`

má složitost rostoucí nejméně se čtvrtou mocninou velikosti instance - Správně, Složitost algoritmu může růst rychleji v závislosti na struktuře grafu a na tom, jak jsou definovány podinstance.

je globální metoda - Správně, Dynamické programování se snaží najít globálně optimální řešení rozdělením problému na menší části.

pokud nepoužíváme rozdělení na stupně, paměť podinstancí roste nejméně se třetí mocninou velikosti instance - Správně, Bez efektivního rozdělení může paměťová náročnost růst s třetí mocninou velikosti instance nebo i rychleji.

`❌ wrong`

má složitost rostoucí nejvýše se třetí mocninou velikosti instance - Špatně, Pokud algoritmus zahrnuje řešení všech podinstancí s dvojicemi (p, q), složitost může být vyšší než kubická.

je pseudopolynomiální - Špatně, Algoritmus je klasifikován jako pseudopolynomiální na základě jiných kritérií, než jsou pouze složitostní třídy.

---

Dynamické programování je aplikováno na grafový problém. Používá jako klíč k výběru z paměti řešení podinstancí dvojici diskrétních proměnných (p,q), kde p je index uzlu a q index hrany. Velikost instance se měří počtem uzlů. Složitost kompozice a dekompozice je konstantní. Algoritmus

`💛 hint`

má exponenciální dolní asymptotickou mez složitosti

je pseudopolynomiální

má kubickou horní asymptotickou mez složitosti

pokud se nepoužijí stupně, paměť vyžaduje kubické množství řešení podinstancí

`answer`

`✅ correct`

má kubickou horní asymptotickou mez složitosti - Správně, Vzhledem k použití konstantní složitosti pro kompozici a dekompozici a způsobu definice podinstancí může algoritmus dosahovat kubické složitosti.

pokud se nepoužijí stupně, paměť vyžaduje kubické množství řešení podinstancí - Správně, Bez optimalizace může paměťová náročnost růst až kubicky s velikostí instance.

`❌ wrong`

má exponenciální dolní asymptotickou mez složitosti - Špatně, Dynamické programování typicky vede k polynomiální nebo pseudopolynomiální složitosti díky efektivnímu využívání výpočtů podinstancí.

je pseudopolynomiální - Špatně, Pseudopolynomiální složitost závisí na numerických hodnotách vstupu, zde je složitost definována strukturou problému.

---

Dynamické programování je aplikováno na grafový problém. Velikost instance je charakterizována počtem uzlů. Podinstance je charakterizována podgrafem grafu zadaného v instanci o nejvýše n/2 uzlech, kde n je velikost instance. Kompozice a dekompozice mají lineární složitost. Algoritmus je

`💛 hint`

exponenciální

pseudopolynomiální

polynomiální

globální metoda

`answer`

`✅ correct`

polynomiální - Správně, Algoritmus dosahuje polynomiální složitosti díky efektivní dekompozici a kompozici problému.

globální metoda - Správně, Dynamické programování je globální metoda, protože hledá řešení celého problému rozdělením na menší části a jejich řešením.

`❌ wrong`

exponenciální - Špatně, Vzhledem k lineární složitosti kompozice a dekompozice a efektivnímu rozdělení problému je algoritmus polynomiální.

pseudopolynomiální - Špatně, Pseudopolynomiální klasifikace není přímo aplikovatelná bez dalších specifikací o vstupních hodnotách.

---

Dynamické programování je aplikováno na grafový problém. Velikost instance se měří počtem uzlů. Podinstance je charakterizována libovolnou podmnožinou uzlů. Kompozice a dekompozice je v konstantním čase. Existuje instance, kde je třeba vypočíst všechny podinstance. Algoritmus je vždy

`💛 hint`

nejhůře lineární

pseudopolynomiální

nejhůře polynomiální

nejlépe exponenciální

`answer`

`✅ correct`

nejlépe exponenciální - Správně, Nutnost vypočítat všechny podmnožiny uzlů vede k exponenciální složitosti v nejhorším případě.

`❌ wrong`

nejhůře lineární - Špatně, Vzhledem k nutnosti vypočítat všechny podmnožiny uzlů, algoritmus může dosahovat exponenciální složitosti.

pseudopolynomiální - Špatně, Složitost algoritmu závisí na struktuře problému, ne na numerických hodnotách.

nejhůře polynomiální - Špatně, Vzhledem k charakterizaci podinstancí libovolnou podmnožinou uzlů může být složitost exponenciální.

---

Dynamické programování používá jako klíč k výběru z paměti řešení podinstancí dvojici diskrétních proměnných (p, q), kde rozsah hodnot p je dán v instanci, ale nesouvisí s její velikostí N, rozsah q je O(N^2). Složitost kompozice a dekompozice je konstantní. Algoritmus je

`💛 hint`

lineární

pseudopolynomiální

polynomiální

polynomiální ve velikosti instance

globální metoda

`answer`

`✅ correct`

pseudopolynomiální - Správně, Složitost algoritmu závisí na numerických hodnotách vstupu, což jej činí pseudopolynomiálním.

polynomiální ve velikosti instance - Správně, Celková složitost algoritmu je polynomiální ve velikosti instance vzhledem k rozsahu q.

globální metoda - Správně, Dynamické programování hledá globálně optimální řešení problému.

`❌ wrong`

lineární - Špatně, Vzhledem k rozsahu q, který je O(N^2), není algoritmus lineární.

polynomiální - Špatně, I když je složitost kompozice a dekompozice konstantní, celková složitost algoritmu závisí na specifických vlastnostech problému.

---

Dynamické programování používá jako klíč k výběru z paměti řešení podinstancí k-tici binárních proměnných, kde k = logN a N je velikost instance. Postup výpočtu je od triviálních podinstancí k finálnímu řešení, každou hodnotu je třeba vypočíst. Složitost kompozice a dekompozice je konstantní. Algoritmus je

`💛 hint`

lineární

pseudopolynomiální

polynomiální

exaktní metoda

`answer`

`✅ correct`

lineární - Správně, Použití logaritmického počtu proměnných a konstantní složitost kompozice a dekompozice naznačují, že algoritmus může být efektivně lineární.

polynomiální - Správně, Použití k-tice binárních proměnných, kde k je logaritmické v N, vede k polynomiální složitosti algoritmu.

exaktní metoda - Správně, Algoritmus poskytuje přesné řešení problému, čímž splňuje definici exaktní metody.

`❌ wrong`

pseudopolynomiální - Špatně, Algoritmus není pseudopolynomiální, protože jeho složitost závisí na logaritmické velikosti instance, což je charakteristika polynomiální složitosti.

---

Dynamické programování je aplikováno na problém, kde vstupní proměnné zobrazují graf s uzly očíslovanými 1…n, kde n je velikost instance a dále celé číslo K. Podinstance je tvořena prvními m - 1 hranami, kde m je počet hran právě dekomponované instance, každá podinstance může mít jiné K, nejvýše rovné log K právě dekomponované instance. Kompozice a dekompozice mají složitost Θ(log M). Existují instance, kde je třeba vyřešit všechny podinstance. Algoritmus

`💛 hint`

má lineární horní asymptotickou mez složitosti

má exponenciální dolní asymptotickou mez složitosti

má polynomiální horní asymptotickou mez složitosti

je pseudopolynomiální

`answer`

`✅ correct`

má polynomiální horní asymptotickou mez složitosti - Správně, S logaritmickou složitostí kompozice a dekompozice a s potřebou řešit všechny podinstance může celková složitost algoritmu dosahovat polynomiálních hodnot.

`❌ wrong`

má lineární horní asymptotickou mez složitosti - Špatně, Algoritmus využívá dekompozice a kompozice s logaritmickou složitostí, což spolu s potřebou řešit všechny podinstance naznačuje, že celková složitost může být větší než lineární.

má exponenciální dolní asymptotickou mez složitosti - Špatně, Zadání neudává přímé důvody pro exponenciální složitost; spíše naznačuje složitost závislou na logaritmických operacích.

je pseudopolynomiální - Špatně, Zadání neposkytuje dostatek informací k určení pseudopolynomiální povahy algoritmu.

---

Dynamické programování používá klíč k výběru z paměti řešení N-tici binárních čísel proměnných, kde N je velikost instance. Postup výpočtu je od triviálních podinstancí k finálnímu řešení, každou hodnotu je třeba vypočíst. Algoritmus je

`💛 hint`

Lineární

Pseudopolynomiální

Polynomiální

Lokální metoda

`answer`

`✅ correct`

Polynomiální - Správně, dynamické programování často vede k polynomiální časové složitosti díky efektivnímu využívání výsledků menších podproblémů.

`❌ wrong`

Lineární - Špatně, dynamické programování může mít různou časovou složitost, ne vždy je lineární.

Pseudopolynomiální - Špatně, i když pro některé specifické problémy může dynamické programování dosahovat pseudopolynomiální složitosti, nelze ho obecně označit za pseudopolynomiální.

Lokální metoda - Špatně, dynamické programování je globální metoda, protože hledá optimální řešení celého problému.

---

Dynamické programování používá jako klíč k výběru z paměti řešení podinstancí dvojici proměnných v rozsahu 0..n, kde n je velikost instance. Postup výpočtu je od triviálních podinstancí k finálnímu řešení, každou hodnotu je třeba vypočíst. Algoritmus je

`💛 hint`

exponenciální

pseudopolynomiální

lineární

polynomiální

kubický

`answer`

`✅ correct`

polynomiální - Správně, Rozsah proměnných a postup od triviálních podinstancí k finálnímu řešení naznačuje polynomiální složitost.

`❌ wrong`

exponenciální - Špatně, Použití dvojice proměnných v rozsahu 0..n neimplikuje nutně exponenciální složitost.

pseudopolynomiální - Špatně, Zadání neposkytuje dostatek důvodů pro klasifikaci jako pseudopolynomiální.

lineární - Špatně, Použití dvojic proměnných naznačuje složitější strukturu než lineární.

kubický - Špatně, Bez specifických důkazů pro kubickou složitost.

---

Dynamické programování je aplikováno na problém, kde vstupní proměnné zobrazují graf s uzly očíslovanými 1…n, kde n je velikost instance a dále celé číslo K. Podinstance je tvořena prvními K hranami, každá podinstance může mít jiné K. Kompozice a dekompozice mají konstantní složitost. Algoritmus

`💛 hint`

je pseudopolynomiální

má složitost nejméně exponenciální ve velikosti instance

má složitost nejméně kvadratickou ve velikosti instance

má složitost rostoucí nejhůře s třetí mocninou ve velikosti instance

`answer`

`✅ correct`

je pseudopolynomiální - Správně, S ohledem na variabilní K může být algoritmus klasifikován jako pseudopolynomiální, i když zde odpověď může být diskutabilní.

má složitost nejméně kvadratickou ve velikosti instance - Správně, Závislost na velikosti instance a na K může vést k vyšší složitosti, ale specifikace „nejméně kvadratická“ bez dalších důkazů je spekulativní.

má složitost rostoucí nejhůře s třetí mocninou ve velikosti instance - Správně, Bez konkrétních důkazů z textu zadání je těžké určit přesnou složitost, ale předpokládá se složitější výpočet než lineární či kvadratický.

`❌ wrong`

má složitost nejméně exponenciální ve velikosti instance - Špatně, Konstantní složitost kompozice a dekompozice neimplikuje nutně exponenciální složitost.

---

Dynamické programování je aplikováno na permutační problém, instance je množina velikosti n. Dekompozice má složitost Θ (n^2), kde n je velikost původně zadané instance. Podinstance je charakterizována libovolnou podmnožinou původní množiny. Existují instance, na kterých je nutno vypočíst všechny podinstance Algoritmus

`💛 hint`

má exponenciální dolní asymptotickou mez složitosti

pseudopolynomiální

polynomiální

má horní asymptotickou mez složitosti O(n^2.2^n)

`answer`

`✅ correct`

má exponenciální dolní asymptotickou mez složitosti - Správně, Nutnost vypočítat všechny podmnožiny původní množiny vede k exponenciální složitosti.

má horní asymptotickou mez složitosti O(n^2.2^n) - Správně, Dekompozice má kvadratickou složitost a nutnost vypočítat všechny podmnožiny vede k exponenciálnímu faktoru.

`❌ wrong`

pseudopolynomiální - Špatně, Exponenciální složitost vylučuje pseudopolynomiální klasifikaci.

polynomiální - Špatně, Exponenciální povaha výpočtu vylučuje polynomiální složitost.

---

Dynamické programování je aplikováno na permutační problém, instance je množina velikosti n. Dekompozice má složitost Θ(n), kde n je velikost původně zadané instance. Podinstance je charakterizována libovolnou podmnožinou původní množiny. Existují instance, na kterých je nutno vypočíst všechny podinstance. Algoritmus

`💛 hint`

je nejvýše polynomiální

je O(2^n)

je pseudopolynomiální

je polynomiální ve velikosti instance

`answer`

`✅ correct`

je O(2^n) - Správně, vzhledem k potřebě vypočítat všechny podmnožiny původní množiny, což znamená exponenciální počet podinstancí vzhledem k velikosti vstupní množiny n.

`❌ wrong`

je nejvýše polynomiální - Špatně, Nutnost vypočítat všechny podmnožiny vede k exponenciální složitosti.

je pseudopolynomiální - Špatně, Exponenciální složitost vylučuje pseudopolynomiální klasifikaci.

je polynomiální ve velikosti instance - Špatně, Exponenciální povaha výpočtu vylučuje polynomiální složitost.

---

Dynamické programování vybírá optimální podmnožinu množiny, jejíž velikost je velikostí instance. Podinstance je charakterizována libovolnou podmnožinou v instanci. Postup výpočtu je od triviálních podinstancí k finálnímu řešení. Každou hodnotu je třeba vypočíst. Horní asymptotická mez složitosti je

`💛 hint`

exponenciální

kvadratická

lineární

polynomiální

`answer`

`✅ correct`

exponenciální - Správně, Potřeba vypočítat všechny podmnožiny vede k exponenciální složitosti.

`❌ wrong`

kvadratická - Špatně, Exponenciální povaha problému vylučuje kvadratickou složitost.

lineární - Špatně, Exponenciální povaha výpočtu vylučuje lineární složitost.

polynomiální - Špatně, Exponenciální povaha problému vylučuje polynomiální složitost.

---

Dynamické programování je aplikováno na grafový problém. Podinstance je charakterizována podmnožinou uzlů (libovolnou). Existují instance, na kterých je nutno všechny podinstance vypočíst. Velikost instance se měří počtem uzlů. Algoritmus je

`💛 hint`

globální metoda

pseudopolynomiální

lineární

polynomiální

`answer`

`✅ correct`

globální metoda - Správně, Dynamické programování hledá optimální řešení problému jako celku, což je charakteristika globální metody.

`❌ wrong`

pseudopolynomiální - Špatně, Potřeba vypočítat všechny podmnožiny uzlů vede spíše k exponenciální složitosti.

lineární - Špatně, Složitost výpočtu všech podinstancí vede k vyšší než lineární složitosti.

polynomiální - Špatně, Exponenciální povaha problému vylučuje polynomiální složitost.

---

Dynamické programování je aplikováno na grafový problém. Velikost instance se měří počtem uzlů. Podinstance je charakterizována podmnožinou uzlů (libovolnou). Kompozice je v konstantním čase. Postup výpočtu je od triviálních podinstancí k finálnímu řešení, každou hodnotu je třeba vypočíst. Horní asymptotická mez složitosti algoritmu je

`💛 hint`

lineární

kvadratická

polynomiální

exponenciální

`answer`

`✅ correct`

exponenciální - Správně, Potřeba vypočítat každou podmnožinu uzlů vede k exponenciální složitosti.

`❌ wrong`

lineární - Špatně, Vzhledem k potřebě vypočítat každou podmnožinu uzlů, složitost není omezena na lineární.

kvadratická - Špatně, Složitost přesahuje polynomiální rámec kvůli potřebě vypočítat všechny podmnožiny.

polynomiální - Špatně, Vzhledem k exponenciálnímu počtu podmnožin uzlů v grafu není složitost polynomiální.

---

# Simulovaná evoluce

Evoluční programování pracuje nad

`💛 hint`

stromovou reprezentací programu

reprezentací automatu

lineární reprezentací strojového kódu

orientovaným acyklickým grafem datových závislostí

`answer`

`✅ correct`

reprezentací automatu - Správně, Evoluční programování může pracovat s automaty jako formou reprezentace pro řešení určitých typů problémů.

`❌ wrong`

stromovou reprezentací programu - Špatně, Evoluční programování typicky pracuje nad jinými formami reprezentace než jsou stromové struktury programů.

lineární reprezentací strojového kódu - Špatně, Toto není typická reprezentace používaná v evolučním programování.

orientovaným acyklickým grafem datových závislostí - Špatně, Tato forma reprezentace není běžně spojována s evolučním programováním.

---

Evoluční strategie pracuje nad reprezentací

`💛 hint`

vektoru reálných čísel a odchylek

rozkladového stromu výrazu

binárního řetězu

automatu

`answer`

`✅ correct`

vektoru reálných čísel a odchylek - Správně, Evoluční strategie často pracují s vektory reálných čísel a odchylek jako základem pro optimalizaci.

`❌ wrong`

rozkladového stromu výrazu - Špatně, Tato reprezentace není typická pro evoluční strategie.

binárního řetězu - Špatně, Evoluční strategie se obvykle nezaměřují na binární reprezentace.

automatu - Špatně, Reprezentace automatu není charakteristická pro evoluční strategie.

---

Podle teorie stavebních bloků

`💛 hint`

složitější schémata (vyššího řádu) přežívají lépe

schémata, jejichž proměnné jsou rozptýleny po celém genotypu, přežívají hůře

mutace zhoršuje přežívání všech schémat (i když ne všech stejně)

uvažované jednobodové křížení má za následek závislost přežívání na délce schématu

`answer`

`✅ correct`

schémata, jejichž proměnné jsou rozptýleny po celém genotypu, přežívají hůře - Správně, Dlouhá schémata s rozptýlenými proměnnými jsou náchylnější k narušení křížením.

mutace zhoršuje přežívání všech schémat (i když ne všech stejně) - Správně, Mutace může narušit schémata, čímž zhoršuje jejich šance na přežití.

uvažované jednobodové křížení má za následek závislost přežívání na délce schématu - Správně, Jednobodové křížení může snadněji narušit dlouhá schémata, což ovlivňuje jejich přežití.

`❌ wrong`

složitější schémata (vyššího řádu) přežívají lépe - Špatně, Teorie stavebních bloků naznačuje, že krátká, nízkořádová, vysoce fit schémata mají lepší šance na přežití.

---

# Genetický algoritmus

V genetickém algoritmu je třeba zpomalit konvergenci. Možností je upravit pravděpodobnost mutace a nebo upravit selekční tlak. Platí

`💛 hint`

přednostně snížíme selekční tlak

přednostně zvýšíme pravděpodobnost mutace

pokud snížíme selekční tlak, může dojít k divergenci a je třeba snížit i pravděpodobnost mutace

`answer`

`✅ correct`

přednostně snížíme selekční tlak - Správně, Snížení selekčního tlaku může pomoci zachovat diverzitu v populaci a zpomalit konvergenci.

pokud snížíme selekční tlak, může dojít k divergenci a je třeba snížit i pravděpodobnost mutace - Správně, Úprava selekčního tlaku a mutace musí být vyvážena k udržení optimální explorace a exploatace.

`❌ wrong`

přednostně zvýšíme pravděpodobnost mutace - Špatně, Zvýšení pravděpodobnosti mutace může vést k větší exploraci, ale také k destabilizaci populace.

---

V genetickém algoritmu je třeba zpomalit konvergenci. Pravděpodobně bude účinné

`💛 hint`

upravit koeficienty lineárního škálování, pokud je použito

přejít od výběru ruletou k výběru turnajem při zachování selekčního tlaku

zvětšit velikost turnaje, pokud je použit

`answer`

`✅ correct`

upravit koeficienty lineárního škálování, pokud je použito - Správně, Úprava škálování může pomoci kontrolovat selekční tlak a zpomalit konvergenci.

`❌ wrong`

přejít od výběru ruletou k výběru turnajem při zachování selekčního tlaku - Špatně, Tato změna sama o sobě nemusí zpomalit konvergenci; záleží na implementaci a parametrech selekce.

zvětšit velikost turnaje, pokud je použit - Špatně, Zvětšení velikosti turnaje obvykle zvyšuje selekční tlak, což by konvergenci spíše urychlilo.

---

V genetickém algoritmu je třeba urychlit konvergenci. Možností je upravit pravděpodobnost mutace nebo selekci. Platí

`💛 hint`

změna selekčního mechanismu nemá významný vliv, pokud zachováme selekční tlak

přednostně zvýšíme pravděpodobnost mutace

přednostně zvýšíme selekční tlak, pracujeme s minimální potřebnou mutací

`answer`

`✅ correct`

změna selekčního mechanismu nemá významný vliv, pokud zachováme selekční tlak - Správně, Důležitý je celkový selekční tlak, ne konkrétní mechanismus selekce.

přednostně zvýšíme selekční tlak, pracujeme s minimální potřebnou mutací - Správně, Zvýšení selekčního tlaku může urychlit konvergenci tím, že preferuje lepší jedince.

`❌ wrong`

přednostně zvýšíme pravděpodobnost mutace - Špatně, Zvýšení pravděpodobnosti mutace nemusí nutně urychlit konvergenci a může vést k větší náhodnosti.

---

Genetický algoritmus dobře konverguje až do určité vzdálenosti od předpokládaného globálního minima, pak začne divergovat. Příčina může být

`💛 hint`

povaha stavového prostoru („landscape“) se v okolí globálního minima prudce změní

pracuje s příliš malou pravděpodobností mutace

adaptace selekčního tlaku nepracuje dostatečně dobře

`answer`

`✅ correct`

povaha stavového prostoru („landscape“) se v okolí globálního minima prudce změní - Správně, Náhlá změna v povaze stavového prostoru může způsobit, že algoritmus ztratí schopnost efektivně navigovat k optimu.

adaptace selekčního tlaku nepracuje dostatečně dobře - Správně, Neadekvátní adaptace selekčního tlaku může způsobit, že algoritmus není schopen udržet potřebnou diverzitu populace v pozdějších fázích hledání.

`❌ wrong`

pracuje s příliš malou pravděpodobností mutace - Špatně, Příliš malá pravděpodobnost mutace typicky nevede k divergenci, ale může způsobit předčasnou konvergenci.

---

Algoritmus, který má za běhu upravovat selekční tlak v genetickém algoritmu s lineárním škálováním, bude přímo nastavovat

`💛 hint`

pravděpodobnost mutace

konstanty přepočtu zdatnosti

pravděpodobnost výběru nejlepšího jedince

`answer`

`✅ correct`

konstanty přepočtu zdatnosti - Správně, Konstanty přepočtu zdatnosti v lineárním škálování přímo ovlivňují selekční tlak.

`❌ wrong`

pravděpodobnost mutace - Špatně, Pravděpodobnost mutace ovlivňuje variabilitu populace, ale ne selekční tlak.

pravděpodobnost výběru nejlepšího jedince - Špatně, Pravděpodobnost výběru nejlepšího jedince není obvykle přímo nastavována v kontextu lineárního škálování.

---

Algoritmus, který má za běhu upravovat selekční tlak v genetickém algoritmu, může být založen na zjištění

`💛 hint`

diverzity jedinců

změny průměrné zdatnosti mezi generacemi

poměru zdatnosti např. nejzdatnějšího jedince a jedince v polovině pořadí

`answer`

`✅ correct`

diverzity jedinců - Správně, Měření diverzity jedinců pomáhá určit, zda populace ztrácí genetickou variabilitu.

změny průměrné zdatnosti mezi generacemi - Správně, Sledování změn průměrné zdatnosti může poskytnout vhled do dynamiky konvergenci.

poměru zdatnosti např. nejzdatnějšího jedince a jedince v polovině pořadí - Správně, Tento poměr může indikovat, jak rychle populace konverguje a zda je selekční tlak příliš vysoký nebo nízký.

---

Algoritmus, který má za běhu upravovat selekční tlak v genetickém algoritmu používajícím lineární škálování a ruletový výběr, bude přímo nastavovat

`💛 hint`

pravděpodobnost mutace

výseče rulety

koeficienty lineárního škálování

`answer`

`✅ correct`

koeficienty lineárního škálování - Správně, Koeficienty lineárního škálování přímo ovlivňují distribuci selekčního tlaku.

`❌ wrong`

pravděpodobnost mutace - Špatně, To není přímý způsob, jak upravit selekční tlak v kontextu lineárního škálování a ruletového výběru.

výseče rulety - Špatně, Výseče rulety jsou určeny zdatností jedinců, která je ovlivněna škálováním.

---

Algoritmus, který má za běhu upravovat selekční tlak v genetickém algoritmu s výběrem ruletou, může přímo nastavovat

`💛 hint`

konstantní převod ranku (pořadí zdatnosti) na pravděpodobnost výběru

konstanty lineárního škálování

pravděpodobnost aplikace operátoru „cut and splice“

`answer`

`✅ correct`

konstantní převod ranku (pořadí zdatnosti) na pravděpodobnost výběru - Správně, Toto je jedna z metod, jak ovlivnit selekční tlak ve výběru ruletou.

konstanty lineárního škálování - Správně, I když je výběr ruletou založen na zdatnosti, lineární škálování může upravit rozložení pravděpodobnosti výběru.

`❌ wrong`

pravděpodobnost aplikace operátoru „cut and splice“ - Špatně, Toto se týká operací na genotypu, nikoli selekčního tlaku.

---

Máte vyhodnotit, zda algoritmus, který automaticky udržuje selekční tlak v genetickém algoritmu, pracuje uspokojivě. Provedete následující

`💛 hint`

Budete měřit četnost mutace v závislosti na poměrné zdatnosti.

Budete měřit četnost výběru (selekce) v závislosti na poměrné zdatnosti.

Pro každou velikost instance zvolíte jednu instanci.

Zvolíte jednu velikost instance a použijete instance rozdílné obtížnosti.

`answer`

`✅ correct`

Budete měřit četnost výběru (selekce) v závislosti na poměrné zdatnosti. - Správně, To pomůže zjistit, jak dobře algoritmus udržuje selekční tlak a zda podporuje diverzitu.

`❌ wrong`

Budete měřit četnost mutace v závislosti na poměrné zdatnosti. - Špatně, Četnost mutace neukazuje efektivitu udržování selekčního tlaku.

Pro každou velikost instance zvolíte jednu instanci. - Špatně, To neukáže, jak algoritmus reaguje na různé úrovně selekčního tlaku v různých instancích.

Zvolíte jednu velikost instance a použijete instance rozdílné obtížnosti. - Špatně, To by nebylo účinné pro hodnocení selekčního tlaku, jelikož se zaměřuje na obtížnost, nikoli na dynamiku selekčního tlaku.

---

Selekční tlak ve standardním genetickém algoritmu lze řídit

`💛 hint`

zhruba ve stejném rozsahu při selekci turnajem i ruletou

ve větším rozsahu při výběru univerzálním stochastickým vzorkováním

parametry lineárního škálování

`answer`

`✅ correct`

zhruba ve stejném rozsahu při selekci turnajem i ruletou - Správně, Oba mechanismy umožňují určitou úpravu selekčního tlaku.

parametry lineárního škálování - Správně, Lineární škálování umožňuje přizpůsobit rozložení zdatnosti a tím ovlivnit selekční tlak.

`❌ wrong`

ve větším rozsahu při výběru univerzálním stochastickým vzorkováním - Špatně, Univerzální stochastické vzorkování není zmiňováno jako metoda s větším rozsahem pro řízení selekčního tlaku.

---

Volba selekčního tlaku v genetických algoritmech

`💛 hint`

je omezena hrozbou divergence při malém selekčním tlaku

závisí na obtížnosti instance, obtížnější instance vyžadují pomalejší konvergenci

může vyžadovat odpovídající nastavení pravděpodobnosti funkce

`answer`

`✅ correct`

je omezena hrozbou divergence při malém selekčním tlaku - Správně, Příliš malý selekční tlak může vést k ztrátě konvergenční schopnosti algoritmu.

závisí na obtížnosti instance, obtížnější instance vyžadují pomalejší konvergenci - Správně, Pro složitější problémy může být výhodné zpomalit konvergenci, aby se algoritmus mohl lépe adaptovat a prozkoumat prostor řešení.

může vyžadovat odpovídající nastavení pravděpodobnosti funkce - Správně, Aby bylo možné efektivně prozkoumat stavový prostor a zároveň udržet potřebnou diverzitu populace, může být nutné upravit pravděpodobnost aplikace genetických operátorů.

---

Genetické operátory Fast Messy GA algoritmu pracují nad

`💛 hint`

reprezentací individua

zdatností individua

množinami hodnot genů

reprezentací individua, kde některé geny nejsou ohodnoceny a některé jsou ohodnoceny víckrát

`answer`

`✅ correct`

množinami hodnot genů - Správně, Fast Messy GA se zaměřuje na manipulaci s fragmenty genetické informace.

reprezentací individua, kde některé geny nejsou ohodnoceny a některé jsou ohodnoceny víckrát - Správně, Fast Messy GA umožňuje, aby některé geny byly ohodnoceny vícekrát nebo vůbec.

`❌ wrong`

reprezentací individua - Špatně, Fast Messy GA pracuje spíše s množinami hodnot genů než s celkovou reprezentací individua.

zdatností individua - Špatně, Zdatnost individua je výsledkem procesu, ale není přímo manipulována genetickými operátory.

---

Genetické operátory Fast Messy GA algoritmu pracují s

`💛 hint`

reprezentací individua

podmnožinami genů

fenotypem individua

zdatností individua

`answer`

`✅ correct`

podmnožinami genů - Správně, Fast Messy GA se specializuje na práci s podmnožinami genů.

`❌ wrong`

reprezentací individua

fenotypem individua - Špatně, Fast Messy GA se soustředí více na genotyp než na fenotyp.

zdatností individua - Špatně, Zdatnost je spíše výsledkem než předmětem manipulace v Fast Messy GA.

---

Základní metodou vyhodnocení, se kterou pracuje Fast Messy genetický algoritmus, je

`💛 hint`

stanovení fenotypu přímo z hodnot genů daného jedince a následný výpočet zdatnosti

výpočet odlišnosti genotypu jedince od referenčního jedince

založena na průměrné délce fragmentu v dané generaci

dosazení hodnot fragmentů do referenčního jedince a výpočet jeho zdatnosti

`answer`

`✅ correct`

dosazení hodnot fragmentů do referenčního jedince a výpočet jeho zdatnosti - Správně, V Fast Messy GA se hodnotí jedinci tím, že se fragmenty genů kombinují s referenčním jedincem.

`❌ wrong`

stanovení fenotypu přímo z hodnot genů daného jedince a následný výpočet zdatnosti - Špatně, Fast Messy GA nepracuje přímo s fenotypem jedince.

výpočet odlišnosti genotypu jedince od referenčního jedince - Špatně, Toto není typická metoda pro Fast Messy GA.

založena na průměrné délce fragmentu v dané generaci - Špatně, To není hlavní metoda vyhodnocení v Fast Messy GA.

---

Genetický algoritmus s pravděpodobností mutace 40% připomíná

`💛 hint`

metodu pouze nejlepší

náhodnou procházku

zaujatou náhodou procházku

`answer`

`✅ correct`

náhodnou procházku - Správně, Vysoká pravděpodobnost mutace může vést k náhodnému prohledávání stavového prostoru, což připomíná náhodnou procházku.

`❌ wrong`

metodu pouze nejlepší - Špatně, Vysoká pravděpodobnost mutace není typická pro metodu pouze nejlepší.

zaujatou náhodou procházku - Špatně, I když je pravděpodobnost mutace vysoká, neznamená to nutně, že procházka je zaujatá.

---

Stavební bloky ve Fast Messy GA se generují

`💛 hint`

jako podmnožiny ohodnocených genů zadané délky

jako reprezentace počáteční populace

jako fenotyp individua

jako podmnožiny genů zadaného referenčního individua

`answer`

`✅ correct`

jako podmnožiny ohodnocených genů zadané délky - Správně, Fast Messy GA generuje stavební bloky jako podmnožiny genů s určitou délkou.

`❌ wrong`

jako reprezentace počáteční populace - Špatně, Stavební bloky nejsou vytvářeny jako reprezentace celé počáteční populace.

jako fenotyp individua - Špatně, Stavební bloky jsou založeny na genetických fragmentech, nikoli na fenotypech.

jako podmnožiny genů zadaného referenčního individua - Špatně, Stavební bloky nejsou omezeny pouze na geny referenčního jedince.

---

Stavební blok ve Fast Messy GA je vždy

`💛 hint`

reprezentace individua

ohodnocení podmnožiny genů

fenotyp individua

podmnožina genů referenčního individua

`answer`

`✅ correct`

ohodnocení podmnožiny genů - Správně, Stavební bloky ve Fast Messy GA jsou ohodnocené fragmenty genů.

`❌ wrong`

reprezentace individua - Špatně, Stavební blok je spíše fragmentem genů než celkovou reprezentací jedince.

fenotyp individua - Špatně, Stavební bloky nejsou definovány jako fenotypy jedinců.

podmnožina genů referenčního individua - Špatně, Stavební bloky nejsou omezeny na geny referenčního jedince.

---

Vnější cyklus fmGA postupně zvyšuje

`💛 hint`

složitost referenčního individua

cílovou velikost fragmentů po generování

délku referenčního individua

selekční tlak

`answer`

`✅ correct`

cílovou velikost fragmentů po generování - Správně, Vnější cyklus fmGA zvyšuje velikost fragmentů, které jsou generovány a kombinovány.

`❌ wrong`

složitost referenčního individua - Špatně, Vnější cyklus Fast Messy GA se netýká přímo složitosti referenčního jedince.

délku referenčního individua - Špatně, Délka referenčního jedince není přímo zvyšována vnějším cyklem.

selekční tlak - Špatně, Vnější cyklus se zaměřuje na velikost fragmentů, ne přímo na selekční tlak.

---

Referenční jedinec v fmGA

`💛 hint`

slouží pro vyhodnocení zdatnosti

slouží pro konstrukci stochastického modelu

při použití, jeho proměnné nahrazují proměnné fragmentů genetické informace

při použití, jeho proměnné jsou nahrazovány proměnnými fragmentů genetické informace

`answer`

`✅ correct`

slouží pro vyhodnocení zdatnosti - Správně, Referenční jedinec je používán pro vyhodnocení zdatnosti kombinací s fragmenty genů.

při použití, jeho proměnné jsou nahrazovány proměnnými fragmentů genetické informace - Správně, V procesu Fast Messy GA mohou být proměnné referenčního jedince nahrazeny nebo doplněny fragmenty.

`❌ wrong`

slouží pro konstrukci stochastického modelu - Špatně, Referenční jedinec slouží především pro vyhodnocení, nikoli pro konstrukci modelu.

při použití, jeho proměnné nahrazují proměnné fragmentů genetické informace - Špatně, To by bylo spíše naopak - proměnné fragmentů mohou nahradit proměnné v referenčním jedinci.

---

Ranking v genetickém algoritmu

`💛 hint`

nastavuje velikost turnaje

ovlivní pravděpodobnost výběru nejzdatnějšího jedince

v dané generaci, může způsobit zmenšení selekčního tlaku

v dané generaci, může způsobit zvětšení selekčního tlaku

`answer`

`✅ correct`

ovlivní pravděpodobnost výběru nejzdatnějšího jedince - Správně, Ranking jedinců podle zdatnosti určuje, kdo má větší šanci být vybrán pro reprodukci.

v dané generaci, může způsobit zmenšení selekčního tlaku - Správně, Pokud je ranking použit k vyrovnání šancí, může to snížit selekční tlak tím, že dává šanci i méně zdatným jedincům.

v dané generaci, může způsobit zvětšení selekčního tlaku - Správně, Naopak, přiřazením vyšší pravděpodobnosti výběru zdatnějším jedincům se může selekční tlak zvýšit.

`❌ wrong`

nastavuje velikost turnaje - Špatně, Ranking sám o sobě neurčuje velikost turnaje, ale může ovlivnit selekci jedinců na základě jejich zdatnosti.

---

Genetický algoritmus je aplikován v situaci, kdy některé části stavového prostoru mají výrazně větší hloubku než jiné. Využijeme

`💛 hint`

konstantní poměrně vysokou míru mutace, aby se populace snáze dostala do “vlídnějších kočin”

některých vlastností lineárního škálování

některé metody automatického řízení selekčního tlaku

`answer`

`✅ correct`

některých vlastností lineárního škálování - Správně, Lineární škálování může pomoci přizpůsobit selekční tlak a zlepšit průzkum prostoru tím, že se přizpůsobuje různým hloubkám stavového prostoru.

některé metody automatického řízení selekčního tlaku - Správně, Metody automatického řízení selekčního tlaku umožňují dynamicky upravovat intenzitu selekce v průběhu evoluce populace. Tím se zlepšuje schopnost algoritmu adaptovat se.

`❌ wrong`

konstantní poměrně vysokou míru mutace, aby se populace snáze dostala do “vlídnějších kočin” - Špatně, Vysoká míra mutace může vést k náhodnému prohledávání a ztrátě dobrých řešení, spíše než cílenému průzkumu prostoru.

---


# Relaxace 

Relaxace v iterativních lokálních heuristikách

`💛 hint`

nezávisí na vlastnostech konkrétní konfigurace, vyjadřuje pouze fakt, že řešením není

zhoršuje dosažitelnost ve stavovém prostoru

typicky nahrazuje optimalizační kritérium heuristickou kombinací původního opt. kritéria a odhadu vzdálenosti konfigurace od řešení

spočívá v použití snadných instancí pro závěrečné vyhodnocení

má za úkol vést iterace od konfigurací, které řešením nejsou, k řešením

zlepšuje dosažitelnost ve stavovém prostoru

`answer`

`✅ correct`

typicky nahrazuje optimalizační kritérium heuristickou kombinací původního opt. kritéria a odhadu vzdálenosti konfigurace od řešení - Správně, Relaxace často zahrnuje modifikaci optimalizačního kritéria pro lepší navigaci ve stavovém prostoru.

má za úkol vést iterace od konfigurací, které řešením nejsou, k řešením - Správně, Relaxace usnadňuje postup od neoptimálních konfigurací k optimálním.

zlepšuje dosažitelnost ve stavovém prostoru - Správně, Relaxace pomáhá zlepšit průzkum stavového prostoru a dosáhnout lepších řešení.

`❌ wrong`

nezávisí na vlastnostech konkrétní konfigurace, vyjadřuje pouze fakt, že řešením není - Špatně, Relaxace často závisí na konkrétních vlastnostech konfigurace a jejím vztahu k řešení.

zhoršuje dosažitelnost ve stavovém prostoru - Špatně, Cílem relaxace je spíše zlepšit dosažitelnost než ji zhoršovat.

spočívá v použití snadných instancí pro závěrečné vyhodnocení - Špatně, Relaxace se týká změny kritérií nebo omezení, nikoli použití snadných instancí.

---

Relaxace v iterativních lokálních heuristikách

`💛 hint`

v případě 3-SAT, spočívá ve snížení počtu klauzulí instance

má za úkol opravit konfiguraci tak, aby byla řešením

přiřazuje všem konfiguracím, které nejsou řešením, hodnotu konstantní pro danou instanci

typicky nahrazuje optimalizační kritérium pouze odhadem vzdálenosti konfigurace od řešení

typicky nahrazuje optimalizační kritérium stanovenou konstantní pokutou

`answer`

`❌ wrong`

v případě 3-SAT, spočívá ve snížení počtu klauzulí instance - Špatně, Relaxace v 3-SAT by se spíše zaměřila na modifikaci kritérií než na snížení počtu klauzulí.

má za úkol opravit konfiguraci tak, aby byla řešením - Špatně, Cílem relaxace není přímo opravit konfiguraci, ale umožnit lepší navigaci k řešení.

přiřazuje všem konfiguracím, které nejsou řešením, hodnotu konstantní pro danou instanci - Špatně, To není typický přístup relaxace v iterativních heuristikách.

typicky nahrazuje optimalizační kritérium pouze odhadem vzdálenosti konfigurace od řešení - Špatně, Relaxace obvykle kombinuje několik kritérií, ne nahrazuje je pouze odhadem vzdálenosti.

typicky nahrazuje optimalizační kritérium stanovenou konstantní pokutou - Špatně, Relaxace zahrnuje komplexnější úpravy než pouhé použití konstantní pokuty.

---

Relaxace v iterativních lokálních heuristikách

`💛 hint`

obvykle obsahuje numerický parametr, který je nutno experimentálně nastavit

spočívá v použití malých instancí

Přiřazuje všem konfiguracím, které nejsou řešením, hodnotu konstantní pro danou instanci

Slouží pouze při porovnání konfigurací pro přijetí tahu

`answer`

`✅ correct`

obvykle obsahuje numerický parametr, který je nutno experimentálně nastavit - Správně, Mnoho relaxačních metod vyžaduje nastavení specifických parametrů, které jsou často určeny experimentálně.

`❌ wrong`

spočívá v použití malých instancí - Špatně, Velikost instance není obvykle klíčovým faktorem v relaxaci.

Přiřazuje všem konfiguracím, které nejsou řešením, hodnotu konstantní pro danou instanci - Špatně, Relaxace obvykle pracuje s diferencovanějšími hodnotami než s jednou konstantní hodnotou pro všechny neřešící konfigurace.

Slouží pouze při porovnání konfigurací pro přijetí tahu - Špatně, Relaxace má širší aplikaci než pouze v přijímání tahů.

---

# Simulované ochlazování

Máte experimentálně vyhodnotit, zda chování algoritmu, který automaticky nastavuje počáteční teplotu simulovaného ochlazování, odpovídá teorii, kterou jste vymysleli, a která zahrnuje několik parametrů instance. Zajímá vás také, zda tyto parametry stačí k charakterizaci instance z hlediska práce algoritmu

`💛 hint`

Použijete reprezentativní mix praktických instancí.

Výpočet spustíte opakovaně pro každou instanci.

Použijete vygenerované instance se stejnými hodnotami parametrů, o kterých se hovoří ve Vaší teorii, ale různé velikosti.

Použijete vygenerované instance s různými hodnotami parametrů, o kterých se hovoří ve Vaší teorii.

`answer`

`✅ correct`

Výpočet spustíte opakovaně pro každou instanci. - Správně, Opakované spuštění poskytuje data pro statistickou analýzu a ověření konzistence chování algoritmu.

Použijete vygenerované instance se stejnými hodnotami parametrů, o kterých se hovoří ve Vaší teorii, ale různé velikosti. - Správně, To umožní zjistit, jak velikost instance ovlivňuje chování algoritmu vzhledem k teoretickým parametrům.

Použijete vygenerované instance s různými hodnotami parametrů, o kterých se hovoří ve Vaší teorii. - Správně, Různé hodnoty parametrů umožní testovat různé aspekty teorie.

`❌ wrong`

Použijete reprezentativní mix praktických instancí. - Špatně, Pro experimentální ověření teorie je důležité mít specifické, dobře definované instance.

---

Máte experimentálně vyhodnotit, zda algoritmus, který automaticky nastavuje počáteční teplotu simulovaného ochlazování, pracuje uspokojivě

`💛 hint`

Zvolíte jeden parametr instancí, o kterých se domníváte, že na počáteční teplotu má vliv, a zkonstruujete zkušební instance.

Zvolíte velikost instance, na které budete experiment provádět.

Použijete instance s rozdílnou hloubkou lokálních minim.

Budete sledovat, zda rychlost ochlazování v algoritmu dává přiměřeně rychlou konvergenci pro nastavenou teplotu.

Použijete instance různé velikosti

Výpočet spustíte opakovaně pro každou instanci

Použijete větší počet lehkých instancí k urychlení

`answer`

`✅ correct`

Použijete instance s rozdílnou hloubkou lokálních minim. - Správně, To pomůže posoudit, jak dobře algoritmus zvládá různé topologie problému.

Budete sledovat, zda rychlost ochlazování v algoritmu dává přiměřeně rychlou konvergenci pro nastavenou teplotu. - Správně, Rychlost ochlazování je klíčovým faktorem pro dosažení účinné konvergence.

Použijete instance různé velikosti - Správně, Různé velikosti instancí umožní zjistit, jak velikost ovlivňuje výkon algoritmu.

Výpočet spustíte opakovaně pro každou instanci - Správně, Opakované spuštění zajistí spolehlivější výsledky.

`❌ wrong`

Zvolíte jeden parametr instancí, o kterých se domníváte, že na počáteční teplotu má vliv, a zkonstruujete zkušební instance. - Špatně, Pro komplexní evaluaci je důležité zvážit více parametrů.

Zvolíte velikost instance, na které budete experiment provádět. - Špatně, Omezení se pouze na jednu velikost instance může poskytnout neúplný obraz o chování algoritmu.

Použijete větší počet lehkých instancí k urychlení - Špatně, Použití pouze lehkých instancí může poskytnout zkreslený obraz o výkonu algoritmu.

---

Máte experimentálně vyhodnotit, zda Vámi navržené nastavení simulovaného ochlazování má dostatečnou iterativní sílu

`💛 hint`

Budete měřit závislost času výpočtu na velikost instance.

Budete měřit kvalitu výsledku pro více různých počátečních řešení.

Soubor zkušebních instancí můžete omezit na menší instance.

Výpočet spustíte opakovaně pro každou instanci a počáteční řešení.

`answer`

`✅ correct`

Budete měřit kvalitu výsledku pro více různých počátečních řešení. - Správně, Toto umožní posoudit, jak dobře nastavení funguje napříč různými podmínkami.

Výpočet spustíte opakovaně pro každou instanci a počáteční řešení. - Správně, Opakování experimentů zvyšuje spolehlivost výsledků.

`❌ wrong`

Budete měřit závislost času výpočtu na velikost instance. - Špatně, Čas výpočtu sám o sobě neodráží iterativní sílu nastavení.

Soubor zkušebních instancí můžete omezit na menší instance. - Špatně, Pouze malé instance nemusí poskytnout úplný obraz o efektivitě nastavení.

---

Heuristika, která nastavuje parametry simulovaného ochlazování

`💛 hint`

vždy bude brát v úvahu rozsah optimalizačního kritéria nebo jej normovat

pokud zjistí hloubku lokálních minim, dá se tato hodnota využít

efekt, dosažený manipulací s hloubkou ekvilibria, se dá dosáhnout manipulací s koeficientem ochlazování

`answer`

`✅ correct`

vždy bude brát v úvahu rozsah optimalizačního kritéria nebo jej normovat - Správně, Normování rozsahu optimalizačního kritéria pomáhá zajistit, že parametry ochlazování jsou relevantní pro škálu problému.

pokud zjistí hloubku lokálních minim, dá se tato hodnota využít - Správně, Znalost hloubky lokálních minim může pomoci přizpůsobit nastavení ochlazování pro lepší navigaci ve stavovém prostoru.

efekt, dosažený manipulací s hloubkou ekvilibria, se dá dosáhnout manipulací s koeficientem ochlazování - Správně, Ajustace koeficientu ochlazování může ovlivnit, jak rychle algoritmus překonává lokální minima.

---

Volba počáteční teploty v simulovaném ochlazování

`💛 hint`

pro dosažení nejlepšího výsledku, může vyžadovat odpovídající volbu koeficientu ochlazování

závisí na obtížnosti konkrétní instance

závisí na rozsahu optimalizačního kritéria dané instance

`answer`

`✅ correct`

pro dosažení nejlepšího výsledku, může vyžadovat odpovídající volbu koeficientu ochlazování - Správně, Oba parametry, počáteční teplota a koeficient ochlazování, jsou zásadní pro účinnost algoritmu.

závisí na obtížnosti konkrétní instance - Správně, Obtížnost a charakteristika instance mohou ovlivnit optimální volbu počáteční teploty.

závisí na rozsahu optimalizačního kritéria dané instance - Správně, Rozsah optimalizačního kritéria může ovlivnit, jak je nastavena počáteční teplota, aby bylo možné efektivně prozkoumat stavový prostor.

---

Koncová teplota v simulovaném ochlazování

`💛 hint`

je-li dost nízká, určuje, jak velká část stavového prostoru bude prohledávána

vždy musí zůstat konstantní, pokud se mění počáteční teplota

dá se s výhodou určovat za běhu sledováním konvergence

`answer`

`✅ correct`

dá se s výhodou určovat za běhu sledováním konvergence - Správně, Určování koncové teploty za běhu může pomoci optimalizovat proces ochlazování podle aktuálních potřeb a konvergence algoritmu.

`❌ wrong`

je-li dost nízká, určuje, jak velká část stavového prostoru bude prohledávána - Špatně, Koncová teplota určuje, kdy algoritmus skončí, ale ne nutně, jak velká část stavového prostoru bude prozkoumána.

vždy musí zůstat konstantní, pokud se mění počáteční teplota - Špatně, Koncová teplota může být nastavena nezávisle na počáteční teplotě.

---

Máte udělat závěrečné experimentální vyhodnocení, zda algoritmus, který automaticky nastavuje počáteční teplotu simulovaného ochlazování, pracuje uspokojivě pro praktické nasazení

`💛 hint`

Použijete vygenerované instance stejné velikosti.

Použijete praktické instance stejné velikosti.

Použijete reprezentativní mix praktických instancí.

Výpočet spustíte opakovaně pro každou instanci.

`answer`

`✅ correct`

Použijete reprezentativní mix praktických instancí. - Správně, Tímto přístupem získáte realistický obraz o funkčnosti algoritmu v různých praktických situacích.

Výpočet spustíte opakovaně pro každou instanci. - Správně, Opakované spuštění pomáhá získat stabilní a spolehlivé výsledky.

`❌ wrong`

Použijete vygenerované instance stejné velikosti. - Špatně, Pro komplexní hodnocení je lepší použít různé velikosti instancí.

Použijete praktické instance stejné velikosti. - Špatně, Stejný důvod jako výše.

---

# Randomizovaný/deterministický algoritmus

Potřebujete plánovací algoritmus, který chcete nasadit do aplikace řízení údržby. Omezení času výpočtu existuje, ale není podstatné (počítá se přes noc na příští den). Důležitá je kvalita (naježděné kilometry). Máte dva kandidáty, A a B, oba randomizované algoritmy. Potřebujete je experimentálně srovnat

`💛 hint`

Použijete přednostně instance „nachytané“ při předchozím manuálním řízení.

Pro každou instanci srovnáte dosažené optimalizační kritérium jedním během algoritmů A a B.

Pro každou instanci srovnáte průměrnou hodnotu opt. kritéria pro několik desítek až set spuštění.

Pokud zjistíte, že B je třikrát rychlejší než A, z každých třech hodnot opt. kritéria pro B vezmete tu nejlepší.

`answer`

`✅ correct`

Použijete přednostně instance „nachytané“ při předchozím manuálním řízení. - Správně, Toto poskytne realistický kontext pro testování.

Pro každou instanci srovnáte průměrnou hodnotu opt. kritéria pro několik desítek až set spuštění. - Správně, Tímto způsobem získáte spolehlivější výsledky.

Pokud zjistíte, že B je třikrát rychlejší než A, z každých třech hodnot opt. kritéria pro B vezmete tu nejlepší. - Správně, Tímto přístupem kompenzujete rychlostní rozdíl mezi algoritmy.

`❌ wrong`

Pro každou instanci srovnáte dosažené optimalizační kritérium jedním během algoritmů A a B. - Špatně, Jeden běh nemusí být dostatečně reprezentativní pro randomizované algoritmy.

---

Potřebujete plánovací algoritmus, který chcete nasadit do aplikace řízení údržby. Čas výpočtu je omezený – přes noc. Rozhodující je kvalita (naježděné kilometry). Máte dva kandidáty, A a B, oba randomizované algoritmy. Potřebujete je experimentálně srovnat

`💛 hint`

Pro každou instanci srovnáte průměrnou hodnotu opt. kritéria pro několik desítek až set spuštění.

Pokud zjistíte, že B je třikrát rychlejší než A (tedy dá se za noc spočítat třikrát), vezmete, pro každou instanci, z každých tří výsledků ten nejlepší.

Použijete náhodně generované instance

Použijete přednostně instance „nachytané“ při předchozím manuálním řízení.

`answer`

`✅ correct`

Pro každou instanci srovnáte průměrnou hodnotu opt. kritéria pro několik desítek až set spuštění. - Správně, Tím získáte spolehlivější statistické údaje.

Pokud zjistíte, že B je třikrát rychlejší než A (tedy dá se za noc spočítat třikrát), vezmete, pro každou instanci, z každých tří výsledků ten nejlepší. - Správně, Tímto způsobem můžete vyrovnat rozdíly v rychlosti algoritmů.

Použijete přednostně instance „nachytané“ při předchozím manuálním řízení. - Správně, Tento přístup poskytne realistický kontext pro srovnání.

`❌ wrong`

Použijete náhodně generované instance - Špatně, Lepší je použít praktické instance pro realističtější výsledky.

---

Potřebujete plánovací algoritmus, který chcete nasadit do aplikace řízení údržby. Čas je shora omezen, úspora pod tuto mez není zajímavá. Máte dva kandidáty, A a B, oba randomizované algoritmy. Potřebujete experimentálně srovnat jejich kvalitu

`💛 hint`

Použijete přednostně instance „nachytané“ při předchozím manuálním řízení.

Pro každou instanci srovnáte optimalizační kritérium, dosažené jedním během algoritmů A a B.

Pro každou instanci srovnáte průměrnou hodnotu opt. kritéria pro několik desítek až set spuštění.

Jako jedno spuštění algoritmu lze teoreticky uvažovat tolik běhů kabždého algoritmu, aby byl naplněn časový limit, a výběr nejlepšího řešení z nich.

`answer`

`✅ correct`

Použijete přednostně instance „nachytané“ při předchozím manuálním řízení. - Správně, Tento přístup poskytne realistické testovací prostředí.

Pro každou instanci srovnáte průměrnou hodnotu opt. kritéria pro několik desítek až set spuštění. - Správně, Tímto způsobem získáte spolehlivější a reprezentativnější data.

Jako jedno spuštění algoritmu lze teoreticky uvažovat tolik běhů kabždého algoritmu, aby byl naplněn časový limit, a výběr nejlepšího řešení z nich. - Správně, Tento přístup umožňuje maximálně využít dostupný čas a srovnat kvalitu řešení.

`❌ wrong`

Pro každou instanci srovnáte optimalizační kritérium, dosažené jedním během algoritmů A a B. - Špatně, Pro randomizované algoritmy je důležité srovnávat průměrné výsledky z více běhů.

---

Máte experimentálně vyhodnotit, zda doba běhu Las Vegas randomizovaného algoritmu roste nejvýše s kvadrátem velikosti instance. Chcete o tom napsat teoretický článek

`💛 hint`

Použijete instance „nachytané“ z praxe.

Použijete instance vygenerované tak, aby každá instance zadané velikosti byla stejně pravděpodobná.

Použijete instance jedné velikosti.

Výpočet spustíte opakovaně pro každou instanci.

`answer`

`✅ correct`

Použijete instance vygenerované tak, aby každá instance zadané velikosti byla stejně pravděpodobná. - Správně, Tento přístup zajišťuje objektivitu a reprezentativnost dat.

Výpočet spustíte opakovaně pro každou instanci. - Správně, Opakované spuštění zajišťuje, že výsledky budou statisticky významné.

`❌ wrong`

Použijete instance „nachytané“ z praxe. - Špatně, Pro teoretickou analýzu je lepší použít systematicky generované instance.

Použijete instance jedné velikosti. - Špatně, Pro analýzu závislosti doby běhu na velikosti instance je třeba použít instance různých velikostí.

---

Máte experimentálně vyhodnotit, zda relativní kvalita Monte Carlo randomizovaného algoritmu neklesá s rostoucí velikostí instance

`💛 hint`

Použijete instance „nachytané“ z praxe.

Budete potřebovat exaktní řešení (nebo to budete muset nějak obejít)

Použijete instance vygenerované tak, aby každá instance zadané velikosti byla stejně pravděpodobná.

Výpočet spustíte jednou pro každou instanci.

`answer`

`✅ correct`

Budete potřebovat exaktní řešení (nebo to budete muset nějak obejít) - Správně, Pro srovnání kvality výsledků je potřeba mít referenční řešení.

Použijete instance vygenerované tak, aby každá instance zadané velikosti byla stejně pravděpodobná. - Správně, Tímto způsobem zajišťujete objektivní a reprezentativní výběr instancí.

`❌ wrong`

Použijete instance „nachytané“ z praxe. - Špatně, Pro teoretickou analýzu a srovnání kvality je lepší použít systematicky generované instance.

Výpočet spustíte jednou pro každou instanci. - Špatně, U randomizovaných algoritmů je vhodnější spouštět výpočet opakovaně pro získání reprezentativních výsledků.

---

Máte experimentálně vyhodnotit, zda randomizovaný algoritmus, který vyvíjíte, je citlivý na určitou charakteristickou instanci

`💛 hint`

Použijete přednostně instance „nachytané“ při provozu podobného algoritmu v praxi, i když zkoumanou charakteristiku u nich nelze zjistit.

Použijete přednostně instance vygenerované se známými vlastnostmi.

Použijete instance různých vlastností tak, aby bylo možné srovnání podobných instancí, avšak s či bez zkoumané charakteristiky.

Výpočet spustíte opakovaně pro každou instanci.

`answer`

`✅ correct`

Použijete přednostně instance vygenerované se známými vlastnostmi. - Správně, To umožní přesně testovat citlivost na specifickou charakteristiku.

Použijete instance různých vlastností tak, aby bylo možné srovnání podobných instancí, avšak s či bez zkoumané charakteristiky. - Správně, Tento přístup umožní přesněji určit, zda a jak zkoumaná charakteristika ovlivňuje chování algoritmu.

Výpočet spustíte opakovaně pro každou instanci. - Správně, Opakované spuštění zajišťuje spolehlivost a reprezentativnost výsledků.

`❌ wrong`

Použijete přednostně instance „nachytané“ při provozu podobného algoritmu v praxi, i když zkoumanou charakteristiku u nich nelze zjistit. - Špatně, Pro tento účel je lepší použít instance s jasně definovanými charakteristikami.

---

Máte experimentálně vyhodnotit, zda randomizovaný plánovací algoritmus, který chcete nasadit do aplikace řízení údržby, pracuje pro toto nasazení uspokojivě. Obtížnost instancí řešených v ostrém nasazení je obtížné odhadnout na základě známých charakteristik

`💛 hint`

Použijete přednostně instance „nachytané“ při předchozím manuálním řízení.

Použijete přednostně instance vygenerované se známými vlastnostmi.

Použijete větší počet lehkých instancí k urychlení.

Výpočet spustíte opakovaně pro každou instanci.

`answer`

`✅ correct`

Použijete přednostně instance „nachytané“ při předchozím manuálním řízení. - Správně, Reálné instance poskytují nejlepší základ pro vyhodnocení praktické účinnosti algoritmu.

Výpočet spustíte opakovaně pro každou instanci. - Správně, Opakování experimentů pomáhá získat robustnější data a snížit náhodnou variabilitu.

`❌ wrong`

Použijete přednostně instance vygenerované se známými vlastnostmi. - Špatně, Uměle vygenerované instance nemusí adekvátně odrážet realitu.

Použijete větší počet lehkých instancí k urychlení. - Špatně, Lehké instance nemusí být reprezentativní pro skutečné podmínky nasazení.

---

Srovnáváte dva deterministické algoritmy A a B, za účelem teoretického poznání závislosti počtu kroků na velikosti instance. Pro algoritmus B, různé instance jedné velikosti vykazují velký rozptyl v počtu kroků

`💛 hint`

Počet kroků pro algoritmus B zprůměrujete, protože rozptyl není součástí hodnocení.

Zjistíte statistické rozložení počtu kroků a pokud je symetrické, použijete průměr.

Zjistíte statistické rozložení počtu kroků pro oba algoritmy a vyhodnotíte, zda se překrývají a jak mnoho.

Pokusíte se zjistit, jaká další charakteristika instancí má vliv na počet kroků.

`answer`

`✅ correct`

Zjistíte statistické rozložení počtu kroků a pokud je symetrické, použijete průměr. - Správně, Statistické rozložení poskytuje hlubší vhled do chování algoritmu.

Zjistíte statistické rozložení počtu kroků pro oba algoritmy a vyhodnotíte, zda se překrývají a jak mnoho. - Správně, Porovnání rozložení může odhalit zajímavé rozdíly mezi algoritmy.

Pokusíte se zjistit, jaká další charakteristika instancí má vliv na počet kroků. - Správně, Identifikace dalších faktorů může pomoci pochopit variabilitu v chování algoritmu.

`❌ wrong`

Počet kroků pro algoritmus B zprůměrujete, protože rozptyl není součástí hodnocení. - Špatně, Rozptyl může být důležitý pro porozumění chování algoritmu.

---

Zjišťujete vliv parametru randomizované lokální iterativní heuristiky na kvalitu výsledku. Chcete ukázat, že daný parametr na kvalitu výsledku vliv nemá

`💛 hint`

stačí jeden běh pro každou hodnotu parametru

program spustíte pro každou instanci mnohokrát, sledujete průměr.

pokud to není domácí úkol, použijete statistické metody, například korelaci, abyste dokázali nezávislost

pokud to není domácí úkol, naplánujete statistické metody tak, abyste prokázali nezávislost na parametru při všech charakteristikách instance

`answer`

`✅ correct`

program spustíte pro každou instanci mnohokrát, sledujete průměr. - Správně, Opakované běhy a průměrování výsledků poskytnou robustnější data.

pokud to není domácí úkol, použijete statistické metody, například korelaci, abyste dokázali nezávislost - Správně, Statistické metody jako korelace mohou pomoci prokázat nezávislost parametru na výsledku.

pokud to není domácí úkol, naplánujete statistické metody tak, abyste prokázali nezávislost na parametru při všech charakteristikách instance - Správně, Rozsáhlé statistické testování zajišťuje věrohodnost závěrů.

`❌ wrong`

stačí jeden běh pro každou hodnotu parametru - Špatně, Jeden běh není dostatečný pro spolehlivé statistické vyhodnocení.

---

Zjišťujete vliv parametru randomizované lokální iterativní heuristiky na kvalitu výsledku. Provedli jste jeden běh algoritmu na více instancích pro každou hodnotu parametru. Výsledná závislost je zcela chaotická, přestože by k tomu tak být nemělo

`💛 hint`

Je to důkaz, že kvalita na parametru nezávisí.

Použijete vizualizaci vývoje ceny, abyste zjistili, zda jiné parametry nejsou zcela nevhodně nastaveny.

Algoritmus spouštíte opakovaně na každé instanci.

Pokud to není domácí úkol, použijete statistické testy významnosti, abyste zjistili potřebný počet opakování.

`answer`

`✅ correct`

Použijete vizualizaci vývoje ceny, abyste zjistili, zda jiné parametry nejsou zcela nevhodně nastaveny. - Správně, Vizualizace může odhalit skryté vzorce nebo faktory ovlivňující výsledky.

Algoritmus spouštíte opakovaně na každé instanci. - Správně, Opakování experimentů zvyšuje spolehlivost výsledků.

Pokud to není domácí úkol, použijete statistické testy významnosti, abyste zjistili potřebný počet opakování. - Správně, Statistické testy pomáhají určit, jaký počet opakování je potřebný pro spolehlivé závěry.

`❌ wrong`

Je to důkaz, že kvalita na parametru nezávisí. - Špatně, Chaotické výsledky mohou naznačovat jiné faktory než nezávislost.

---

# Globální metoda

Globální metoda je aplikována na grafový problém. Instance je graf, velikost instance n se měří počtem uzlů grafu. Dekompozice produkuje v čase O(n) dvě podinstance, které obsahují vždy poloviční počet uzlů (nevíme které uzly) a hrany mezi nimi. Kompozice a řešení triviálních instancí je v konstantním čase. Algoritmus

`💛 hint`

dá nutně optimální řešení

O(n^2)

složitost je nejméně lineární

na náhodných instancích, použití paměti řešení podinstancí by se statisticky vyplatilo

je pseudopolynomiální

polynomiální na velikosti instance

při řešení dynamickým programováním, byl by polynomiální

`answer`

`✅ correct`

O(n^2) - Správně, Pokud dekompozice a zpracování každé podinstance trvá lineární čas a provádí se opakovaně, může celková složitost narůstat kvadraticky.

složitost je nejméně lineární - Správně, Dekompozice sama vyžaduje lineární čas, což znamená, že celková složitost nemůže být nižší.

polynomiální na velikosti instance - Správně, Kvadratická složitost je formou polynomiální složitosti.

při řešení dynamickým programováním, byl by polynomiální - Správně, Dynamické programování může algoritmus učinit polynomiálním tím, že efektivně využívá opakované podproblémy.

`❌ wrong`

dá nutně optimální řešení - Špatně, Bez dalších informací nelze určit, zda řešení bude vždy optimální.

na náhodných instancích, použití paměti řešení podinstancí by se statisticky vyplatilo - Špatně, Bez dalších informací o vlastnostech náhodných instancí nelze tvrdit, že by se paměťové řešení vyplatilo.

je pseudopolynomiální - Špatně, Informace poskytnuté nedovolují určit, zda je algoritmus pseudopolynomiální.

---

Globální optimalizační metoda dekomponuje každou instanci velikosti n na dvě instance velikosti n−1. Pokud existují optimální řešení dekomponovaných instancí, kompozicí dostaneme optimální řešení původní instance. Pokud některá z nich neexistuje, víme, že ani původní instance nemá řešení. Kompozice a dekompozice mají konstantní složitost

`💛 hint`

tento algoritmus je dynamickým programováním

z tohoto algoritmu se dá vytvořit dynamické programování

tento algoritmus má složitost Θ(2^n)

tento algoritmus má polynomiální složitost

`answer`

`✅ correct`

z tohoto algoritmu se dá vytvořit dynamické programování - Správně, Struktura problému umožňuje potenciální aplikaci dynamického programování pro efektivnější řešení.

tento algoritmus má složitost Θ(2^n) - Správně, Exponenciální složitost vzniká z nutnosti řešit obě podinstance pro každou dekompozici.

`❌ wrong`

tento algoritmus je dynamickým programováním - Špatně, Algoritmus popsaný nemusí být nutně dynamickým programováním.

tento algoritmus má polynomiální složitost - Špatně, Popisovaná metoda má exponenciální, nikoli polynomiální složitost.

---

Globální metoda je aplikována na grafový problém. Instance je tvořena grafem a jedním celým číslem M. velikost instance n se měří jemnou mírou (počet bitů popisu instance). Dekompozice produkuje v čase O(n log M) dvě podinstance, které obsahují vždy poloviční počet uzlů (nevíme které uzly) a hrany mezi nimi. Kompozice a řešení triviálních instancí je také v konstantním čase. Platí

`💛 hint`

čas jedné dekompozice je polynomiální ve velikosti instance měřené uvedeným způsobem

algoritmus řeší O(N) podinstancí, kde N je počet uzlů

algoritmus je pseudopolynomiální

při řešení dynamickým programováním je pseudopolynomiální

`answer`

`✅ correct`

čas jedné dekompozice je polynomiální ve velikosti instance měřené uvedeným způsobem - Správně, Čas O(n log M) je polynomiální ve velikosti instance.

`❌ wrong`

algoritmus řeší O(N) podinstancí, kde N je počet uzlů - Špatně, Pokud dekompozice produkuje podinstance s polovičním počtem uzlů, celkový počet řešených podinstancí není lineární vzhledem k počtu uzlů.

algoritmus je pseudopolynomiální - Špatně, Bez konkrétnějších informací nelze určit, zda je algoritmus pseudopolynomiální.

při řešení dynamickým programováním je pseudopolynomiální - Špatně, Dynamické programování by mohlo zefektivnit výpočet, ale informace poskytnuté nedovolují jednoznačně určit pseudopolynomiální charakter.

---

# Ostatní otázky (neoznačená změť, ovšem bez duplicit)

Jak se pozná, že heuristika neskončí v lokálním minimu?

`💛 hint`

po restartech skončí vždy ve stejném řešení

po více náhodných restartech skončí jinde

`answer`

`✅ correct`

po restartech skončí vždy ve stejném řešení - Správně, Pokud heuristika po restartech končí ve stejném řešení, může to znamenat, že našla globální minimum nebo je robustní vůči uvíznutí v lokálních minimech.

`❌ wrong`

po více náhodných restartech skončí jinde - Špatně, Pokud heuristika končí po restartech v různých řešeních, může to naznačovat, že existuje více lokálních minim a heuristika v nich může uvíznout.

---

Pokud je počáteční teplota u SA (simulované ochlazování) malá, algoritmus má tendenci padat do lokálního minima

`💛 hint`

ano

ne

`answer`

`✅ correct`

ano - Správně, Nízká počáteční teplota omezuje schopnost algoritmu přijímat horší řešení a tím zvyšuje riziko uvíznutí v lokálním minimu.

`❌ wrong`

ne - Špatně

---

Vede snížení velikosti turnaje ke zvýšení intenzifikace?

`💛 hint`

ano

ne

`answer`

`✅ correct`

ne - Správně, Menší turnaje znamenají slabší selekční tlak, což může pomoci udržet diverzitu populace.

`❌ wrong`

ano - Špatně, Snížení velikosti turnaje ve skutečnosti snižuje selekční tlak, což může vést k menší intenzifikaci.

---

S lineárně rostoucím k roste k-okolí:

`💛 hint`

lineárně

kvadraticky

exponenciálně

`answer`

`✅ correct`

exponenciálně - Správně, Velikost k-okolí může růst exponenciálně s rostoucím k, zvláště v prostorách s vysokou dimenzí.

`❌ wrong`

lineárně - Špatně, Rozsah k-okolí obvykle neroste lineárně s hodnotou k.

kvadraticky - Špatně, Růst k-okolí není obecně kvadratický.

---

Globální metody

`💛 hint`

vždy dávají exaktní výsledek

přibližná dekompozice dává exaktní výsledek

čistá dekompozice dává exaktní výsledek

přesná dekompozice dává exaktní výsledek

mají rekurzivní formulaci

`answer`

`✅ correct`

čistá dekompozice dává exaktní výsledek - Správně, Čistá dekompozice může vést k exaktním výsledkům v některých případech.

přesná dekompozice dává exaktní výsledek - Správně, Přesná dekompozice umožňuje získat exaktní výsledky.

mají rekurzivní formulaci - Správně, Mnoho globálních metod využívá rekurzivní přístup.

`❌ wrong`

vždy dávají exaktní výsledek - Špatně, Ne všechny globální metody poskytují exaktní výsledky.

přibližná dekompozice dává exaktní výsledek - Špatně, Přibližná dekompozice nemusí vždy poskytovat exaktní výsledky.

---

Zvýšení selekčního tlaku může způsobit

`💛 hint`

degeneraci

zrychlení konvergence

divergenci

ztrátu diverzity

`answer`

`✅ correct`

degeneraci - Správně, Příliš vysoký selekční tlak může vést k rychlé ztrátě genetické diverzity.

zrychlení konvergence - Správně, Vyšší selekční tlak může urychlit konvergenci k optimu.

ztrátu diverzity - Správně, Vyšší selekční tlak může snížit diverzitu populace.

`❌ wrong`

divergenci - Špatně, Zvýšení selekčního tlaku spíše snižuje diverzitu, než aby ji zvyšovalo.

---

Zvýšení mutace může způsobit

`💛 hint`

degeneraci

zrychlení konvergence

divergenci

ztrátu diverzity

`answer`

`✅ correct`

divergenci - Správně, Zvýšení mutace může zvýšit exploraci a předcházet předčasné konvergenci.

`❌ wrong`

degeneraci - Špatně, Zvýšená mutace typicky nevede k degeneraci, ale může zvýšit diverzitu.

zrychlení konvergence - Špatně, Příliš vysoká pravděpodobnost mutace může naopak zpomalit konvergenci.

ztrátu diverzity - Špatně, Mutace obvykle zvyšuje genetickou diverzitu v populaci.

---

Snížením selekčního tlaku u genetického algoritmu se zvyšuje diverzifikace

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Nižší selekční tlak umožňuje více jedincům přežít, což podporuje diverzitu.

`❌ wrong`

Ne - Špatně, Snížení selekčního tlaku skutečně podporuje diverzifikaci.

---

Mutace snižuje diverzifikaci

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně, Mutace je mechanismus, který zvyšuje genetickou diverzitu v populaci.

`❌ wrong`

Ano - Špatně, Mutace zvyšuje genetickou variabilitu a tedy diverzifikaci.

---

Globální metody

`💛 hint`

používají celý stavový prostor

nepoužívají stavový prostor vůbec

některé globální metody řeší některé NP-těžké problémy v polynomiálním čase

jsou založené na dekompozici

jsou založené na rekurzi

`answer`

`✅ correct`

jsou založené na dekompozici - Správně, Mnohé globální metody využívají dekompozici problému na menší části.

jsou založené na rekurzi - Správně, Rekurze je často využívána v globálních metodách pro rozklad problému.

`❌ wrong`

používají celý stavový prostor - Špatně, Některé globální metody mohou efektivně prozkoumávat stavový prostor bez jeho úplného prohledání.

nepoužívají stavový prostor vůbec - Špatně, I když některé globální metody mohou být prezentovány jako nevyužívající koncept stavového prostoru, ve skutečnosti se jedná o zjednodušení.

některé globální metody řeší některé NP-těžké problémy v polynomiálním čase - Špatně, Žádná globální metoda nemůže garantovat řešení NP-těžkých problémů v polynomiálním čase pro všechny instance.

---

Jak se pozná, že heuristika padá do lokálního extrému?

`💛 hint`

po každém restartu skončí stejně

po restartu to závisí na počátečním stavu

`answer`

`✅ correct`

po restartu to závisí na počátečním stavu - Správně, Pokud se výsledky mění v závislosti na počátečním stavu, naznačuje to, že heuristika může být citlivá na lokální extrémy.

`❌ wrong`

po každém restartu skončí stejně - Špatně, Toto nemusí nutně indikovat lokální extrém, může být důsledkem konzistence algoritmu.

---

Když zvýšíme selekční tlak, zvýší se intenzifikace?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Zvýšení selekčního tlaku obvykle vede ke koncentraci na prozkoumávání oblastí s vyšší zdatností, což je forma intenzifikace.

`❌ wrong`

Ne - Špatně

---

Když zvýšíme počáteční teplotu, skončí algoritmus rychle v lokálním extrému?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně

`❌ wrong`

Ano - Špatně, Vysoká počáteční teplota v simulovaném ochlazování umožňuje algoritmu lépe prozkoumat prostor řešení a je méně pravděpodobné, že rychle uvízne v lokálním extrému.

---

Pokud zvýšíme selekční tlak, zvýší se diverzifikace?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně

`❌ wrong`

Ano - Špatně, Zvýšení selekčního tlaku obvykle snižuje diverzifikaci, protože se zvýší intenzifikace na úkor prozkoumávání nových oblastí.

---

Zvyšuje se mutací intenzifikace?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně

`❌ wrong`

Ano - Špatně, Mutace obvykle zvyšuje diverzifikaci tím, že zavádí nové genetické variace, ne intenzifikaci.

---

Když je lokální heuristika silně závislá na počátečním řešení, pomůže zvětšit nebo zmenšit okolí?

`💛 hint`

Zvětšit

Zmenšit

`answer`

`✅ correct`

Zvětšit - Správně, Zvětšení okolí může pomoci heuristice uniknout z lokálních extrémů a lépe prozkoumat prostor řešení.

`❌ wrong`

Zmenšit - Špatně

---

Jaká strategie se používá pro výběr souseda u simulovaného ochlazování?

`💛 hint`

pouze nejlepší

prvé zlepšení

prvé zlepšení nebo přípustné zhoršení

nejlepší nejdříve

`answer`

`✅ correct`

prvé zlepšení nebo přípustné zhoršení - Správně, Simulované ochlazování akceptuje zlepšení nebo některé zhoršení na základě pravděpodobnostního kritéria.

`❌ wrong`

pouze nejlepší - Špatně, Simulované ochlazování nepoužívá pouze strategii nejlepšího souseda.

prvé zlepšení - Špatně, Tato strategie není typická pro simulované ochlazování.

nejlepší nejdříve - Špatně

---

Pokud je u SA nízká hodnota (délka) equilibria a neupdatuje se dynamicky, skončí heuristika rychle v lokálním minimu?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Nízká hodnota equilibria může způsobit, že simulované ochlazování rychle uvízne v lokálním minimu.

`❌ wrong`

Ne - Špatně

---

Kdy lokální heuristika NEMÁ tendenci padat do lokálního minima:

`💛 hint`

z náhodného řešení skončí vždy jinde

z náhodného řešení skončí vždy ve (zhruba) stejném místě

`answer`

`✅ correct`

z náhodného řešení skončí vždy ve (zhruba) stejném místě - Správně, Pokud heuristika konzistentně dosahuje podobných řešení bez ohledu na počáteční stav, naznačuje to, že není silně ovlivněna lokálními minimy.

`❌ wrong`

z náhodného řešení skončí vždy jinde - Špatně, Toto nenaznačuje, že heuristika neuvízne v lokálním minimu.

---

Pokud je počáteční teplota u SA malá, má algoritmus tendenci padat do lokálního minima?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Nízká počáteční teplota v simulovaném ochlazování může způsobit, že algoritmus rychle konverguje k lokálnímu minimu.

`❌ wrong`

Ne - Špatně

---

Lineární programování

`💛 hint`

je metoda

je problém

může mít omezení v podobě lineární nerovnice

má optimalizační kritéria v podobě lineární rovnice

`answer`

`✅ correct`

je problém - Správně, Lineární programování je typ optimalizačního problému, kde jsou cílová funkce a omezení lineární.

může mít omezení v podobě lineární nerovnice - Správně, Lineární programování typicky zahrnuje omezení ve formě lineárních nerovnic.

má optimalizační kritéria v podobě lineární rovnice - Správně, Cílová funkce v lineárním programování je formulována jako lineární rovnice.

`❌ wrong`

je metoda - Špatně, Lineární programování je matematická technika používaná k řešení optimalizačních problémů.

---

Zvětší se zvětšením populace diverzita?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Větší populace obvykle znamená vyšší genetickou diverzitu v genetických algoritmech.

`❌ wrong`

Ne - Špatně

---

Zvětší se zvětšením mutace diverzita?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Vyšší míra mutace zvyšuje genetickou variabilitu a diverzitu v populaci.

`❌ wrong`

Ne - Špatně

---

Zvýší snížení selekčního tlaku diverzitu?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Snížení selekčního tlaku zpomaluje výběr a může vést k větší diverzitě v populaci.

`❌ wrong`

Ne - Špatně

---

Dynamické programování

`💛 hint`

dává suboptimální výsledek

pro všechny problémy (NP nějaké) zaručuje řešení v polynomiálním čase

pro některé problémy (NP nějaké) zaručuje řešení v polynomiálním čase

je implementací přesné nebo čisté dekompozice

`answer`

`✅ correct`

pro některé problémy (NP nějaké) zaručuje řešení v polynomiálním čase - Správně, Pro některé typy problémů, zejména ty, které lze rozdělit na podproblémy, dynamické programování zajišťuje efektivní řešení.

je implementací přesné nebo čisté dekompozice - Správně, Dynamické programování rozděluje problém na menší části a řeší je postupně.

`❌ wrong`

dává suboptimální výsledek - Špatně, Dynamické programování je zaměřeno na nalezení optimálního řešení.

pro všechny problémy (NP nějaké) zaručuje řešení v polynomiálním čase - Špatně, Ne všechny problémy mohou být řešeny dynamickým programováním v polynomiálním čase.

---

Jak se pozná, že má lokální heuristika dostatečnou iterativní sílu?

`💛 hint`

po restartech skončí vždy ve stejném řešení

po více náhodných restartech skončí jinde

`answer`

`✅ correct`

po restartech skončí vždy ve stejném řešení - Správně, Pokud lokální heuristika konverguje ke stejnému řešení po restartech, může to naznačovat silnou iterativní sílu.

`❌ wrong`

po více náhodných restartech skončí jinde - Špatně

---

Pokud je vysoká teplota tuhnutí u SA, skončíme často v lokálním minimu?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně

`❌ wrong`

Ano - Špatně, Vysoká teplota tuhnutí u simulovaného žíhání (SA) umožňuje algoritmu lépe prozkoumávat prostor a potenciálně se vyhýbat uvíznutí v lokálním minimu.

---

GA, vybíráme turnajem. Když turnaj zmenšíme, zvýší se intenzifikace?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně

`❌ wrong`

Ano - Špatně, Zmenšením velikosti turnaje se obvykle snižuje intenzifikace výběru, protože je menší konkurence mezi jedinci.

---

Podporuje velký selekční tlak diverzifikaci?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně

`❌ wrong`

Ano - Špatně, Velký selekční tlak obvykle snižuje diverzitu, protože preferuje jedince s vyšší zdatností.

---

Metoda nejlepší nejdříve

`💛 hint`

poskytuje exaktní řešení

zaručuje polynomiální složitost

je úplná

je systematická

`answer`

`✅ correct`

poskytuje exaktní řešení - Správně, Metoda nejlepší nejdříve je exaktní metoda, která hledá optimální řešení.

je úplná - Správně, Jako exaktní metoda je metoda nejlepší nejdříve úplná, což znamená, že vždy najde řešení, pokud existuje.

je systematická - Správně, Metoda systematicky prohledává stavový prostor.

`❌ wrong`

zaručuje polynomiální složitost - Špatně, Tato metoda nemusí vždy zaručovat polynomiální složitost; záleží na konkrétním problému a implementaci.

---

Zvýšení počtu iterací při konstantní teplotě u SA (equilibrium), odpovídá

`💛 hint`

zvýšení koeficientu ochlazování

snížení koeficientu ochlazování

vztah nelze vyjádřit

`answer`

`✅ correct`

vztah nelze vyjádřit - Správně, Zvýšení počtu iterací při konstantní teplotě a koeficient ochlazování jsou dvě různé věci a jejich vztah není přímý.

`❌ wrong`

zvýšení koeficientu ochlazování - Špatně, Zvýšení počtu iterací při konstantní teplotě neodpovídá zvýšení koeficientu ochlazování. To by spíše zpomalilo proces ochlazování.

snížení koeficientu ochlazování - Špatně, Snížení koeficientu ochlazování by znamenalo pomalejší snižování teploty, což není přímo spojeno se zvýšením počtu iterací při konstantní teplotě.

---

Zvýší se snížením velikosti turnaje selekční tlak?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně, Snížením velikosti turnaje se selekční tlak snižuje.

`❌ wrong`

Ano - Špatně, Snížení velikosti turnaje naopak snižuje selekční tlak, protože zvyšuje šanci méně zdatných jedinců na výběr.

---

Pokud je koeficient ochlazování u SA velmi nízký, skončí heuristika rychle v lokálním minimu?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Velmi nízký koeficient ochlazování může vést k předčasnému uvíznutí v lokálním minimu.

`❌ wrong`

Ne - Špatně

---

Zvyšuje mutace diverzifikaci?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Mutace zvyšuje genetickou diverzitu v populaci.

`❌ wrong`

Ne - Špatně

---

Dynamické programování

`💛 hint`

je exaktní

zaručuje polynomiální složitost

je aproximativní

využívá dekompozice problémů

`answer`

`✅ correct`

je exaktní - Správně, Dynamické programování je exaktní metoda poskytující optimální řešení.

využívá dekompozice problémů - Správně, Dynamické programování rozkládá problém na menší podproblémy.

`❌ wrong`

zaručuje polynomiální složitost - Špatně, Dynamické programování nezaručuje vždy polynomiální složitost; záleží na konkrétním problému.

je aproximativní - Špatně, Jako exaktní metoda poskytuje přesná řešení.

---

Dynamické programování

`💛 hint`

je lokální metoda

představuje přibližnou dekompozici

dává suboptimální řešení

pro některé problémy je pseudopolynomiální

`answer`

`✅ correct`

pro některé problémy je pseudopolynomiální - Správně, Pro některé specifické problémy může být dynamické programování pseudopolynomiální.

`❌ wrong`

je lokální metoda - Špatně, Jako exaktní metoda není dynamické programování omezeno pouze na lokální řešení.

představuje přibližnou dekompozici - Špatně, Dekompozice v dynamickém programování je exaktní.

dává suboptimální řešení - Špatně, Dynamické programování poskytuje optimální řešení.

---

Je u SA při rychlejším ochlazování vyšší pravděpodobnost, že skončíme v lokálním minimu?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Rychlejší ochlazování může vést k uvíznutí v lokálním minimu.

`❌ wrong`

Ne - Špatně

---

Hladové algoritmy

`💛 hint`

dávají exaktní řešení

mají polynomiální složitost

systematicky prohledávají SP

úplně prohledávají SP

`answer`

`✅ correct`

mají polynomiální složitost - Správně, Hladové algoritmy obvykle mají polynomiální složitost.

`❌ wrong`

dávají exaktní řešení - Špatně, Hladové algoritmy často poskytují pouze heuristická nebo suboptimální řešení.

systematicky prohledávají SP - Špatně, Hladové algoritmy neprohledávají stavový prostor systematicky.

úplně prohledávají SP - Špatně, Hladové algoritmy neprohledávají celý stavový prostor, ale dělají lokální rozhodnutí.

---

Metoda pouze nejlepší (best only)

`💛 hint`

poskytuje exaktní řešení

zaručuje polynomiální složitost

je úplná SA

je systematická

`answer`

`❌ wrong`

poskytuje exaktní řešení - Špatně, Metoda "pouze nejlepší" nemusí vždy poskytnout exaktní řešení, zvláště v případě NP-těžkých problémů.

zaručuje polynomiální složitost - Špatně, Toto tvrzení nelze obecně považovat za pravdivé, jelikož efektivita metody závisí na specifikách problému.

je úplná SA - Špatně, "Pouze nejlepší" není úplná SA (simulované ochlazování) metoda.

je systematická - Špatně, Metoda "pouze nejlepší" nemusí být systematická ve smyslu prohledávání celého prostoru řešení.

---

Tabu prohledávání používá při transformaci metodu

`💛 hint`

pouze nejlepší

prvé zlepšení

prvé zlepšení   zhoršení

nejlepší nejdříve

`answer`

`✅ correct`

prvé zlepšení - Správně

`❌ wrong`

pouze nejlepší - Špatně, Tabu prohledávání obecně používá metodu "prvé zlepšení" s udržováním tabu listu k prevenci cyklení.

prvé zlepšení   zhoršení - Špatně

nejlepší nejdříve - Špatně

---

Metoda nejlepsi nejdříve (best first)

`💛 hint`

poskytuje exaktní řešení

NEzaručuje polynomiální složitost

je úplná

je systematická

`answer`

`✅ correct`

poskytuje exaktní řešení - Správně, Ve vhodných podmínkách a s dostatečnými zdroji může "nejlepší nejdříve" poskytnout exaktní řešení.

NEzaručuje polynomiální složitost - Správně, Složitost algoritmu "nejlepší nejdříve" může rychle růst v závislosti na problému.

je úplná - Správně, Za předpokladu dostatečných zdrojů je metoda schopna prozkoumat celý prostor řešení.

je systematická - Správně, Metoda "nejlepší nejdříve" systematicky prozkoumává prostor řešení podle určitého kritéria (např. heuristiky).

---

Zavedení lineárního škálování u GA

`💛 hint`

Zvýší selekční tlak

Sníží selekční tlak

Sníží nebo zvýší selekční tlak, podle aktuální hodnoty fitness v populaci

Nesouvisi se selekčním tlakem

`answer`

`✅ correct`

Sníží nebo zvýší selekční tlak, podle aktuální hodnoty fitness v populaci - Správně

`❌ wrong`

Zvýší selekční tlak - Špatně

Sníží selekční tlak - Špatně

Nesouvisi se selekčním tlakem - Špatně

---

Pro globální metody platí:

`💛 hint`

exaktní řešení najdou vždy

pokud používají čistou dekompozici, najdou exaktní řešení vždy

pokud používají přibližnou dekompozici, najdou exaktní řešení vždy

pokud používají čistou dekompozici a řešení nenaleznou, znamená to, že řešení neexistuje

mají rekurzivní formulaci

`answer`

`✅ correct`

mají rekurzivní formulaci - Správně

`❌ wrong`

exaktní řešení najdou vždy - Špatně

pokud používají čistou dekompozici, najdou exaktní řešení vždy - Špatně, Toto tvrzení je nesprávné; i s čistou dekompozicí nemusí globální metoda vždy najít exaktní řešení.

pokud používají přibližnou dekompozici, najdou exaktní řešení vždy - Špatně

pokud používají čistou dekompozici a řešení nenaleznou, znamená to, že řešení neexistuje - Špatně, Toto tvrzení je příliš zjednodušující a nemusí platit pro všechny situace.

---

Jak poznám, že moje jednoduchá lokální iterativní metoda funguje dobře:

`💛 hint`

po náhodných restartech vždy skončí ve stejném stavu

po náhodných restartech skončí vždy v počátku

`answer`

`❌ wrong`

po náhodných restartech vždy skončí ve stejném stavu - Špatně, Konzistence výsledků po náhodných restartech může naznačovat stabilitu, ale ne nutně, že metoda funguje "dobře" v kontextu nalezení optimálního řešení.

po náhodných restartech skončí vždy v počátku - Špatně

---

Velikost k-okolí při zvyšování k roste

`💛 hint`

nejvýše lineárně

nejvýše kvadraticky

až exponenciálně

`answer`

`✅ correct`

až exponenciálně - Správně

`❌ wrong`

nejvýše lineárně - Špatně

nejvýše kvadraticky - Špatně

---

Zvětšení turnaje zvyšuje intenzifikaci?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ano - Správně, Zvětšení turnaje zvyšuje selekční tlak, což může vést k intenzivnějšímu prozkoumávání prostoru nejlepších jedinců.

`❌ wrong`

Ne - Špatně

---

Velká koncová teplota způsobí uváznutí v lokálním minimu?

`💛 hint`

Ano

Ne

`answer`

`✅ correct`

Ne - Správně, Větší koncová teplota umožňuje algoritmu uniknout z lokálních minim díky vyšší pravděpodobnosti přijetí horších řešení.

`❌ wrong`

Ano - Špatně, Velká koncová teplota v simulovaném ochlazování by mohla vést k většímu průzkumu a potenciálně k překonání lokálních minim, nikoli k uváznutí v nich.

---

Metoda první zlepšení má tyto vlastnosti

`💛 hint`

poskytuje exaktní řešení

zaručuje polynomiální složitost

je úplná

je systematická

`answer`

`❌ wrong`

poskytuje exaktní řešení - Špatně, Metoda prvního zlepšení nemusí vždy poskytnout exaktní (optimální) řešení, protože může uváznout v lokálním optimu.

zaručuje polynomiální složitost - Špatně, Metoda prvního zlepšení nezaručuje polynomiální složitost; složitost závisí na problému a definici okolí.

je úplná - Špatně, Metoda není úplná, protože nemusí prozkoumat celý stavový prostor.

je systematická - Špatně, Metoda není systematická v tom smyslu, že systematicky prozkoumává celý prostor řešení; místo toho se zastaví u prvního nalezeného zlepšení.

---

Metoda Kernighan - Lin má následující vlastnosti

`💛 hint`

je založena na konstrukci proměnného okolí

toto okolí prohledává metodou pouze nejlepší

je založena na prořezávání

poskytuje kvalitnější výsledky než metoda nejlepší nejdříve

`answer`

`✅ correct`

je založena na konstrukci proměnného okolí - Správně, Metoda Kernighan-Lin dynamicky upravuje okolí během svého běhu.

`❌ wrong`

toto okolí prohledává metodou pouze nejlepší - Špatně, Kernighan-Lin může prohledávat okolí za účelem najít výměny, které vedou k celkovému zlepšení, ale ne nutně pouze nejlepší v každém kroku.

je založena na prořezávání - Špatně, Kernighan-Lin není založena na prořezávání v tradičním smyslu, jako je například v algoritmech rozhodovacího stromu.

poskytuje kvalitnější výsledky než metoda nejlepší nejdříve - Špatně, Kvalita výsledků závisí na specifickém problému a nemusí být vždy lepší než u jiných metod.

---

Metoda prohledávání okolí v tabu prohledávání je

`💛 hint`

prvé zlepšení nebo akceptovatelné zhoršení

pouze nejlepší

`answer`

`✅ correct`

pouze nejlepší - Správně, V některých variantách tabu prohledávání se skutečně hledá nejlepší dostupné řešení v okolí, i když to není univerzální pravidlo.

`❌ wrong`

prvé zlepšení nebo akceptovatelné zhoršení - Špatně, Tabu prohledávání může používat první zlepšení, ale také umožňuje akceptovat zhoršení za účelem překonání lokálních optim.

---

Změna parametrů lineárního škálování, která má za následek zvětšení poměru zdatnosti nejlepšího a nejhoršího jedince v genetických algoritmech způsobí diverzifikaci

`💛 hint`

ano

ne

`answer`

`✅ correct`

ne – Správně, způsobí intenzifikaci, protože slabší odpadnou - Správně, Intenzifikace je proces, kdy se algoritmus soustředí na prozkoumávání okolí aktuálně nejlepších řešení.

`❌ wrong`

ano - Špatně, Zvětšení tohoto poměru obvykle způsobí intenzifikaci tím, že se zvýší selekční tlak na lepší jedince, což může vést k rychlejší konvergenci.

---

Máte dynamické programování pro problém. Je závislé na podmnožině podproblémů (a nelze to udělat jinak). Jaký je to algoritmus?

`💛 hint`

Exponenciální

Pseudopolynomiální

Polynomiální

Globální optimalizace

`answer`

`✅ correct`

Globální optimalizace - Správně, Dynamické programování často poskytuje globální optimální řešení tím, že systematicky prozkoumává a řeší všechny relevantní podproblémy.

`❌ wrong`

Exponenciální - Špatně, Závislost na podmnožině podproblémů neimplikuje automaticky exponenciální složitost.

Pseudopolynomiální - Špatně, Pseudopolynomiálnost se vztahuje k algoritmům, jejichž složitost závisí na numerické hodnotě vstupu, ne na struktuře problému.

Polynomiální - Špatně, Dynamické programování může být polynomiální i při závislosti na podmnožině podproblémů, pokud jsou tyto podproblémy efektivně řešitelné.

---

Máme problém zakódovaný binárním vektorem. Definujeme určitou hranici na vzdálenost operace (Hammingova vzdálenost = počet bitů, které se oproti současnému stavu změní). Všechny stavy, které jsou pod hranicí, označíme jako tabu v tabu prohledávání. Toto je:

`💛 hint`

Diverzifikace

Intenzifikace

Omezení prostoru

`answer`

`✅ correct`

Diverzifikace - Správně, Omezení prostoru stavů, které jsou příliš blízko současnému řešení, může vést k diverzifikaci tím, že se algoritmus vyhýbá opakovanému prozkoumávání nedávno navštívených stavů.

Omezení prostoru - Správně, Definování hranice na Hammingovu vzdálenost a označení stavů jako tabu efektivně omezuje prozkoumávaný prostor stavů.

`❌ wrong`

Intenzifikace - Špatně, Toto nastavení spíše brání intenzifikaci tím, že zabraňuje opakovanému návratu k nedávno prozkoumaným řešením.

---

Máte genetický algoritmus a svou teorii ohledně vlastností instance, jak ji ověříte?

`💛 hint`

Vygeneruji instance s danou vlastností a nad nimi spustím genetický algoritmus

Algoritmus spustím opakovaně nad instancemi

Vygeneruji jak malé, tak velké instance a nad nimi spustím algoritmus

`answer`

`✅ correct`

Algoritmus spustím opakovaně nad instancemi - Správně, Opakovaný běh algoritmu na různých instancích může pomoci identifikovat, zda vlastnosti instance ovlivňují výkon algoritmu.

Vygeneruji jak malé, tak velké instance a nad nimi spustím algoritmus - Správně, Testování algoritmu na různých velikostech instancí pomůže zjistit, jak velikost instance ovlivňuje výkon algoritmu a může pomoci ověřit teorii v různých škálách problému.

`❌ wrong`

Vygeneruji instance s danou vlastností a nad nimi spustím genetický algoritmus - Špatně, Tento přístup může být relevantní, ale samotný není dostatečný pro ověření teorie.

---

Co má na vstupu evoluční programování?

`💛 hint`

Automat

Binární řetěz

Vektor čísel

Rozkladový strom výrazu

`answer`

`✅ correct`

Automat - Správně, Evoluční programování může pracovat s automaty jako jednou z možných reprezentací.

`❌ wrong`

Binární řetěz - Špatně, Binární řetězy jsou spíše typické pro genetické algoritmy než pro evoluční programování.

Vektor čísel - Špatně, I když vektory čísel mohou být použity, nejsou typickou reprezentací pro evoluční programování.

Rozkladový strom výrazu - Špatně, Rozkladové stromy výrazů jsou běžnější v genetickém programování.

---

Máte dynamické programování pro řešení grafového problému. Do předchozí instance se ptáte s klíčem (p, q) kde p je index uzlu a q je index hrany. Velikost instance se měří počtem uzlů.

`💛 hint`

Složitost roste třetí mocninou velikosti instance

Složitost roste druhou mocninou velikosti instance

Je to pseudopolynomiální

Je to globální metoda

`answer`

`✅ correct`

Složitost roste třetí mocninou velikosti instance - Správně, Závislost na počtu uzlů a hran může vést k třetí mocnině v některých grafových problémech.

Je to globální metoda - Správně, Dynamické programování je globální metoda, protože se snaží najít optimální řešení celého problému.

`❌ wrong`

Složitost roste druhou mocninou velikosti instance - Špatně, Zadání naznačuje složitější vztah než je kvadratický.

Je to pseudopolynomiální - Špatně, Pseudopolynomiální složitost se vztahuje k jinému typu problémů.

---

Selekční tlak v turnajovém výběru PŘÍMO nastavuje

`💛 hint`

velikost turnaje

pravděpodobnost výběru nejlepšího jedince

`answer`

`✅ correct`

velikost turnaje - Správně, Velikost turnaje přímo určuje, jaký selekční tlak je aplikován, protože větší turnaje obvykle zvyšují konkurenci mezi jedinci.

`❌ wrong`

pravděpodobnost výběru nejlepšího jedince - Špatně, Pravděpodobnost výběru nejlepšího jedince není přímo ovlivněna velikostí turnaje.

---

Máte simulované ochlazování s automatickým nastavováním počáteční teploty. Jak ověříte správnost nastavování počáteční teploty?

`💛 hint`

Pustím na instance různých velikostí

Pustím na instance různých hloubek

Pustim na mnoho malych instanci, abych to urychlil

Výpočet spustíte opakovaně pro každou instanci

`answer`

`✅ correct`

Pustím na instance různých velikostí - Správně, Testování na různých velikostech instancí pomůže zjistit, jak dobře se algoritmus přizpůsobuje různým problémovým prostředím.

Pustím na instance různých hloubek - Správně, Různé hloubky problémů poskytnou další dimenzi pro testování efektivity automatického nastavení teploty.

Výpočet spustíte opakovaně pro každou instanci - Správně, Opakované spuštění algoritmu na stejných instancích pomůže zjistit jeho konzistenci a robustnost.

`❌ wrong`

Pustim na mnoho malych instanci, abych to urychlil - Špatně, Testování pouze na malých instancích nemusí adekvátně odrážet chování algoritmu na větších a složitějších problémech.

---

GA lineárně škálovatelný s ruletovým výběrem může přímo ovlivňovat selekční tlak

`💛 hint`

pravděpodobnosti mutace

vyseče rulety

parametry lineárního škálování

`answer`

`✅ correct`

parametry lineárního škálování - Správně, Parametry lineárního škálování přímo ovlivňují rozdělení pravděpodobnosti výběru, což ovlivňuje selekční tlak.

`❌ wrong`

pravděpodobnosti mutace - Špatně, Pravděpodobnost mutace ovlivňuje variabilitu v genetické populaci, ale ne selekční tlak.

vyseče rulety - Špatně, Vyseče rulety jsou určeny zdatností, která je ovlivněna škálováním, ale nejsou přímo nastavovány.

---

Trvalá paměť se u Tabu algoritmu může použít k

`💛 hint`

diverzifikaci

intenzifikaci

omezení prohledávaného okolí tabu

`answer`

`✅ correct`

diverzifikaci - Správně, Pomáhá při hledání nových oblastí stavového prostoru.

intenzifikaci - Správně, Pomáhá zaměřit se na oblasti s dobrými řešeními.

omezení prohledávaného okolí tabu - Správně, Může být použita k omezení prohledávaného okolí.

---

Dynamický algoritmus, který jako klíče používá velikost instance a výpočet provádí na základě výsledku nižší instance a počítá od nejmenších instancí je

`💛 hint`

polynomiální

pseudopolynomiální

kvadratický

s lokální metodou

`answer`

`✅ correct`

polynomiální - Správně, Tento přístup ukazuje, že algoritmus je schopen řešit problémy v polynomiálním čase vzhledem k velikosti instance.

`❌ wrong`

pseudopolynomiální - Špatně, Neposkytujeme informace o závislosti složitosti na numerických hodnotách vstupu.

kvadratický - Špatně, Bez dalších informací nelze určit, že algoritmus má specificky kvadratickou složitost.

s lokální metodou - Špatně, Lokální metoda se v tomto kontextu nevztahuje k vlastnostem algoritmu.

---

Typická úloha toho, že tah je tabu v tabu prohledávání je

`💛 hint`

diverzifikace

intenzifikace

omezení okolí

`answer`

`✅ correct`

diverzifikace - Správně, Označení tahu jako tabu může pomoci algoritmu prozkoumávat nové oblasti.

omezení okolí - Správně, Tabu tahy pomáhají omezit prohledávané okolí a soustředit se na specifické oblasti.

`❌ wrong`

intenzifikace - Špatně, Intenzifikace se soustředí spíše na zkoumání oblastí s dobře známými dobrými řešeními.

---

Genetické programování pracuje nad reprezentací

`💛 hint`

vektoru reálných čísel

rozkladového stromu výrazu

binárního řetězu

automatu

`answer`

`✅ correct`

rozkladového stromu výrazu - Správně, Genetické programování často používá stromové struktury pro reprezentaci programů nebo rozhodovacích pravidel.

`❌ wrong`

vektoru reálných čísel - Špatně, Vektor reálných čísel není typickou reprezentací v genetickém programování.

binárního řetězu - Špatně, Binární řetězce jsou běžnější v genetických algoritmech.

automatu - Špatně, Automaty nejsou typickou reprezentací v genetickém programování.

---

Atributy z dlouhodobé paměti v TABU mohou být použité k

`💛 hint`

diverzifikaci

intenzifikaci

omezení okolí

`answer`

`✅ correct`

diverzifikaci - Správně, Dlouhodobá paměť může pomoci algoritmu prozkoumávat nové oblasti.

intenzifikaci - Správně, Může být využita k zaměření na oblasti, kde se dříve našla dobrá řešení.

omezení okolí - Správně, Pomáhá řídit prohledávání tím, že zahrnuje nebo vylučuje určité tahy.

---

Typická úloha aspiračních kritérií je

`💛 hint`

diverzifikace

intenzifikace

omezení okolí

`answer`

`✅ correct`

intenzifikace - Správně, Pomáhají soustředit se na oblasti s potenciálem pro zlepšení.

`❌ wrong`

diverzifikace - Špatně, Aspirační kritéria jsou využívána k překonání tabu stavu, pokud nové řešení přináší významné zlepšení.

omezení okolí - Špatně, Aspirační kritéria neomezuje okolí, ale umožňuje výjimky z tabu pravidel.

---

Algoritmus, který bude za běhu upravovat selekční tlak v GA, bude zjišťovat

`💛 hint`

diverzitu (rozdílnost) jedinců

změnu průměrné zdatnosti mezi generacemi

poměry zdatnosti

`answer`

`✅ correct`

diverzitu (rozdílnost) jedinců - Správně, Monitorování diverzity pomáhá zajistit, že selekční tlak nepovede k předčasné konvergenci.

změnu průměrné zdatnosti mezi generacemi - Správně, Sledování změny průměrné zdatnosti umožňuje adaptovat selekční tlak podle aktuálního stavu evoluce.

`❌ wrong`

poměry zdatnosti - Špatně, Konkrétní poměry zdatnosti nejsou přímo spojeny s upravováním selekčního tlaku.

---

# FIKI – zkouškové otázky 2013-2015

Základní jednotkou reprezentace, se kterou pracuje stochastická optimalizace, je

`💛 hint`

stochastický model závislosti mezi proměnnými

dvojice [identifikace proměnné, hodnota]

dvojice [střední hodnota, standardní odchylka]

binární řetěz

`answer`

`✅ correct`

stochastický model závislosti mezi proměnnými - Správně, Stochastická optimalizace často pracuje se stochastickými modely k modelování závislostí mezi proměnnými a nejistotami.

`❌ wrong`

dvojice [identifikace proměnné, hodnota] - Špatně, Tato reprezentace je typičtější pro deterministické optimalizační problémy.

dvojice [střední hodnota, standardní odchylka] - Špatně, I když tyto statistické údaje mohou být součástí stochastického modelu, nejsou samy o sobě základní jednotkou reprezentace.

binární řetěz - Špatně, Binární řetězy jsou spíše používány v genetických algoritmech a jiných formách evolučních výpočtů.

---

Dynamické programování je aplikováno na problém, kde konfigurační proměnné zobrazují graf s uzly očíslovanými 1…n, kde n je velikost instance. Podinstance je tvořena prvními m uzly. Kompozice a dekompozice mají složitost Omega(n). Algoritmus:

`💛 hint`

má složitost rostoucí s třetí mocninou velikosti instance

má složitost rostoucí s kvadrátem (druhou mocninou) velikosti instance

má složitost lineární ve velikosti instance

má složitost exponenciální ve velikosti instance

je pseudopolynomiální

`answer`

`✅ correct`

má složitost rostoucí s kvadrátem (druhou mocninou) velikosti instance - Správně, Omega(n) naznačuje, že minimální složitost je lineární, ale v kontextu grafu a podinstancí může skutečná složitost růst kvadraticky.

`❌ wrong`

má složitost rostoucí s třetí mocninou velikosti instance - Špatně, Uvedené informace neposkytují důvod pro tuto složitost.

má složitost lineární ve velikosti instance - Špatně, Uvedené informace naznačují vyšší než lineární složitost.

má složitost exponenciální ve velikosti instance - Špatně, Exponenciální složitost není indikována uvedenými podmínkami.

je pseudopolynomiální - Špatně, Není důvod klasifikovat algoritmus jako pseudopolynomiální na základě poskytnutých informací.

---

Dynamické programování řeší problém, kde každá instance i podinstance je charakterizována počtem prvků n a celočíselným parametrem P. Postup výpočtu je od triviálních podinstancí k finálnímu řešení. Dá se dokázat, že je třeba vyřešit podinstance pro všechna n, ale pro každé n pouze Θ(log(P)) instancí. Kompozice a dekompozice mají konstantní složitost. Algoritmus je:

`💛 hint`

nejméně exponenciální

pseudopolynomiální

kubický

polynomiální

`answer`

`✅ correct`

polynomiální - Správně, Polynomiální složitost je indikována potřebou vyřešit Θ(log(P)) instancí pro každé n a konstantní složitostí kompozice a dekompozice.

`❌ wrong`

nejméně exponenciální - Špatně, Exponenciální složitost není indikována, když je potřeba vyřešit pouze Θ(log(P)) instancí pro každé n.

pseudopolynomiální - Špatně, Pseudopolynomiální klasifikace by vyžadovala závislost na numerické hodnotě P, nikoli na logaritmu P.

kubický - Špatně, Kubická složitost není odůvodněna.

---

V genetickém algoritmu používáme operátor inverze, jestliže:

`💛 hint`

chceme potlačit statistickou nevyváženost uniformního křížení

chceme potlačit statistickou nevyváženost jednobodového křížení

současně používáme uniformní stochastický výběr

`answer`

`✅ correct`

chceme potlačit statistickou nevyváženost jednobodového křížení - Správně, Inverze může pomoci redukovat negativní dopady jednobodového křížení tím, že udržuje geny blízko sebe a potlačuje jejich rozdělení.

`❌ wrong`

chceme potlačit statistickou nevyváženost uniformního křížení - Špatně, Operátor inverze nemá přímý vztah k uniformnímu křížení.

současně používáme uniformní stochastický výběr - Špatně, Tato metoda selekce není přímo spojena s použitím operátoru inverze.

---

Pro praktickou aplikaci kombinatorického optimalizačního problému jste zvolili simulované ochlazování bez adaptačních mechanismů a s pevnou hodnotou koncové teploty. Na většině instancí se optimalizační kritérium nejdříve poněkud zhoršuje a přitom vykazuje náhodné změny, posléze se zlepšuje a náhodné změny se zmenšují. Na převážné části instancí konverguje ke stabilnímu a dobrému řešení. Na zbylých stále zlepšuje opt. kritérium a náhodné změny se zmenšují, ale optimalizační kritérium se nedostane ani ke startovací hodnotě. Na vině je:

`💛 hint`

příliš vysoká hodnota počáteční teploty

příliš nízká hodnota koncové teploty

podmínka ukončení, která nedetekuje konvergenci

příliš nízká hodnota koeficientu ochlazování

`answer`

`✅ correct`

podmínka ukončení, která nedetekuje konvergenci - Správně, Pokud algoritmus pokračuje v zlepšování bez dosažení konvergence, může to být způsobeno nedostatečnou podmínkou ukončení.

`❌ wrong`

příliš vysoká hodnota počáteční teploty - Špatně, Vysoká počáteční teplota by nezpůsobila popsaný problém.

příliš nízká hodnota koncové teploty - Špatně, Nízká koncová teplota by měla podporovat konvergenci.

příliš nízká hodnota koeficientu ochlazování - Špatně, Nízký koeficient ochlazování by způsobil pomalejší pokles teploty, což by mělo konvergenci spíše podporovat.

---

Instance problému splnění podmínek má n konfiguračních proměnných, doména každé proměnné má právě d hodnot. Algoritmus má stav odvozený pouze z konfiguračních proměnných.

`💛 hint`

Stavový prostor má n^d stavů

Stavový prostor má d^n stavů

Prostor prohledávání má (d+1)^n stavů

Prostor prohledávání má d^(2n) stavů

`answer`

`✅ correct`

Stavový prostor má d^n stavů - Správně, Prostor všech možných konfigurací má velikost d^n, kde d je počet hodnot pro každou proměnnou a n je počet proměnných.

Prostor prohledávání má (d+1)^n stavů - Správně, Pokud zahrneme možnost, že každá proměnná může být i neohodnocena, získáme tento rozšířený prostor prohledávání.

`❌ wrong`

Stavový prostor má n^d stavů - Špatně, Tato formulace není správná pro popis velikosti stavového prostoru.

Prostor prohledávání má d^(2n) stavů - Špatně, Tato formulace nepřesně reprezentuje velikost prostoru prohledávání.

---

Dynamické programování je aplikováno na problém, kde konfigurační proměnné zobrazují graf s hranami očíslovanými 1…m, kde m je počet hran instance. Každá hrana je ohodnocena celým číslem 1 … M. Podinstance je tvořena prvními m-1 hranami, každá je vypočítána. Kompozice a dekompozice mají složitost Theta(log(M)). Algoritmus

`💛 hint`

je lineární

je exponenciální

je polynomiální

je pseudopolynomiální

`answer`

`✅ correct`

je polynomiální - Správně, Složitost zpracování každé hrany a logaritmická složitost kompozice/dekompozice naznačuje, že celková složitost může být polynomiální.

`❌ wrong`

je lineární - Špatně, Složitost závisí na počtu hran a způsobu zpracování, ale ne nutně lineárně.

je exponenciální - Špatně, Neexistují důkazy, že by složitost byla exponenciální na základě poskytnutých informací.

je pseudopolynomiální - Špatně, Neexistují důkazy, že by algoritmus byl pseudopolynomiální.
