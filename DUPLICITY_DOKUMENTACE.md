# Dokumentace duplicitních tříd a sekcí v style.css

**Celkový počet řádků:** 20,776  
**Datum analýzy:** 14. listopadu 2025

---

## 📋 Obsah
1. [Hlavní duplicitní sekce](#hlavní-duplicitní-sekce)
2. [Duplicitní třídy komponenty](#duplicitní-třídy-komponenty)
3. [Překrývající se stylizace](#překrývající-se-stylizace)
4. [CSS proměnné](#css-proměnné)
5. [Doporučení pro refaktoring](#doporučení-pro-refaktoring)

---

## 1. Hlavní duplicitní sekce

### 🔄 HEADER (5× duplicitní)
**První výskyt:**
- **Řádky:** 3-14
- **Sekce:** INDEX (hlavní homepage)
- **Třídy:** `.header`, `.navbar`, `.logo`

**Další výskyty:**
1. **Řádky:** 5624-5636 (COURSE DETAIL PAGE - KURZ DETAIL)
2. **Řádky:** 8504-8516 (DETAIL STYLE)
3. **Řádky:** 11203-11215 (PROFILE PAGE - MŮJ PROFIL)
4. **Řádky:** 14319-14331 (SHOPPING CART PAGE - NÁKUPNÍ KOŠÍK)
5. **Řádky:** 15715-15727 (CHECKOUT PAGE - POKLADNA)
6. **Řádky:** 16825-16837 (PROFIL LEKTORA)
7. **Řádky:** 18461-18473 (TEST PAGE STYLES)

**Duplicita:** 100% identické stylování v 7 různých sekcích

---

### 🔄 SEARCHBAR (5× duplicitní)
**První výskyt:**
- **Řádky:** 16-35
- **Sekce:** INDEX
- **Třídy:** `.searchbar-container`, `.search-form`, `.search-wrapper`, `.search-icon`, `.search-input`

**Další výskyty:**
1. **Řádky:** 5637-5657 (COURSE DETAIL)
2. **Řádky:** 8517-8541 (DETAIL STYLE)
3. **Řádky:** 11216-11240 (PROFILE PAGE)
4. **Řádky:** 14332-14352 (SHOPPING CART)
5. **Řádky:** 15728-15748 (CHECKOUT)
6. **Řádky:** 16838-16858 (PROFIL LEKTORA)
7. **Řádky:** 18474-18498 (TEST PAGE)

**Duplicita:** 100% identické

---

### 🔄 MOBILE MENU (5× duplicitní)
**První výskyt:**
- **Řádky:** 37-64
- **Sekce:** INDEX
- **Třídy:** `.hamburger`, `.hamburger-btn`, `.mobile-menu`, `.mobile-link`, `.mobile-btn`

**Další výskyty:**
1. **Řádky:** 5658-5686 (COURSE DETAIL)
2. **Řádky:** 8542-8574 (DETAIL STYLE)
3. **Řádky:** 11241-11273 (PROFILE PAGE)
4. **Řádky:** 14353-14381 (SHOPPING CART)
5. **Řádky:** 15749-15777 (CHECKOUT)
6. **Řádky:** 16859-16889 (PROFIL LEKTORA)
7. **Řádky:** 18499-18531 (TEST PAGE)

**Duplicita:** 100% identické

---

### 🔄 DESKTOP MENU (5× duplicitní)
**První výskyt:**
- **Řádky:** 66-90
- **Sekce:** INDEX
- **Třídy:** `.navbar-menu`, `.nav-links`, `.nav-item`, `.nav-link`, `.dropdown`, `.dropdown-link`

**Další výskyty:**
1. **Řádky:** 5687-5712 (COURSE DETAIL)
2. **Řádky:** 8575-8602 (DETAIL STYLE)
3. **Řádky:** 11274-11301 (PROFILE PAGE)
4. **Řádky:** 14382-14407 (SHOPPING CART)
5. **Řádky:** 15778-15803 (CHECKOUT)
6. **Řádky:** 16890-16915 (PROFIL LEKTORA)
7. **Řádky:** 18532-18559 (TEST PAGE)

**Duplicita:** 100% identické

---

### 🔄 BUTTONS (5× duplicitní)
**První výskyt:**
- **Řádky:** 92-107
- **Sekce:** INDEX
- **Třídy:** `.btn-outline`, `.btn-primary`, `.icon-btn`, `.icon-btn-alt`

**Další výskyty:**
1. **Řádky:** 5713-5766 (COURSE DETAIL) - rozšířená verze
2. **Řádky:** 8603-8627 (DETAIL STYLE)
3. **Řádky:** 11311-11319 (PROFILE PAGE) - zkrácená verze
4. **Řádky:** 14408-14424 (SHOPPING CART)
5. **Řádky:** 15804-15820 (CHECKOUT)
6. **Řádky:** 16916-16924 (PROFIL LEKTORA)
7. **Řádky:** 18569-18577 (TEST PAGE)

**Duplicita:** ~80-100% podle sekce

---

### 🔄 HERO SECTION (6× duplicitní)
**První výskyt:**
- **Řádky:** 109-269
- **Sekce:** INDEX
- **Třídy:** `.hero-section`, `.hero-wrapper`, `.hero-gradient`, `.bubble-field`, `.hero-content`, `.hero-texts`, `.hero-title`, `.hero-paragraph`, `.hero-buttons`, atd.

**Další výskyty:**
1. **Řádky:** 3394-3465 (DETAIL KURZU PŘIHLÁŠENÝ) - upravená verze
2. **Řádky:** 5809-5889 (COURSE DETAIL) - upravená verze
3. **Řádky:** 8655-8698 (DETAIL STYLE) - upravená verze
4. **Řádky:** 11320-11368 (PROFILE PAGE) - "from detail-kurzu"
5. **Řádky:** 14425-14470 (SHOPPING CART)
6. **Řádky:** 15821-15866 (CHECKOUT)
7. **Řádky:** 16945-17102 (PROFIL LEKTORA) - rozšířená verze
8. **Řádky:** 18578-18633 (TEST PAGE)

**Duplicita:** 60-90% podle sekce, některé upraveny pro specifický účel

---

### 🔄 BUBBLES (4× duplicitní)
**První výskyt:**
- **Řádky:** 125 (.bubble-field) a 129 (.bubble) v INDEX
- **Sekce:** INDEX (součást HERO SECTION)

**Další výskyty:**
1. **Řádky:** 5615-5623 (COURSE DETAIL PAGE - samostatná sekce)
2. **Řádky:** 11194-11202 (PROFILE PAGE)
3. **Řádky:** 14310-14318 (SHOPPING CART)
4. **Řádky:** 15706-15714 (CHECKOUT)
5. **Řádky:** 18452-18460 (TEST PAGE)

**Duplicita:** 100% identické

---

### 🔄 TABS (5× duplicitní)
**První výskyt:**
- **Řádky:** 3472-3507
- **Sekce:** DETAIL KURZU PŘIHLÁŠENÝ
- **Třídy:** `.tabs-wrapper`, `.tabs`, `.tab`, `.tab.active`, `.tab:hover`
- **Obsahuje:** CSS proměnné `--indicator-left` a `--indicator-width`

**Další výskyty:**
1. **Řádky:** 6014-6062 (COURSE DETAIL PAGE) - duplicitní proměnné odstraněny
2. **Řádky:** 8761-8814 (DETAIL STYLE) - struktura
3. **Řádky:** 12837-12862 (SETTINGS TAB v PROFILE) - duplicitní proměnné odstraněny
4. **Řádky:** 17166-17214 (PROFIL LEKTORA)

**Duplicita:** 85-95%, některé mají rozdílné specifické vlastnosti

---

### 🔄 TAB CONTENT (4× duplicitní)
**První výskyt:**
- **Řádky:** 3508-3514
- **Sekce:** DETAIL KURZU PŘIHLÁŠENÝ
- **Třídy:** `.tab-content`, `.tab-content.active`

**Další výskyty:**
1. **Řádky:** 6063-6088 (COURSE DETAIL)
2. **Řádky:** 8815-8907 (DETAIL STYLE)
3. **Řádky:** 17215-17225 (PROFIL LEKTORA)

**Duplicita:** 80-100%

---

### 🔄 FOOTER (6× duplicitní)
**První výskyt:**
- **Řádky:** 851-1070
- **Sekce:** INDEX (moved from profil-lektora.css)
- **Třídy:** `.footer`, `.footer-container`, `.footer-logo`, `.footer-grid`, `.footer-info`, `.footer-categories`, `.footer-heading`, `.footer-links`, atd.

**Další výskyty:**
1. **Řádky:** 4025-4097 (DETAIL KURZU PŘIHLÁŠENÝ)
2. **Řádky:** 6174-6394 (COURSE DETAIL)
3. **Řádky:** 9652-9728 (DETAIL STYLE)
4. **Řádky:** 12148-12230 (PROFILE PAGE - "from index.html")
5. **Řádky:** 14918-14993 (SHOPPING CART)
6. **Řádky:** 16378-16454 (CHECKOUT)
7. **Řádky:** 17606-17825 (PROFIL LEKTORA)

**Duplicita:** 90-100%, velmi rozsáhlá sekce

---

### 🔄 MAIN CONTENT (4× duplicitní)
**První výskyt:**
- **Řádky:** 1581-1585
- **Sekce:** HERO SECTION CATEGORY
- **Třídy:** `.main-content`

**Další výskyty:**
1. **Řádky:** 3375-3379 (DETAIL KURZU PŘIHLÁŠENÝ)
2. **Řádky:** 5767-5771 (COURSE DETAIL)
3. **Řádky:** 8628-8654 (DETAIL STYLE)
4. **Řádky:** 16925-16944 (PROFIL LEKTORA)

**Duplicita:** 100% pro základní třídu

---

### 🔄 CONTENT CARD (4× duplicitní)
**První výskyt:**
- **Řádky:** 3466-3471
- **Sekce:** DETAIL KURZU PŘIHLÁŠENÝ
- **Třídy:** `.content-card`

**Další výskyty:**
1. **Řádky:** 5954-6013 (COURSE DETAIL)
2. **Řádky:** 8699-8760 (DETAIL STYLE)
3. **Řádky:** 17103-17112 (PROFIL LEKTORA)

**Duplicita:** ~70%, každá má mírně odlišné vlastnosti

---

### 🔄 SIDEBAR (3× duplicitní)
**První výskyt:**
- **Řádky:** 3833-3847
- **Sekce:** DETAIL KURZU PŘIHLÁŠENÝ
- **Třídy:** `.sidebar`

**Další výskyty:**
1. **Řádky:** 6089-6173 (COURSE DETAIL - SIDEBAR & PROGRESS CARD)
2. **Řádky:** 7127-7154 (COURSE DETAIL - SIDEBAR - COURSE SPECIFIC STYLES)
3. **Řádky:** 8942-9150 (DETAIL STYLE - SIDEBAR LAYOUT)
4. **Řádky:** 11997-12147 (PROFILE PAGE)
5. **Řádky:** 14691-14774 (SHOPPING CART - CART SIDEBAR)
6. **Řádky:** 19460-19469 (TEST PAGE)

**Duplicita:** 50-80%, různé účely ale podobná struktura

---

### 🔄 REVIEWS SECTION (3× duplicitní)
**První výskyt:**
- **Řádky:** 692-850
- **Sekce:** INDEX
- **Třídy:** `.reviews-section`, `.reviews-header`, `.reviews-title`, `.reviews-subtitle`, `.myReviewsSwiper`, `.review-card`, atd.

**Další výskyty:**
1. **Řádky:** 6893-7126 (COURSE DETAIL)
2. **Řádky:** 18093-18431 (PROFIL LEKTORA)

**Duplicita:** 85-95%

---

### 🔄 RESPONSIVE STYLES (6× duplicitní)
**První výskyt:**
- **Řádky:** 1108-1291 (RESPONSIVE: MOBILE v INDEX)
- **Sekce:** INDEX

**Další výskyty:**
1. **Řádky:** 2407-3071 (kategorie kurzu)
2. **Řádky:** 4098-4967 (DETAIL KURZU PŘIHLÁŠENÝ)
3. **Řádky:** 7346-8295 (COURSE DETAIL)
4. **Řádky:** 9729-10596 (DETAIL STYLE)
5. **Řádky:** 12231-12740 (PROFILE PAGE)
6. **Řádky:** 14994-15684 (SHOPPING CART)
7. **Řádky:** 16455-16820 (CHECKOUT)
8. **Řádky:** 17226-17605 (PROFIL LEKTORA)

**Duplicita:** Velmi rozsáhlé, 60-90% překryv

---

## 2. Duplicitní třídy (komponenty)

### A) Instructor komponenty (3× duplicitní)

#### `.instructor-info`
- **První výskyt:** Řádek 2133 (INSTRUCTORS SECTION)
- **Druhý výskyt:** Řádek 3418 (DETAIL KURZU PŘIHLÁŠENÝ)
- **Duplicita:** Rozdílný obsah a účel

#### `.instructor-avatar`
- **První výskyt:** Řádek 2127 (INSTRUCTORS SECTION)
- **Druhý výskyt:** Řádek 3426 (DETAIL KURZU PŘIHLÁŠENÝ)
- **Duplicita:** Podobná struktura, rozdílná velikost

#### `.instructor-name`
- **První výskyt:** Řádek 2137 (INSTRUCTORS SECTION)
- **Druhý výskyt:** Řádek 3438 (DETAIL KURZU PŘIHLÁŠENÝ)
- **Duplicita:** 90%

---

### B) Tag komponenty (4× duplicitní)

#### `.tag`
- **První výskyt:** Řádek 360 (CARDS SHARED)
- **Další výskyty:**
  - Řádek 1982 (COURSE CARDS)
  - Řádek 3446 (DETAIL KURZU PŘIHLÁŠENÝ)
- **Duplicita:** Základní třída 100%, modifikátory různé

#### Tag modifikátory:
- `.tag-purple` - Řádky: 363, 1988
- `.tag-cyan` - Řádky: 1993
- `.tag-green` - Řádky: 357, 1998
- `.tag-blue` - Řádek 360
- `.tag-turquoise` - Řádky: 367, 2003
- `.tag-bestseller` - Řádek 3450
- `.tag-trial` - Řádek 3454

**Duplicita:** Barvy se opakují ale s různými kombinacemi

---

### C) Hero komponenty

#### `.hero-gradient`
- **První výskyt:** Řádek 117 (INDEX - HERO SECTION)
- **Další výskyty:**
  - Řádek 673 (CATEGORY GRADIENT)
  - Řádek 3395 (DETAIL KURZU PŘIHLÁŠENÝ)
- **Duplicita:** 60-80%, různé velikosti a vlastnosti

#### `.hero-title`
- **Výskyty:** Řádky 141, 1528 (category), 3409, 5816, 8662, 11324, atd.
- **Duplicita:** 70-90%, různé velikosti fontů

#### `.hero-paragraph`
- **Výskyty:** Řádky 149, 1534, 3413
- **Duplicita:** 85-95%

---

### D) Swiper komponenty

#### Navigační šipky (kompletní duplikace)
- `.swiper-button-prev`, `.swiper-button-next`
- `.news-prev`, `.news-next`
- `.category-prev`, `.category-next`
- `.review-prev`, `.review-next`

**Řádky:** 375-447 (SWIPER NAVIGATION)
**Duplicita:** Všechny používají téměř identický styl s různými pozicemi

---

### E) Progress bar komponenty (2× duplicitní)

#### Progress bars
- **První výskyt:** Řádek 1089 (COURSE DETAIL)
- **Druhý výskyt:** Řádek 11906 (PROFILE PAGE - "from detail-kurzu-prihlaseny.css")
- **Třídy:** `.progress-bar`, `.progress-bar-fill`
- **Duplicita:** 100%

---

### F) Modal komponenty (3× různé modály)

#### `.cart-modal`
- **Řádky:** 2226-2406 (kategorie kurzu)
- **Řádky:** 8296-8477 (DETAIL STYLE - CART MODAL)
- **Duplicita:** 95-100%

#### `.review-modal`
- **Řádky:** 4968-5073 (DETAIL KURZU PŘIHLÁŠENÝ)
- **Duplicita:** Unikátní

#### `.discussion-modal`
- **Řádky:** 9529-9651 (DETAIL STYLE)
- **Duplicita:** Unikátní

#### `.streak-modal`
- **Řádky:** 11777-11905 (PROFILE PAGE)
- **Duplicita:** Unikátní

#### `.upload-avatar-modal`
- **Řádky:** 13034-14289 (PROFILE PAGE)
- **Duplicita:** Unikátní

---

## 3. Překrývající se stylizace

### A) Duplicitní `instructors-subtitle`
- **Řádek 2102:** V sekci INSTRUCTORS SECTION
- **Řádek 3068:** V sekci před THANK YOU PAGE (prázdná deklarace)
- **Problém:** Druhý výskyt je prázdný a zbytečný

---

### B) Duplicitní `.filter-options`
- **Řádek 1656:** První definice
- **Řádek 1693:** Druhá definice
- **Duplicita:** 100%

---

### C) Duplicitní `.show-more-btn`
- **Řádek 1681:** V SIDEBAR FILTERS
- **Řádek 1800:** Znovu definován
- **Duplicita:** 100%

---

### D) Duplicitní `.price-range`
- **Řádek 1669:** První definice
- **Řádek 1727:** Druhá definice
- **Duplicita:** 100%

---

### E) Duplicitní "DISABLED ANSWER STYLES"
- **Řádek 19111:** První výskyt
- **Řádek 19112:** Duplicitní komentář
- **Problém:** Identický komentář na dvou po sobě jdoucích řádcích

---

## 4. CSS proměnné

### A) `--indicator-left` a `--indicator-width`

**Zachována pouze první definice** (refaktoring proveden):
- **Řádky 3479-3480:** První `.tabs` (ZACHOVÁNO ✅)

**Odstraněno z:**
1. ~~Řádky ~6023-6024:~~ Druhý `.tabs` (ODSTRANĚNO ✅)
2. ~~Řádky ~6472-6473:~~ `.sidebar-tabs` (ODSTRANĚNO ✅)
3. ~~Řádky ~12849-12850:~~ Třetí `.tabs` v SETTINGS TAB (ODSTRANĚNO ✅)
4. ~~Řádky ~13676-13677:~~ `.subscription-tabs` (ODSTRANĚNO ✅)

**Poznámka:** Všechny třídy stále používají `var(--indicator-left)` a `var(--indicator-width)` ve svých `::after` pseudoelementech.

---

### B) `--bar-left` a `--bar-width`

**Použití (ne definice):**
- **Řádky 643-644:** V `.category-tabs::before` - `left: var(--bar-left, 0); width: var(--bar-width, 0);`
- **Řádky 1408-1409:** V `.plan-tabs::before` - stejné použití

**Poznámka:** Tyto proměnné jsou pouze **používány**, nikoli **definovány** v CSS. Pravděpodobně se nastavují dynamicky přes JavaScript.

---

## 5. Doporučení pro refaktoring

### 🎯 Priorita 1: Kritické duplicity (nutno odstranit)

1. **Globální komponenty do samostatných souborů:**
   ```
   components/
   ├── _header.css (7× duplicitní)
   ├── _searchbar.css (7× duplicitní)
   ├── _mobile-menu.css (7× duplicitní)
   ├── _desktop-menu.css (7× duplicitní)
   ├── _buttons.css (7× duplicitní)
   ├── _footer.css (7× duplicitní)
   └── _bubbles.css (5× duplicitní)
   ```

2. **Sdílené komponenty:**
   ```
   components/
   ├── _hero.css (6× s variacemi)
   ├── _tabs.css (5× s variacemi)
   ├── _modals.css (různé modály)
   ├── _cards.css (news-card, course-card, atd.)
   └── _swiper-navigation.css
   ```

---

### 🎯 Priorita 2: Strukturální reorganizace

**Doporučená struktura:**
```
src/
├── base/
│   ├── _reset.css
│   ├── _variables.css (CSS proměnné)
│   └── _typography.css
├── components/
│   ├── _header.css
│   ├── _footer.css
│   ├── _buttons.css
│   ├── _cards.css
│   ├── _tabs.css
│   ├── _modals.css
│   └── _forms.css
├── layout/
│   ├── _hero.css
│   ├── _sidebar.css
│   └── _grid.css
└── pages/
    ├── _home.css
    ├── _course-detail.css
    ├── _course-enrolled.css
    ├── _profile.css
    ├── _cart.css
    ├── _checkout.css
    ├── _instructor.css
    └── _tests.css
```

---

### 🎯 Priorita 3: Optimalizace CSS proměnných

**Centralizované proměnné:**
```css
:root {
  /* Colors */
  --color-primary: #0069B2;
  --color-secondary: #28A6FF;
  --color-accent: #00E8E8;
  
  /* Indicators */
  --indicator-left: 0px;
  --indicator-width: 0px;
  --bar-left: 0;
  --bar-width: 0;
  
  /* Spacing */
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 2rem;
}
```

---

### 🎯 Priorita 4: Odstranění prázdných/duplicitních deklarací

**K odstranění:**
1. Řádek 3068: `.instructors-subtitle { }` (prázdná)
2. Řádek 19112: Duplicitní komentář
3. Řádek 1693: Duplicitní `.filter-options`
4. Řádek 1800: Duplicitní `.show-more-btn`
5. Řádek 1727: Duplicitní `.price-range`

---

### 📊 Statistika duplicit

| Komponenta | Počet výskytů | Řádků celkem | Úspora (odhadem) |
|------------|---------------|--------------|------------------|
| HEADER | 7 | ~700 | ~600 řádků |
| SEARCHBAR | 7 | ~700 | ~600 řádků |
| MOBILE MENU | 7 | ~210 | ~180 řádků |
| DESKTOP MENU | 7 | ~210 | ~180 řádků |
| BUTTONS | 7 | ~140 | ~120 řádků |
| FOOTER | 7 | ~1540 | ~1320 řádků |
| HERO SECTION | 8 | ~1280 | ~900 řádků |
| BUBBLES | 5 | ~50 | ~40 řádků |
| TABS | 5 | ~200 | ~150 řádků |
| REVIEWS | 3 | ~480 | ~320 řádků |
| **CELKEM** | - | **~5,510** | **~4,410 řádků** |

**Potenciální redukce:** ~21% ze současných 20,776 řádků

---

### ✅ Výhody refaktoringu

1. **Menší velikost souboru:** Z 20,776 na ~16,000 řádků
2. **Lepší udržitelnost:** Změna komponenty na jednom místě
3. **Konzistence:** Jednotný styl napříč stránkami
4. **Rychlejší načítání:** Menší CSS soubor
5. **Snadnější debugging:** Přehledná struktura

---

### ⚠️ Poznámky k implementaci

1. **Testování:** Po každé změně otestovat všechny stránky
2. **Postupný přechod:** Refaktorovat po sekcích, ne vše najednou
3. **Git commits:** Dělat commits po každé větší změně
4. **Backup:** Zálohovat před začátkem refaktoringu
5. **CSS Modules/Scope:** Zvážit použití CSS modulů nebo scoped stylů

---

## Závěr

Soubor `style.css` obsahuje **masivní duplicity** napříč 8 hlavními stránkami projektu. Hlavní problémy:

- **Header/Footer/Navigation:** Duplikováno 7× (každá stránka má vlastní kopii)
- **Hero Section:** 8 různých verzí s 60-90% překryvem
- **Responsive styly:** Duplikované media queries napříč sekcemi
- **CSS proměnné:** Částečně vyřešeno, ale je potřeba centralizace

**Doporučení:** Provést strukturální refaktoring s rozdělením do komponent podle výše uvedené struktury. To zlepší udržitelnost, sníží velikost kódu a usnadní budoucí vývoj.

---

**Konec dokumentace**
