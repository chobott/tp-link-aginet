# TP-Link Aginet

Kompletní přehled platformy TP-Link Aginet pro poskytovatele internetových služeb (ISP/WISP).

> **Stav dokumentu:** informační přehled podle veřejné dokumentace TP-Linku, ověřený 13. srpna 2026. Konkrétní funkce, kompatibilita, dostupnost licencí a názvy modulů se mohou lišit podle regionu, modelu zařízení, firmwaru a smlouvy s TP-Linkem.

## Obsah

- [Co je Aginet](#co-je-aginet)
- [Přehled řešení](#přehled-řešení)
- [TAUC](#tauc)
- [Aginet ACS](#aginet-acs)
- [Aginet Config](#aginet-config)
- [Aginet App](#aginet-app)
- [Architektura a protokoly](#architektura-a-protokoly)
- [Typický životní cyklus zařízení](#typický-životní-cyklus-zařízení)
- [Přínosy pro ISP](#přínosy-pro-isp)
- [Bezpečnost a provoz](#bezpečnost-a-provoz)
- [Omezení a kompatibilita](#omezení-a-kompatibilita)
- [Terminologie](#terminologie)
- [Oficiální zdroje](#oficiální-zdroje)

## Co je Aginet

TP-Link Aginet je produktová značka a ekosystém určený pro internetové poskytovatele. Neskládá se pouze z jednoho routeru nebo jedné mobilní aplikace: kombinuje síťová zařízení pro přístupovou infrastrukturu a domácí Wi-Fi s nástroji pro provisioning, vzdálenou správu, diagnostiku, aktualizace firmwaru a podporu koncových zákazníků.

Cílem je převést část práce z výjezdů technika a ruční konfigurace na centralizované, automatizované procesy. ISP tak může zařízení hromadně nasadit, měnit konfiguraci na dálku, sledovat stav domácí sítě a řešit vybrané incidenty bez fyzické návštěvy.

Aginet se typicky uplatní u:

- klasických ISP a telekomunikačních operátorů;
- WISP, lokálních bezdrátových poskytovatelů a komunitních sítí;
- poskytovatelů optického připojení a PON infrastruktury;
- služeb managed Wi-Fi a white-label domácí konektivity.

## Přehled řešení

Oficiální Aginet Solution tvoří čtyři hlavní části:

| Část | Účel | Hlavní uživatel |
|---|---|---|
| **TAUC** (TP-Link Aginet Unified Cloud) | Cloudová platforma pro jednotnou správu, provisioning, monitoring, diagnostiku a API integraci | ISP, NOC, podpora |
| **Aginet ACS** | Autokonfigurační server pro vzdálenou správu kompatibilních Service Provider zařízení | ISP, WISP, technická podpora |
| **Aginet Config** | Příprava a hromadné nahrání ISP konfigurace do zařízení, včetně výchozí konfigurace přetrvávající po resetu | Sklad, instalace, provisioning |
| **Aginet App** | Mobilní správa domácí sítě, vizualizace a síťová diagnostika pro koncového uživatele | Zákazník ISP |

Jednotlivé komponenty se mohou nasazovat samostatně nebo jako součást širšího řešení. TAUC a ACS jsou zaměřeny primárně na zařízení pro poskytovatele; Aginet Config může podle seznamu kompatibility pracovat také s vybranými retailovými modely.

## TAUC

TAUC je cloudové řešení pro managed Wi-Fi a vzdálenou správu zařízení zákazníků. TP-Link jej popisuje jako jednotnou platformu využívající cloudový server, průmyslové standardy, bezdotykové nasazení, téměř okamžitou diagnostiku, úlohy a otevřenou integraci API.

### Hlavní schopnosti

- **Zero-touch deployment:** zařízení lze připravit k automatickému přijetí služby a konfigurace bez ručního nastavování u zákazníka.
- **Centrální správa:** operátor spravuje CPE a domácí sítě z jednoho rozhraní.
- **Monitoring:** přehled dostupnosti, topologie sítě, síly signálu, rychlostí a historie událostí.
- **Diagnostika:** vzdálené hledání problémů, například slabého signálu, rušení, překážek nebo problémů s kvalitou připojení.
- **Upozornění:** události a varování mohou upozornit podporu na vznikající problém dříve, než zákazník zavolá.
- **Vzdálené akce:** změna parametrů, restart, diagnostické testy a aktualizace podle oprávnění a kompatibility zařízení.
- **API Gateway:** napojení na OSS/BSS, aktivaci služby, autentizaci, autorizaci a automatizaci provozních procesů.
- **Rozšiřitelnost:** TP-Link uvádí podporu Linux Containers (LXC), AI‑podporované správy a kompatibility s vybranými zařízeními třetích stran; skutečný rozsah je nutné ověřit pro konkrétní deployment.

### Co může sledovat NOC

Praktický monitoring může zahrnovat online stav CPE, síťovou topologii, sílu bezdrátového signálu, historii změn, dostupnost zařízení, výsledky testů a události na domácí síti. Smyslem není pouze zobrazit stav, ale umožnit podpůrnému týmu provést diagnostiku a nápravu na dálku.

## Aginet ACS

Aginet ACS je autokonfigurační server pro vzdálený provoz zařízení TP-Link Service Provider. ACS (Auto Configuration Server) komunikuje s CPE, aplikuje parametry, získává diagnostická data a automatizuje opakované provozní úkony.

### Uváděné funkce

- vzdálená konfigurace a změna parametrů;
- diagnostické informace a proaktivní řešení problémů;
- upozornění a notifikace;
- správa zařízení za NATem;
- podpora datového modelu TR-181;
- konfigurace vybraných Wi-Fi 6 funkcí;
- vizualizace průzkumu okolních přístupových bodů;
- hromadná aktualizace firmwaru;
- účty s více rolemi a řízením oprávnění;
- testy výkonu.

TP-Link na stránce řešení uvádí škálování až na 100 000 CPE. Jde o deklarovanou kapacitu řešení, nikoli automatickou garanci pro každé prostředí; při návrhu je třeba ověřit sizing, licencování, regionální dostupnost, modely zařízení a požadavky na SLA.

ACS je vhodné zejména tam, kde ISP potřebuje řídit rozsáhlou flotilu kompatibilních CPE a nechce řešit konfiguraci jednotlivých routerů ručně.

## Aginet Config

Aginet Config je nástroj pro přípravu vlastního výchozího nastavení a jeho hromadné nasazení. ISP může vytvořit deployment model, změnit vybrané parametry, nastavit SSID a hesla a podle podpory modelu upravit také logo nebo favicon.

### Důležitá vlastnost resetu

Konfigurace zapsaná jako přizpůsobená výchozí konfigurace může zůstat zachována i po stisknutí resetovacího tlačítka. Tím se zařízení po obnovení nemusí vrátit k anonymnímu továrnímu profilu, což omezuje počet servisních zásahů. Tuto vlastnost je nutné testovat na konkrétním modelu a firmwaru, protože se nejedná o univerzální vlastnost všech TP-Link zařízení.

### Typický postup

1. Připravit počítač a síťový switch.
2. Zaregistrovat se a stáhnout Aginet Config Suite z portálu TP-Link.
3. Nainstalovat nástroj a vytvořit konfigurační soubory s nastavením ISP.
4. Připojit zařízení a importovat konfiguraci.
5. Nechat nástroj provést automatické hromadné nahrání nebo upgrade.
6. Ověřit výsledek, přístup k managementu, konektivitu, Wi-Fi a chování po resetu.

### Konfigurace, kterou lze řešit

- obecné výchozí parametry;
- SSID, hesla a další bezdrátová nastavení podle možností modelu;
- branding, logo a favicon;
- specifické nastavení jednotlivých modelů;
- hromadné použití stejného nebo připraveného profilu na více zařízení;
- hromadné aktualizace firmwaru, pokud je podporuje konkrétní workflow.

Konfigurace zařízení připojených k internetu by měla následně pokračovat přes vzdálenou platformu, například ACS nebo TAUC. Aginet Config je především onboarding/provisioning nástroj, nikoli plná náhrada dlouhodobého monitoringu.

## Aginet App

Aginet App je mobilní aplikace pro koncového zákazníka. Umožňuje spravovat kompatibilní router nebo mesh síť, zobrazit připojená zařízení a provádět základní síťovou diagnostiku.

### Uživatelské funkce

- průvodce prvotním nastavením;
- správa domácí Wi-Fi a vybraných síťových parametrů;
- přehled zařízení a vizualizace topologie;
- rodinné a domácí funkce podle modelu a profilu ISP;
- základní diagnostika konektivity a Wi-Fi;
- uživatelsky přívětivé zobrazení stavu sítě;
- možnost co-brandingu pro ISP, pokud je podporována konkrétní službou.

Přesný rozsah aplikace závisí na modelu, firmwaru, regionu a konfiguraci poskytovatele. Instalaci je vhodné provádět pouze z oficiálního Google Play nebo App Store a používat účet a přihlašovací údaje určené pro danou službu.

## Architektura a protokoly

Aginet staví na oddělení rolí mezi koncovým zařízením, cloudovou nebo ACS platformou, mobilní aplikací a systémy ISP.

```text
OSS/BSS, aktivace služby, CRM
              │ API / integrace
              ▼
        TAUC nebo Aginet ACS
              │ vzdálená správa
              ▼
 CPE / router / mesh / ONT / gateway zákazníka
              ▲
              │ lokální správa a diagnostika
              │
          Aginet App
```

### Relevantní standardy a technologie

TP-Link u TAUC uvádí podporu nebo návaznost na tyto standardy a technologie:

- **TR-369 / USP:** moderní protokol pro správu uživatelských zařízení;
- **TR-069 / CWMP:** rozšířený standard vzdálené autokonfigurace CPE;
- **TR-157 Bulk Data:** hromadný sběr telemetrie;
- **TR-143:** testování výkonu a propustnosti;
- **TR-181:** standardizovaný informační model zařízení a Multi-AP prvků;
- **EasyMesh:** interoperabilita a správa mesh Wi-Fi topologie;
- **LXC:** kontejnery uváděné jako součást rozšiřitelnosti TAUC;
- **REST/API integrace:** propojení s vlastními systémy ISP podle konkrétního API kontraktu.

Podpora protokolu na platformě sama o sobě neznamená, že všechny parametry nebo akce podporuje každý model. Rozhodující je kombinace modelu, hardwarové revize, firmwaru a oprávnění.

## Typický životní cyklus zařízení

1. **Výběr:** ověřit cílový model, regionální SKU, firmware, podporu protokolů a licenční podmínky.
2. **Příprava:** vytvořit v Aginet Config základní profil, případně branding a instalační parametry.
3. **Sklad:** otestovat sérii zařízení, firmware, MAC/serial evidenci a obnovu po resetu.
4. **Instalace:** připojit CPE k přístupové síti; podle architektury se zařízení zaregistruje v TAUC/ACS.
5. **Aktivace:** aplikovat službu, WAN parametry, Wi-Fi profil, mesh nastavení a bezpečnostní zásady.
6. **Provoz:** sledovat stav, topologii, události a výkonnostní metriky.
7. **Podpora:** provést vzdálenou diagnostiku a nápravnou akci, případně naplánovat servisní výjezd.
8. **Upgrade:** testovat firmware v pilotu a následně provést řízenou hromadnou aktualizaci.
9. **Vyřazení:** zrušit vazbu na zákazníka, odebrat přístupová oprávnění a bezpečně zpracovat zařízení.

## Přínosy pro ISP

- menší počet výjezdů a nižší náklady podpory;
- rychlejší aktivace služby a méně ruční konfigurace;
- konzistentní výchozí nastavení napříč flotilou;
- centralizovaný přehled o domácích sítích;
- proaktivní odhalování problémů;
- řízené aktualizace firmwaru;
- možnost nabídnout managed Wi-Fi jako součást nebo nadstavbu služby;
- branding aplikace a uživatelské zkušenosti podle možností konkrétního řešení;
- API integrace do interních provozních systémů.

## Bezpečnost a provoz

Aginet poskytuje nástroje pro vzdálenou správu, ale bezpečnost závisí na správném návrhu a provozu ISP. Doporučené minimum:

- oddělit role NOC, podpory, instalace a administrátorů;
- používat nejsilnější dostupné přihlašování a pravidelně revidovat účty;
- omezit oprávnění podle principu nejmenších privilegií;
- evidovat změny konfigurace a administrátorské akce;
- oddělit provisioning od běžného uživatelského přístupu;
- testovat firmware a konfigurace v pilotní skupině;
- plánovat rollback nebo servisní postup pro neúspěšný upgrade;
- chránit exporty konfigurace, sériová čísla, MAC adresy a zákaznická data;
- nepoužívat stejné administrátorské heslo napříč zařízeními;
- ověřit retenční dobu telemetrie a požadavky GDPR ve vlastní jurisdikci;
- pravidelně kontrolovat, zda jsou zařízení i cloudové účty aktivní pouze po dobu oprávněného poskytování služby.

Toto README není bezpečnostní certifikace ani náhrada za oficiální bezpečnostní dokumentaci, smluvní podmínky a interní provozní standardy.

## Omezení a kompatibilita

Před nasazením je třeba ověřit:

- přesný model a hardwarovou revizi;
- region a lokalizaci produktu;
- minimální a doporučenou verzi firmwaru;
- zda jde o retailový nebo Service Provider model;
- které parametry podporuje TR-181/TR-069/TR-369 implementace zařízení;
- dostupnost TAUC, Aginet ACS, Aginet Config Suite a Aginet App v daném regionu;
- licencování, kapacitní limity, API a SLA;
- chování zařízení po factory resetu;
- kompatibilitu EasyMesh a mesh diagnostiky;
- síťové požadavky, firewall, DNS, NAT a časovou synchronizaci;
- pravidla ochrany osobních údajů a ukládání telemetrie.

Veřejné stránky TP-Linku uvádějí seznamy kompatibilních produktů, které se mohou měnit. Tento dokument proto záměrně neuvádí úplný statický seznam modelů. Pro konkrétní rollout je rozhodující aktuální seznam podporovaných modelů a firmware od TP-Linku nebo vašeho account týmu.

## Terminologie

| Zkratka | Význam |
|---|---|
| **ACS** | Auto Configuration Server, server automatické konfigurace |
| **CPE** | Customer Premises Equipment, zařízení u zákazníka |
| **CWMP** | CPE WAN Management Protocol, protokol TR-069 |
| **ISP** | Internet Service Provider, poskytovatel internetových služeb |
| **NOC** | Network Operations Center, dohledové/průchozí centrum sítě |
| **OSS/BSS** | Provozní a obchodní podpůrné systémy ISP |
| **TAUC** | TP-Link Aginet Unified Cloud |
| **TR-181** | Datový/informační model zařízení a síťových prvků |
| **USP** | User Services Platform, protokol TR-369 |
| **WISP** | Wireless Internet Service Provider |

## Oficiální zdroje

- [Aginet Solution – TP-Link Service Provider](https://service-provider.tp-link.com/aginet-solution/)
- [Řešení Aginet – TP-Link Česká republika](https://www.tp-link.com/cz/landing/aginet-solution/)
- [Aginet Config – TP-Link](https://www.tp-link.com/us/solution/agile-config/)
- [TAUC – oficiální oznámení TP-Linku](https://www.tp-link.com/us/press/news/20443/)
- [ISP Tools – Aginet Config, Cloud Management and More](https://www.tp-link.com/nordic/solution/isp-tools/)
- [Portál TP-Link Service Provider](https://service-provider.tp-link.com/)

## Licence a odpovědnost

Tento dokument je komunitní/informační přehled a není oficiální dokumentací TP-Linku. Názvy produktů a ochranné známky patří příslušným vlastníkům. Před produkčním nasazením ověřte všechny údaje u TP-Linku, v aktuálních manuálech, release notes a smluvních podmínkách pro váš region.