# dolips5 – KytyPS5 build pro testování Demon's Souls

Tahle větev neobsahuje zdrojáky emulátoru, jen GitHub Actions workflow
(`.github/workflows/build-kytyps5.yml`). Ten na Windows runneru postaví dvě varianty
z připnutých commitů, abys je mohl porovnat:

| Artifact | Zdroj | Build | Poznámka |
|---|---|---|---|
| `KytyPS5-U59-PGO-Windows-x64` | [Jetsku/KytyPS5](https://github.com/Jetsku/KytyPS5) `main` @ `28bc20f` | clang-cl 22.1.3, Release, LTO, **PGO** | Výkonnostní fork: U59 renderer, Demon's Souls shader/kompatibilitní změny, práce na command procesoru a VRAM. PGO profil je natrénovaný na Astro Bot (Sky Garden), ne na DeS. Neoficiální fork třetí strany. |
| `KytyPS5-official-Windows-x64` | [KytyPS5/KytyPS5](https://github.com/KytyPS5/KytyPS5) `main` @ `9e41d83` | clang-cl, Release, LTO | Oficiální upstream, nejnovější shader fixy. Ostatní větve repa jsou 70–93 commitů pozadu. |

## Jak získat exe

1. Otevři záložku **Actions**, workflow „Build KytyPS5 for Demon's Souls testing“, poslední běh.
2. Dole v **Artifacts** stáhni oba zipy a rozbal je do **dvou různých složek**.
3. Spusť `launcher.exe`.

Jiné commity postavíš přes **Run workflow** (`workflow_dispatch`) a vyplnění `jetsku_ref` / `official_ref`.

## Jak je férově srovnat

- Testuj na stejném místě ve hře (třeba Nexus a začátek 1-1) a se stejným rozlišením a nastavením.
- První spuštění skoro vždy laguje, protože se kompilují shadery. Měř až při **druhém** průchodu.
- FPS ukazuje titulek okna. Sleduj průměr i propady a zaznamenej pády nebo grafické chyby.
- U PGO buildu je v balíčku `u59-preset.json` (výchozí `KYTY_*` volby forku) a `U59-README.md`
  se známými problémy. Na AMD GPU fork doporučuje nechat zapnuté patch mody.

Hru si musíš legálně dumpnout ze svého PS5. Emulátor žádné hry ani systémový software
neobsahuje. Obě varianty jsou pod licencí GPL-2.0 (viz `LICENSE` v artifactu).
