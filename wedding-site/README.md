# Zosia & Kuba — Strona weselna 💙

Prosta, elegancka strona weselna w kolorach błękitno-białych z systemem RSVP i plikami iCal.

## Struktura plików

```
/
├── index.html        ← cała strona (HTML + CSS + JS w jednym pliku)
├── ics/
│   ├── ceremony.ics  ← Ceremonia ślubna (28.08, 16:00)
│   ├── party.ics     ← Przyjęcie weselne (28.08, ~18:00)
│   ├── poprawiny.ics ← Poprawiny (29.08, 13:00)
│   └── all.ics       ← Wszystkie trzy wydarzenia razem
└── README.md
```

## Jak uruchomić na GitHub Pages

1. Utwórz nowe repo na GitHubie (np. `zosia-kuba-wesele`)
2. Wrzuć wszystkie pliki:
   ```bash
   git init
   git add .
   git commit -m "Strona weselna"
   git branch -M main
   git remote add origin https://github.com/TWOJ_LOGIN/NAZWA_REPO.git
   git push -u origin main
   ```
3. W ustawieniach repo → **Settings → Pages → Source: main / root**
4. Strona będzie dostępna pod adresem:
   `https://TWOJ_LOGIN.github.io/NAZWA_REPO/`

Pliki `.ics` będą dostępne np. pod:
`https://TWOJ_LOGIN.github.io/NAZWA_REPO/ics/ceremony.ics`

## Co można łatwo zmienić w `index.html`

### Dane
| Co | Gdzie szukać w pliku |
|---|---|
| Imiona pary | `<h1>` w sekcji hero |
| Data i miejsce | `hero-date`, countdown (`new Date('2027-08-28T16:00:00')`) |
| Adresy kościoła i hotelu | sekcja `lokalizacje`, linki Google Maps |
| Termin RSVP | tekst `23 lipca 2027` + badge z zegarem |
| Godziny planu dnia | klasy `.tl-time` w sekcji `plan` |

### Kolory (CSS variables u góry pliku)
```css
--sky:       #deeaf5   /* jasny błękit tła */
--blue:      #5b8eb5   /* akcent niebieski */
--navy:      #1a3a52   /* ciemny granat */
--beige:     #f5efe6   /* ciepły beż */
```

### Zdjęcia
Zastąp bloki `.photo-ph` zwykłymi tagami `<img>`:
```html
<img src="zdjecia/nasze1.jpg" alt="Zosia i Kuba" style="width:100%;height:100%;object-fit:cover">
```

## System RSVP

Dane gości przechowywane są w `localStorage` przeglądarki gościa — każda osoba widzi swoją odpowiedź i listę wszystkich potwierdzonych.

**Ograniczenie:** Ty jako gospodarz nie widzisz listy z innego urządzenia.  
**Rozwiązanie:** Podlinkuj zamiast tego Google Forms lub Airtable Form — wystarczy zamienić `<form id="rsvpForm">` na przycisk/link do zewnętrznego formularza.

## Pliki iCal

Pliki `.ics` działają na wszystkich platformach:
- **iOS** — otwiera się bezpośrednio w Kalendarzu Apple
- **Android** — otwiera się w Google Calendar
- **Desktop** — pobiera plik do zaimportowania

Jeśli zmienisz daty/godziny, zaktualizuj też pliki w folderze `ics/` (format `YYYYMMDDTHHMMSSZ` w UTC).
