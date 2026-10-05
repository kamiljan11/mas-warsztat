# RUNBOOK — mas-warsztat (publiczne repo referencyjne)

Ten plik opisuje WYLACZNIE to repo. Repo jest publiczne i nie zawiera kodu aplikacji, wiec nie ma tu procedur operacyjnych aplikacji (hosty, funkcje, konfiguracja). Te trzymamy w prywatnym repo aplikacji.

## Podstawy
- Co to jest: strona referencyjna (README + licencja) opisujaca system MAS Warsztat, bez kodu.
- Widocznosc repo: publiczne (sprawdzone `gh repo view`, 2026-10-05).
- Zywa aplikacja: https://app.garage.mountaincar.is (adres juz publiczny w README).
- Prywatne repo aplikacji: [DO UZUPELNIENIA przez Kamila: nazwa prywatnego repo z kodem aplikacji — nie wpisujemy jej tu automatycznie]
- Wlasciciel: Kamil Jan (MAS Group).

## Deploy
- Tego repo nie deployuje sie nigdzie. Zmiana = merge do `main` i GitHub pokazuje nowy README.
- Aplikacja: procedura deployu jest w runbooku prywatnego repo aplikacji. [DO UZUPELNIENIA przez Kamila: potwierdzic, ze tam istnieje aktualny docs/RUNBOOK.md]

## Rollback
```bash
git revert <sha-zlego-commita> && git push   # tylko dla zmian w tym repo (dokumenty)
```

## Sekrety
- W tym repo: zero sekretow i zero zmiennych srodowiskowych.
- Sekrety aplikacji: nie sa tu opisywane. [DO UZUPELNIENIA przez Kamila: wskazac, gdzie jest ich spis (nazwy + miejsce przechowywania) w dokumentacji prywatnej]

## Typowe awarie
| Objaw | Pierwszy krok |
|---|---|
| README na GitHubie wyglada zle | Podglad Markdown w PR przed merge; popraw skladnie i wypchnij |
| Ktos pyta o kod lub dostep | Kod jest prywatny i nie jest tu publikowany — odeslij do wlasciciela |
| Trzeba zmienic opis w README | Edytuj README.md i dodaj wpis do CHANGELOG.md; nie dopisuj tu danych klientow, hostow ani szczegolow konfiguracji bezpieczenstwa |

## Zasady dla tego repo (bo jest publiczne)
- Nie wpisuj: nazw klientow, danych osobowych, adresow mailowych, wewnetrznych hostow i IP, sekretow, opisow podatnosci.
- Opisy bezpieczenstwa w README zostaja ogolne (model izolacji), bez konkretow wykorzystania.

## Kontakty
- Wlasciciel: Kamil Jan. [DO UZUPELNIENIA przez Kamila: preferowany kanal kontaktu dla przejmujacego]
