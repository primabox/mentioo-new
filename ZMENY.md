# Návrh implementace přejmenování duplicitních CSS tříd

**Datum vytvoření:** 14. listopadu 2025  
**Status:** Návrh - Před implementací  
**Založeno na:** DUPLICITY_DOKUMENTACE.md

---

## ⚠️ DŮLEŽITÉ UPOZORNĚNÍ

Tento dokument popisuje **alternativní přístup** k řešení duplicit v `style.css`. 

### Doporučený přístup (PRIORITA 1):
✅ **Odstranit duplicitní sekce** a používat sdílené komponenty  
✅ Zachovat pouze jednu verzi každé komponenty  
✅ Všechny HTML soubory budou používat stejné třídy  

### Popisovaný přístup (ALTERNATIVA):
⚠️ **Přejmenovat duplicitní třídy** podle sekce  
⚠️ Vyžaduje úpravy CSS i HTML souborů  
⚠️ Složitější údržba, ale zachovává nezávislost sekcí  

---

## 📋 Obsah
1. [Mapování HTML souborů na CSS sekce](#mapování-html-souborů-na-css-sekce)
2. [Konvence pojmenování](#konvence-pojmenování)
3. [Detailní plán přejmenování](#detailní-plán-přejmenování)
4. [Implementační kroky](#implementační-kroky)
5. [Kontrolní checklist](#kontrolní-checklist)

---

## 1. Mapování HTML souborů na CSS sekce

### 1.1 INDEX (Hlavní stránka)
- **HTML soubor:** `index.html`
- **CSS sekce:** Řádky 3-1506 (INDEX)
- **Třídy:** Zachovat původní názvy (`.header`, `.navbar`, `.logo`, atd.)
- **Poznámka:** Toto je REFERENČNÍ implementace

---

### 1.2 COURSE DETAIL (Detail kurzu - nezahájený)
- **HTML soubor:** `detail-kurzu.html`
- **CSS sekce:** Řádky 5601-8478 (COURSE DETAIL PAGE - KURZ DETAIL)
- **Prefix:** `cd-` (course-detail)
- **Příklad:** `.header` → `.cd-header`

---

### 1.3 COURSE ENROLLED (Detail kurzu - přihlášený)
- **HTML soubory:** 
  - `detail-kurzu-prihlaseny.html`
  - `detail-kurzu-prihlaseny-hotovo.html`
  - `detail-kurzu-nezahajeny.html`
- **CSS sekce:** Řádky 3362-5597 (DETAIL KURZU PŘIHLÁŠENÝ)
- **Prefix:** `ce-` (course-enrolled)
- **Příklad:** `.header` → `.ce-header`

---

### 1.4 LESSON DETAIL (Detail lekce)
- **HTML soubor:** `detail-lekce.html`
- **CSS sekce:** Řádky 8478-11174 (DETAIL STYLE)
- **Prefix:** `ld-` (lesson-detail)
- **Příklad:** `.header` → `.ld-header`

---

### 1.5 PROFILE (Můj profil)
- **HTML soubor:** `muj-profil.html`
- **CSS sekce:** Řádky 11177-14290 (PROFILE PAGE - MŮJ PROFIL)
- **Prefix:** `pf-` (profile)
- **Příklad:** `.header` → `.pf-header`

---

### 1.6 SHOPPING CART (Nákupní košík)
- **HTML soubory:**
  - `nakupni-kosik.html`
  - `nakupni-kosik-prazdny.html`
- **CSS sekce:** Řádky 14293-15685 (SHOPPING CART PAGE - NÁKUPNÍ KOŠÍK)
- **Prefix:** `cart-` (cart)
- **Příklad:** `.header` → `.cart-header`

---

### 1.7 CHECKOUT (Pokladna)
- **HTML soubory:**
  - `pokladna.html`
  - `pokladna2.html`
- **CSS sekce:** Řádky 15688-16821 (CHECKOUT PAGE - POKLADNA)
- **Prefix:** `co-` (checkout)
- **Příklad:** `.header` → `.co-header`

---

### 1.8 INSTRUCTOR PROFILE (Profil lektora)
- **HTML soubor:** `profil-lektora.html`
- **CSS sekce:** Řádky 16822-18432 (PROFIL LEKTORA)
- **Prefix:** `ip-` (instructor-profile)
- **Příklad:** `.header` → `.ip-header`

---

### 1.9 TESTS (Testové stránky)
- **HTML soubory:**
  - `test1.html` až `test7.html`
  - `test7-complete.html`, `test7-failed.html`
  - `test_vyhodnoceni1.html` až `test_vyhodnoceni5.html`
- **CSS sekce:** Řádky 18435-konec (TEST PAGE STYLES)
- **Prefix:** `test-` (test)
- **Příklad:** `.header` → `.test-header`

---

### 1.10 CATEGORY (Kategorie kurzů)
- **HTML soubor:** `kategorie-kurzu.html`
- **CSS sekce:** Řádky 1507-3072 (HERO SECTION CATEGORY + filtry)
- **Prefix:** `cat-` (category)
- **Poznámka:** Používá některé INDEX komponenty, některé vlastní

---

### 1.11 THANK YOU PAGE
- **HTML soubor:** `thankYou.html`
- **CSS sekce:** Řádky 3072-3361 (MIGRATED: THANK YOU PAGE & FEATURES)
- **Prefix:** `ty-` (thank-you)

---

## 2. Konvence pojmenování

### 2.1 Pravidla pro prefixy
```
INDEX:              Žádný prefix (referenční)
Course Detail:      cd-
Course Enrolled:    ce-
Lesson Detail:      ld-
Profile:            pf-
Shopping Cart:      cart-
Checkout:           co-
Instructor Profile: ip-
Tests:              test-
Category:           cat-
Thank You:          ty-
```

### 2.2 Příklady transformace
```css
/* PŘED */
.header { ... }
.navbar { ... }
.footer { ... }

/* PO (pro Course Detail) */
.cd-header { ... }
.cd-navbar { ... }
.cd-footer { ... }
```

---

## 3. Detailní plán přejmenování

### 3.1 HEADER Komponenta (7× duplicitní)

#### INDEX (ZACHOVAT)
**Řádky:** 3-14  
**Třídy:** `.header`, `.navbar`, `.logo`  
**Akce:** ✅ Žádná změna

#### COURSE DETAIL
**Řádky:** 5624-5636  
**Změny:**
```css
/* PŘED */
.header { ... }
.navbar { ... }
.logo { ... }

/* PO */
.cd-header { ... }
.cd-navbar { ... }
.cd-logo { ... }
```
**HTML soubor:** `detail-kurzu.html`

#### DETAIL STYLE (Lesson Detail)
**Řádky:** 8504-8516  
**Změny:**
```css
.ld-header { ... }
.ld-navbar { ... }
.ld-logo { ... }
```
**HTML soubor:** `detail-lekce.html`

#### PROFILE PAGE
**Řádky:** 11203-11215  
**Změny:**
```css
.pf-header { ... }
.pf-navbar { ... }
.pf-logo { ... }
```
**HTML soubor:** `muj-profil.html`

#### SHOPPING CART
**Řádky:** 14319-14331  
**Změny:**
```css
.cart-header { ... }
.cart-navbar { ... }
.cart-logo { ... }
```
**HTML soubory:** `nakupni-kosik.html`, `nakupni-kosik-prazdny.html`

#### CHECKOUT
**Řádky:** 15715-15727  
**Změny:**
```css
.co-header { ... }
.co-navbar { ... }
.co-logo { ... }
```
**HTML soubory:** `pokladna.html`, `pokladna2.html`

#### INSTRUCTOR PROFILE
**Řádky:** 16825-16837  
**Změny:**
```css
.ip-header { ... }
.ip-navbar { ... }
.ip-logo { ... }
```
**HTML soubor:** `profil-lektora.html`

#### TEST PAGE
**Řádky:** 18461-18473  
**Změny:**
```css
.test-header { ... }
.test-navbar { ... }
.test-logo { ... }
```
**HTML soubory:** `test1.html` až `test7.html` + všechny test varianty

---

### 3.2 SEARCHBAR Komponenta (7× duplicitní)

#### INDEX (ZACHOVAT)
**Řádky:** 16-35  
**Třídy:** `.searchbar-container`, `.search-form`, `.search-wrapper`, `.search-icon`, `.search-input`

#### COURSE DETAIL
**Řádky:** 5637-5657
```css
.cd-searchbar-container { ... }
.cd-search-form { ... }
.cd-search-wrapper { ... }
.cd-search-icon { ... }
.cd-search-input { ... }
```

#### LESSON DETAIL
**Řádky:** 8517-8541
```css
.ld-searchbar-container { ... }
.ld-search-form { ... }
.ld-search-wrapper { ... }
.ld-search-icon { ... }
.ld-search-input { ... }
```

#### PROFILE
**Řádky:** 11216-11240
```css
.pf-searchbar-container { ... }
.pf-search-form { ... }
.pf-search-wrapper { ... }
.pf-search-icon { ... }
.pf-search-input { ... }
```

#### SHOPPING CART
**Řádky:** 14332-14352
```css
.cart-searchbar-container { ... }
.cart-search-form { ... }
.cart-search-wrapper { ... }
.cart-search-icon { ... }
.cart-search-input { ... }
```

#### CHECKOUT
**Řádky:** 15728-15748
```css
.co-searchbar-container { ... }
.co-search-form { ... }
.co-search-wrapper { ... }
.co-search-icon { ... }
.co-search-input { ... }
```

#### INSTRUCTOR PROFILE
**Řádky:** 16838-16858
```css
.ip-searchbar-container { ... }
.ip-search-form { ... }
.ip-search-wrapper { ... }
.ip-search-icon { ... }
.ip-search-input { ... }
```

#### TEST PAGE
**Řádky:** 18474-18498
```css
.test-searchbar-container { ... }
.test-search-form { ... }
.test-search-wrapper { ... }
.test-search-icon { ... }
.test-search-input { ... }
```

---

### 3.3 MOBILE MENU Komponenta (7× duplicitní)

#### INDEX (ZACHOVAT)
**Řádky:** 37-64  
**Třídy:** `.hamburger`, `.hamburger-btn`, `.mobile-menu`, `.mobile-menu.active`, `.mobile-link`, `.mobile-btn`

#### Přejmenování pro ostatní sekce:

**COURSE DETAIL** (Řádky 5658-5686):
```css
.cd-hamburger { ... }
.cd-hamburger-btn { ... }
.cd-mobile-menu { ... }
.cd-mobile-menu.active { ... }
.cd-mobile-link { ... }
.cd-mobile-btn { ... }
```

**LESSON DETAIL** (Řádky 8542-8574):
```css
.ld-hamburger { ... }
.ld-hamburger-btn { ... }
.ld-mobile-menu { ... }
.ld-mobile-menu.active { ... }
.ld-mobile-link { ... }
.ld-mobile-btn { ... }
```

**PROFILE** (Řádky 11241-11273):
```css
.pf-hamburger { ... }
.pf-hamburger-btn { ... }
.pf-mobile-menu { ... }
.pf-mobile-menu.active { ... }
.pf-mobile-link { ... }
.pf-mobile-btn { ... }
```

**SHOPPING CART** (Řádky 14353-14381):
```css
.cart-hamburger { ... }
.cart-hamburger-btn { ... }
.cart-mobile-menu { ... }
.cart-mobile-menu.active { ... }
.cart-mobile-link { ... }
.cart-mobile-btn { ... }
```

**CHECKOUT** (Řádky 15749-15777):
```css
.co-hamburger { ... }
.co-hamburger-btn { ... }
.co-mobile-menu { ... }
.co-mobile-menu.active { ... }
.co-mobile-link { ... }
.co-mobile-btn { ... }
```

**INSTRUCTOR PROFILE** (Řádky 16859-16889):
```css
.ip-hamburger { ... }
.ip-hamburger-btn { ... }
.ip-mobile-menu { ... }
.ip-mobile-menu.active { ... }
.ip-mobile-link { ... }
.ip-mobile-btn { ... }
```

**TEST PAGE** (Řádky 18499-18531):
```css
.test-hamburger { ... }
.test-hamburger-btn { ... }
.test-mobile-menu { ... }
.test-mobile-menu.active { ... }
.test-mobile-link { ... }
.test-mobile-btn { ... }
```

---

### 3.4 DESKTOP MENU Komponenta (7× duplicitní)

#### INDEX (ZACHOVAT)
**Řádky:** 66-90  
**Třídy:** `.navbar-menu`, `.nav-links`, `.nav-item`, `.nav-link`, `.dropdown`, `.dropdown-link`

#### Přejmenování vzor:

**COURSE DETAIL** (Řádky 5687-5712):
```css
.cd-navbar-menu { ... }
.cd-nav-links { ... }
.cd-nav-item { ... }
.cd-nav-link { ... }
.cd-dropdown { ... }
.cd-dropdown-link { ... }
```

**LESSON DETAIL** (Řádky 8575-8602):
```css
.ld-navbar-menu { ... }
/* atd. */
```

**PROFILE** (Řádky 11274-11301):
```css
.pf-navbar-menu { ... }
/* atd. */
```

**SHOPPING CART** (Řádky 14382-14407):
```css
.cart-navbar-menu { ... }
/* atd. */
```

**CHECKOUT** (Řádky 15778-15803):
```css
.co-navbar-menu { ... }
/* atd. */
```

**INSTRUCTOR PROFILE** (Řádky 16890-16915):
```css
.ip-navbar-menu { ... }
/* atd. */
```

**TEST PAGE** (Řádky 18532-18559):
```css
.test-navbar-menu { ... }
/* atd. */
```

---

### 3.5 BUTTONS Komponenta (7× duplicitní)

#### INDEX (ZACHOVAT)
**Řádky:** 92-107  
**Třídy:** `.btn-outline`, `.btn-primary`, `.icon-btn`, `.icon-btn-alt`

#### Přejmenování vzor:

**COURSE DETAIL** (Řádky 5713-5766):
```css
.cd-btn-outline { ... }
.cd-btn-primary { ... }
.cd-icon-btn { ... }
.cd-icon-btn-alt { ... }
```

**Poznámka:** COURSE DETAIL má rozšířenou verzi s dodatečnými třídami - ty také přejmenovat s prefixem `cd-`

**LESSON DETAIL** (Řádky 8603-8627):
```css
.ld-btn-outline { ... }
.ld-btn-primary { ... }
.ld-icon-btn { ... }
.ld-icon-btn-alt { ... }
```

**PROFILE** (Řádky 11311-11319):
```css
.pf-btn-outline { ... }
.pf-btn-primary { ... }
.pf-icon-btn { ... }
.pf-icon-btn-alt { ... }
```

**SHOPPING CART** (Řádky 14408-14424):
```css
.cart-btn-outline { ... }
.cart-btn-primary { ... }
.cart-icon-btn { ... }
.cart-icon-btn-alt { ... }
```

**CHECKOUT** (Řádky 15804-15820):
```css
.co-btn-outline { ... }
.co-btn-primary { ... }
.co-icon-btn { ... }
.co-icon-btn-alt { ... }
```

**INSTRUCTOR PROFILE** (Řádky 16916-16924):
```css
.ip-btn-outline { ... }
.ip-btn-primary { ... }
.ip-icon-btn { ... }
.ip-icon-btn-alt { ... }
```

**TEST PAGE** (Řádky 18569-18577):
```css
.test-btn-outline { ... }
.test-btn-primary { ... }
.test-icon-btn { ... }
.test-icon-btn-alt { ... }
```

---

### 3.6 HERO SECTION Komponenta (8× duplicitní)

**Poznámka:** Hero sekce mají větší variabilitu - některé jsou značně upravené.

#### INDEX (ZACHOVAT)
**Řádky:** 109-269  
**Hlavní třídy:** `.hero-section`, `.hero-wrapper`, `.hero-gradient`, `.hero-content`, `.hero-texts`, `.hero-title`, `.hero-paragraph`, `.hero-buttons`

#### COURSE ENROLLED (DETAIL KURZU PŘIHLÁŠENÝ)
**Řádky:** 3394-3465
```css
.ce-hero-gradient { ... }
.ce-hero-bg { ... }
.ce-hero-title { ... }
.ce-hero-description { ... }
/* atd. */
```

#### COURSE DETAIL
**Řádky:** 5809-5889
```css
.cd-hero-section { ... }
.cd-hero-wrapper { ... }
.cd-hero-gradient { ... }
/* atd. */
```

#### LESSON DETAIL
**Řádky:** 8655-8698
```css
.ld-hero-section { ... }
.ld-hero-gradient { ... }
/* atd. */
```

#### PROFILE
**Řádky:** 11320-11368
```css
.pf-hero-section { ... }
.pf-hero-bg { ... }
/* atd. */
```

#### SHOPPING CART
**Řádky:** 14425-14470
```css
.cart-hero-section { ... }
.cart-hero-gradient { ... }
/* atd. */
```

#### CHECKOUT
**Řádky:** 15821-15866
```css
.co-hero-section { ... }
.co-hero-gradient { ... }
/* atd. */
```

#### INSTRUCTOR PROFILE
**Řádky:** 16945-17102
```css
.ip-hero-section { ... }
.ip-hero-gradient { ... }
/* atd. */
```

#### TEST PAGE
**Řádky:** 18578-18633
```css
.test-hero-section { ... }
.test-hero-bg { ... }
/* atd. */
```

---

### 3.7 BUBBLES Komponenta (5× duplicitní)

#### INDEX (ZACHOVAT)
**Řádky:** 125, 129  
**Třídy:** `.bubble-field`, `.bubble`

#### COURSE DETAIL
**Řádky:** 5615-5623
```css
.cd-bubble-field { ... }
.cd-bubble { ... }
```

#### PROFILE
**Řádky:** 11194-11202
```css
.pf-bubble-field { ... }
.pf-bubble { ... }
```

#### SHOPPING CART
**Řádky:** 14310-14318
```css
.cart-bubble-field { ... }
.cart-bubble { ... }
```

#### CHECKOUT
**Řádky:** 15706-15714
```css
.co-bubble-field { ... }
.co-bubble { ... }
```

#### TEST PAGE
**Řádky:** 18452-18460
```css
.test-bubble-field { ... }
.test-bubble { ... }
```

---

### 3.8 TABS Komponenta (5× duplicitní)

#### COURSE ENROLLED (PRVNÍ VÝSKYT - ZACHOVAT JAKO REFERENČNÍ)
**Řádky:** 3472-3507  
**Třídy:** `.tabs-wrapper`, `.tabs`, `.tab`, `.tab.active`, `.tab:hover`  
**Obsahuje:** CSS proměnné `--indicator-left` a `--indicator-width`

#### COURSE DETAIL
**Řádky:** 6014-6062
```css
.cd-tabs-wrapper { ... }
.cd-tabs { ... }
.cd-tab { ... }
.cd-tab.active { ... }
.cd-tab:hover { ... }
```

#### LESSON DETAIL
**Řádky:** 8761-8814
```css
.ld-tabs-wrapper { ... }
.ld-tabs { ... }
.ld-tab { ... }
/* atd. */
```

#### PROFILE - SETTINGS TAB
**Řádky:** 12837-12862
```css
.pf-tabs-wrapper { ... }
.pf-tabs { ... }
.pf-tab { ... }
/* atd. */
```

#### INSTRUCTOR PROFILE
**Řádky:** 17166-17214
```css
.ip-tabs-wrapper { ... }
.ip-tabs { ... }
.ip-tab { ... }
/* atd. */
```

---

### 3.9 FOOTER Komponenta (7× duplicitní)

**Poznámka:** Footer je jedna z nejrozsáhlejších komponent (~220 řádků na instanci)

#### INDEX (ZACHOVAT)
**Řádky:** 851-1070  
**Hlavní třídy:** 
- `.footer`
- `.footer-container`
- `.footer-logo`
- `.footer-logo-img`
- `.footer-content`
- `.footer-grid`
- `.footer-info`
- `.footer-info-text`
- `.footer-categories`
- `.footer-heading`
- `.footer-links`
- `.footer-link`
- `.footer-about`
- `.footer-divider`
- `.footer-bottom`
- `.footer-copyright`
- `.footer-social`
- `.social-link`

#### COURSE ENROLLED
**Řádky:** 4025-4097
```css
.ce-footer { ... }
.ce-footer-container { ... }
.ce-footer-logo { ... }
.ce-footer-logo-img { ... }
/* atd. pro všechny třídy */
```

#### COURSE DETAIL
**Řádky:** 6174-6394
```css
.cd-footer { ... }
.cd-footer-container { ... }
/* atd. */
```

#### LESSON DETAIL
**Řádky:** 9652-9728
```css
.ld-footer { ... }
.ld-footer-container { ... }
/* atd. */
```

#### PROFILE
**Řádky:** 12148-12230
```css
.pf-footer { ... }
.pf-footer-container { ... }
/* atd. */
```

#### SHOPPING CART
**Řádky:** 14918-14993
```css
.cart-footer { ... }
.cart-footer-container { ... }
/* atd. */
```

#### CHECKOUT
**Řádky:** 16378-16454
```css
.co-footer { ... }
.co-footer-container { ... }
/* atd. */
```

#### INSTRUCTOR PROFILE
**Řádky:** 17606-17825
```css
.ip-footer { ... }
.ip-footer-container { ... }
/* atd. */
```

---

### 3.10 TAB CONTENT Komponenta (4× duplicitní)

#### COURSE ENROLLED (REFERENČNÍ)
**Řádky:** 3508-3514
```css
.tab-content { ... }
.tab-content.active { ... }
```

#### COURSE DETAIL
**Řádky:** 6063-6088
```css
.cd-tab-content { ... }
.cd-tab-content.active { ... }
```

#### LESSON DETAIL
**Řádky:** 8815-8907
```css
.ld-tab-content { ... }
.ld-tab-content.active { ... }
```

#### INSTRUCTOR PROFILE
**Řádky:** 17215-17225
```css
.ip-tab-content { ... }
.ip-tab-content.active { ... }
```

---

### 3.11 SIDEBAR Komponenta (6× duplicitní)

**Poznámka:** Sidebar má různé účely v různých sekcích

#### COURSE ENROLLED (REFERENČNÍ)
**Řádky:** 3833-3847
```css
.sidebar { ... }
```

#### COURSE DETAIL
**Řádky:** 6089-6173
```css
.cd-sidebar { ... }
```

#### LESSON DETAIL
**Řádky:** 8942-9150
```css
.ld-sidebar { ... }
```

#### PROFILE
**Řádky:** 11997-12147
```css
.pf-sidebar { ... }
```

#### SHOPPING CART
**Řádky:** 14691-14774
```css
.cart-sidebar { ... }
```

#### TEST PAGE
**Řádky:** 19460-19469
```css
.test-sidebar { ... }
```

---

### 3.12 REVIEWS SECTION Komponenta (3× duplicitní)

#### INDEX (ZACHOVAT)
**Řádky:** 692-850  
**Třídy:** `.reviews-section`, `.reviews-header`, `.reviews-title`, `.reviews-subtitle`, `.myReviewsSwiper`, `.review-card`, atd.

#### COURSE DETAIL
**Řádky:** 6893-7126
```css
.cd-reviews-section { ... }
.cd-reviews-header { ... }
.cd-reviews-title { ... }
.cd-reviews-subtitle { ... }
/* atd. */
```

#### INSTRUCTOR PROFILE
**Řádky:** 18093-18431
```css
.ip-reviews-section { ... }
.ip-reviews-header { ... }
/* atd. */
```

---

### 3.13 Další duplicitní komponenty

#### CONTENT CARD (4×)
**Referenční:** Řádky 3466-3471 (COURSE ENROLLED)
- COURSE DETAIL: `cd-content-card`
- LESSON DETAIL: `ld-content-card`
- INSTRUCTOR PROFILE: `ip-content-card`

#### MAIN CONTENT (4×)
**Referenční:** Řádky 1581-1585
- COURSE ENROLLED: `ce-main-content`
- COURSE DETAIL: `cd-main-content`
- LESSON DETAIL: `ld-main-content`
- INSTRUCTOR PROFILE: `ip-main-content`

---

## 4. Implementační kroky

### Fáze 1: Příprava (KRITICKÁ)
1. ✅ **Vytvořit backup celého projektu**
2. ✅ **Vytvořit novou Git branch** `feature/rename-duplicate-classes`
3. ✅ **Připravit mapping tabulku** (tento dokument)
4. ✅ **Otestovat současný web** - zaznamenat všechny funkcionality

### Fáze 2: CSS Úpravy
Pro každou sekci (kromě INDEX):

1. **Identifikovat řádky** podle DUPLICITY_DOKUMENTACE.md
2. **Najít všechny třídy** v dané sekci pomocí regex: `^\s*\.([\w-]+)\s*\{`
3. **Přejmenovat třídy** v CSS souboru:
   ```
   .header { → .cd-header {
   .navbar { → .cd-navbar {
   ```
4. **Aktualizovat závislé selektory**:
   ```
   .header .navbar → .cd-header .cd-navbar
   ```
5. **Zkontrolovat pseudo-třídy**:
   ```
   .mobile-menu.active → .cd-mobile-menu.active
   ```

### Fáze 3: HTML Úpravy
Pro každý HTML soubor:

1. **Identifikovat soubor** podle mappingu
2. **Najít všechny výskyty** starých tříd
3. **Nahradit** odpovídajícím prefixem
4. **Zkontrolovat JavaScript** reference (pokud existují)

### Fáze 4: JavaScript Úpravy
1. **Vyhledat** všechny `.querySelector()` a `.getElementsByClassName()`
2. **Aktualizovat** názvy tříd
3. **Zkontrolovat** event listenery

### Fáze 5: Testování
1. **Otevřít každou stránku** v prohlížeči
2. **Ověřit vzhled** - porovnat se screenshoty z Fáze 1
3. **Otestovat interaktivitu**:
   - Hamburger menu
   - Dropdowny
   - Modály
   - Formuláře
   - Swipery
4. **Responsive design** - otestovat všechny breakpointy
5. **Konzole** - zkontrolovat, že nejsou chyby

### Fáze 6: Dokumentace
1. **Aktualizovat ZMENY.md** se skutečnými změnami
2. **Vytvořit migration guide** pro ostatní vývojáře
3. **Zdokumentovat** všechny nalezené problémy

---

## 5. Kontrolní checklist

### 5.1 CSS Checklist

#### HEADER Komponenta
- [ ] INDEX - Zachováno ✅
- [ ] COURSE DETAIL - Přejmenováno na `cd-*`
- [ ] LESSON DETAIL - Přejmenováno na `ld-*`
- [ ] PROFILE - Přejmenováno na `pf-*`
- [ ] SHOPPING CART - Přejmenováno na `cart-*`
- [ ] CHECKOUT - Přejmenováno na `co-*`
- [ ] INSTRUCTOR PROFILE - Přejmenováno na `ip-*`
- [ ] TEST PAGE - Přejmenováno na `test-*`

#### SEARCHBAR Komponenta
- [ ] INDEX - Zachováno ✅
- [ ] COURSE DETAIL - `cd-searchbar-*`
- [ ] LESSON DETAIL - `ld-searchbar-*`
- [ ] PROFILE - `pf-searchbar-*`
- [ ] SHOPPING CART - `cart-searchbar-*`
- [ ] CHECKOUT - `co-searchbar-*`
- [ ] INSTRUCTOR PROFILE - `ip-searchbar-*`
- [ ] TEST PAGE - `test-searchbar-*`

#### MOBILE MENU Komponenta
- [ ] INDEX - Zachováno ✅
- [ ] COURSE DETAIL - `cd-hamburger`, `cd-mobile-*`
- [ ] LESSON DETAIL - `ld-hamburger`, `ld-mobile-*`
- [ ] PROFILE - `pf-hamburger`, `pf-mobile-*`
- [ ] SHOPPING CART - `cart-hamburger`, `cart-mobile-*`
- [ ] CHECKOUT - `co-hamburger`, `co-mobile-*`
- [ ] INSTRUCTOR PROFILE - `ip-hamburger`, `ip-mobile-*`
- [ ] TEST PAGE - `test-hamburger`, `test-mobile-*`

#### DESKTOP MENU Komponenta
- [ ] INDEX - Zachováno ✅
- [ ] COURSE DETAIL - `cd-navbar-menu`, `cd-nav-*`, `cd-dropdown*`
- [ ] LESSON DETAIL - `ld-navbar-menu`, `ld-nav-*`, `ld-dropdown*`
- [ ] PROFILE - `pf-navbar-menu`, `pf-nav-*`, `pf-dropdown*`
- [ ] SHOPPING CART - `cart-navbar-menu`, `cart-nav-*`, `cart-dropdown*`
- [ ] CHECKOUT - `co-navbar-menu`, `co-nav-*`, `co-dropdown*`
- [ ] INSTRUCTOR PROFILE - `ip-navbar-menu`, `ip-nav-*`, `ip-dropdown*`
- [ ] TEST PAGE - `test-navbar-menu`, `test-nav-*`, `test-dropdown*`

#### BUTTONS Komponenta
- [ ] INDEX - Zachováno ✅
- [ ] COURSE DETAIL - `cd-btn-*`, `cd-icon-btn*`
- [ ] LESSON DETAIL - `ld-btn-*`, `ld-icon-btn*`
- [ ] PROFILE - `pf-btn-*`, `pf-icon-btn*`
- [ ] SHOPPING CART - `cart-btn-*`, `cart-icon-btn*`
- [ ] CHECKOUT - `co-btn-*`, `co-icon-btn*`
- [ ] INSTRUCTOR PROFILE - `ip-btn-*`, `ip-icon-btn*`
- [ ] TEST PAGE - `test-btn-*`, `test-icon-btn*`

#### FOOTER Komponenta
- [ ] INDEX - Zachováno ✅
- [ ] COURSE ENROLLED - `ce-footer*`
- [ ] COURSE DETAIL - `cd-footer*`
- [ ] LESSON DETAIL - `ld-footer*`
- [ ] PROFILE - `pf-footer*`
- [ ] SHOPPING CART - `cart-footer*`
- [ ] CHECKOUT - `co-footer*`
- [ ] INSTRUCTOR PROFILE - `ip-footer*`

#### HERO SECTION
- [ ] INDEX - Zachováno ✅
- [ ] COURSE ENROLLED - `ce-hero-*`
- [ ] COURSE DETAIL - `cd-hero-*`
- [ ] LESSON DETAIL - `ld-hero-*`
- [ ] PROFILE - `pf-hero-*`
- [ ] SHOPPING CART - `cart-hero-*`
- [ ] CHECKOUT - `co-hero-*`
- [ ] INSTRUCTOR PROFILE - `ip-hero-*`
- [ ] TEST PAGE - `test-hero-*`

#### BUBBLES
- [ ] INDEX - Zachováno ✅
- [ ] COURSE DETAIL - `cd-bubble*`
- [ ] PROFILE - `pf-bubble*`
- [ ] SHOPPING CART - `cart-bubble*`
- [ ] CHECKOUT - `co-bubble*`
- [ ] TEST PAGE - `test-bubble*`

#### TABS
- [ ] COURSE ENROLLED - Zachováno jako referenční ✅
- [ ] COURSE DETAIL - `cd-tabs*`, `cd-tab*`
- [ ] LESSON DETAIL - `ld-tabs*`, `ld-tab*`
- [ ] PROFILE - `pf-tabs*`, `pf-tab*`
- [ ] INSTRUCTOR PROFILE - `ip-tabs*`, `ip-tab*`

#### TAB CONTENT
- [ ] COURSE ENROLLED - Zachováno ✅
- [ ] COURSE DETAIL - `cd-tab-content*`
- [ ] LESSON DETAIL - `ld-tab-content*`
- [ ] INSTRUCTOR PROFILE - `ip-tab-content*`

#### SIDEBAR
- [ ] COURSE ENROLLED - Zachováno ✅
- [ ] COURSE DETAIL - `cd-sidebar*`
- [ ] LESSON DETAIL - `ld-sidebar*`
- [ ] PROFILE - `pf-sidebar*`
- [ ] SHOPPING CART - `cart-sidebar*`
- [ ] TEST PAGE - `test-sidebar*`

#### REVIEWS SECTION
- [ ] INDEX - Zachováno ✅
- [ ] COURSE DETAIL - `cd-reviews-*`, `cd-review-*`
- [ ] INSTRUCTOR PROFILE - `ip-reviews-*`, `ip-review-*`

---

### 5.2 HTML Checklist

#### Homepage
- [ ] `index.html` - Žádné změny (používá referenční třídy)

#### Course Pages
- [ ] `detail-kurzu.html` - Aktualizovat na `cd-*` prefixy
- [ ] `detail-kurzu-prihlaseny.html` - Aktualizovat na `ce-*` prefixy
- [ ] `detail-kurzu-prihlaseny-hotovo.html` - Aktualizovat na `ce-*` prefixy
- [ ] `detail-kurzu-nezahajeny.html` - Aktualizovat na `ce-*` prefixy
- [ ] `detail-lekce.html` - Aktualizovat na `ld-*` prefixy

#### Profile
- [ ] `muj-profil.html` - Aktualizovat na `pf-*` prefixy

#### Shopping & Checkout
- [ ] `nakupni-kosik.html` - Aktualizovat na `cart-*` prefixy
- [ ] `nakupni-kosik-prazdny.html` - Aktualizovat na `cart-*` prefixy
- [ ] `pokladna.html` - Aktualizovat na `co-*` prefixy
- [ ] `pokladna2.html` - Aktualizovat na `co-*` prefixy

#### Instructor
- [ ] `profil-lektora.html` - Aktualizovat na `ip-*` prefixy

#### Tests
- [ ] `test1.html` - Aktualizovat na `test-*` prefixy
- [ ] `test2.html` - Aktualizovat na `test-*` prefixy
- [ ] `test3.html` - Aktualizovat na `test-*` prefixy
- [ ] `test4.html` - Aktualizovat na `test-*` prefixy
- [ ] `test5.html` - Aktualizovat na `test-*` prefixy
- [ ] `test6.html` - Aktualizovat na `test-*` prefixy
- [ ] `test7.html` - Aktualizovat na `test-*` prefixy
- [ ] `test7-complete.html` - Aktualizovat na `test-*` prefixy
- [ ] `test7-failed.html` - Aktualizovat na `test-*` prefixy
- [ ] `test_vyhodnoceni1.html` - Aktualizovat na `test-*` prefixy
- [ ] `test_vyhodnoceni2.html` - Aktualizovat na `test-*` prefixy
- [ ] `test_vyhodnoceni3.html` - Aktualizovat na `test-*` prefixy
- [ ] `test_vyhodnoceni4.html` - Aktualizovat na `test-*` prefixy
- [ ] `test_vyhodnoceni5.html` - Aktualizovat na `test-*` prefixy

#### Other
- [ ] `kategorie-kurzu.html` - Aktualizovat na `cat-*` prefixy (částečně)
- [ ] `thankYou.html` - Aktualizovat na `ty-*` prefixy

---

### 5.3 JavaScript Checklist

- [ ] Zkontrolovat `js/hamburger.js` - možné reference na `.hamburger`, `.mobile-menu`
- [ ] Zkontrolovat `js/tabs.js` - reference na `.tab`, `.tab-content`
- [ ] Zkontrolovat `js/sidebarTabs.js` - reference na tab třídy
- [ ] Zkontrolovat všechny JS soubory v `js/` složce
- [ ] Vyhledat `querySelector` a `getElementsByClassName` v projektu
- [ ] Aktualizovat event listenery

---

### 5.4 Testovací Checklist

#### Vizuální Testy
- [ ] Homepage - Vzhled OK
- [ ] Course Detail - Vzhled OK
- [ ] Course Enrolled - Vzhled OK
- [ ] Lesson Detail - Vzhled OK
- [ ] Profile - Vzhled OK
- [ ] Shopping Cart - Vzhled OK
- [ ] Checkout - Vzhled OK
- [ ] Instructor Profile - Vzhled OK
- [ ] Test Pages - Vzhled OK

#### Funkční Testy
- [ ] Hamburger menu - Otevírá/zavírá se
- [ ] Desktop menu - Dropdown funguje
- [ ] Search bar - Funguje na všech stránkách
- [ ] Buttons - Hover efekty fungují
- [ ] Footer links - Všechny linky fungují
- [ ] Tabs - Přepínání funguje
- [ ] Modály - Otevírají/zavírají se
- [ ] Forms - Submit funguje
- [ ] Swipery - Scrollují správně

#### Responsive Testy
- [ ] Mobile (320px-767px)
- [ ] Tablet (768px-1023px)
- [ ] Desktop (1024px+)
- [ ] Large Desktop (1600px+)

---

## 6. Odhadovaný čas implementace

| Fáze | Čas | Poznámka |
|------|-----|----------|
| Příprava | 1 hodina | Backup, Git branch, testování |
| CSS HEADER | 2 hodiny | 7 instancí × ~15 min |
| CSS SEARCHBAR | 2 hodiny | 7 instancí × ~15 min |
| CSS MOBILE MENU | 2 hodiny | 7 instancí × ~15 min |
| CSS DESKTOP MENU | 2 hodiny | 7 instancí × ~15 min |
| CSS BUTTONS | 2 hodiny | 7 instancí × ~15 min |
| CSS FOOTER | 4 hodiny | 7 instancí × ~30 min (rozsáhlé) |
| CSS HERO | 3 hodiny | 8 instancí × ~20 min |
| CSS Ostatní | 4 hodiny | Bubbles, Tabs, Sidebar, atd. |
| HTML Úpravy | 8 hodin | ~25 souborů × ~20 min |
| JavaScript | 2 hodiny | Kontrola a úpravy |
| Testování | 6 hodin | Důkladné testování všech stránek |
| Dokumentace | 2 hodiny | Finalizace dokumentace |
| **CELKEM** | **40 hodin** | ~5 pracovních dnů |

---

## 7. Rizika a varování

### ⚠️ VYSOKÁ RIZIKA

1. **Rozsah změn:**
   - 20,776 řádků CSS
   - ~25 HTML souborů
   - Potenciálně všechny JS soubory
   - **Riziko:** Vysoká pravděpodobnost chyb

2. **Cascade efekty:**
   - Změna jedné třídy může ovlivnit více míst
   - Složité selektory typu `.header .navbar .dropdown`
   - **Riziko:** Nefunkční komponenty

3. **JavaScript závislosti:**
   - Event listenery mohou hledat staré třídy
   - **Riziko:** Ztráta interaktivity

4. **Testování:**
   - 25+ HTML stránek × 4 breakpointy = 100+ scénářů
   - **Riziko:** Nenalezené chyby

### ⚠️ STŘEDNÍ RIZIKA

1. **Konzistence:**
   - Snadné udělat překlep v prefix
   - **Mitigace:** Automatizace pomocí skriptů

2. **Údržba:**
   - Duplicitní kód zůstává
   - **Mitigace:** Toto je dočasné řešení před refaktoringem

3. **Onboarding:**
   - Noví vývojáři musí pochopit systém prefixů
   - **Mitigace:** Dobrá dokumentace

---

## 8. Alternativní přístup (DOPORUČENÝ)

### Místo přejmenování → Odstranění duplicit

**Postup:**
1. ✅ Zachovat INDEX verze všech komponent
2. ✅ Odstranit duplicitní sekce z CSS
3. ✅ Všechny HTML stránky použijí stejné třídy
4. ✅ Vytvořit page-specific overrides pouze pro skutečně odlišné styly

**Výhody:**
- ✅ Redukce kódu o ~21% (4,410 řádků)
- ✅ Jednodušší údržba
- ✅ Konzistentní design
- ✅ Žádné změny v HTML (pokud už používají stejné třídy)
- ✅ Rychlejší implementace (1-2 dny vs 5 dnů)

**Nevýhody:**
- ⚠️ Méně flexibility pro page-specific změny
- ⚠️ Nutnost ověřit, že všechny stránky používají stejné názvy tříd

---

## 9. Doporučení

### Pro implementaci přejmenování:
1. **Začít s jednou komponentou** (např. HEADER)
2. **Vytvořit automatizační skript** pro nahrazování
3. **Testovat po každé komponentě**
4. **Používat Git commits** po každé úspěšné změně

### Pro implementaci odstranění duplicit:
1. **Začít s nejjednodušší komponentou** (např. BUBBLES)
2. **Ověřit funkčnost** na všech stránkách
3. **Postupovat od nejmenších k největším** komponentám
4. **Vytvořit utility třídy** pro specifické případy

---

## 10. Závěr

Tento dokument poskytuje **kompletní plán** pro přejmenování duplicitních CSS tříd podle sekcí. 

**Doporučení:**
- ⚠️ **Zvážit alternativní přístup** (odstranění duplicit)
- ✅ **Pokud pokračovat s přejmenováním:** Postupovat systematicky podle tohoto plánu
- ✅ **Používat automatizaci** kde je to možné
- ✅ **Důkladně testovat** po každé změně

**Další kroky:**
1. Rozhodnout mezi přejmenováním vs. odstraněním duplicit
2. Vytvořit Git branch
3. Začít s pilotní implementací (1 komponenta)
4. Vyhodnotit výsledky
5. Pokračovat nebo pivotovat

---

**Dokument připraven:** 14. listopadu 2025  
**Verze:** 1.0  
**Status:** Návrh k revizi
