# dolips5 – KytyPS5 build pro testování Demon's Souls

Tahle větev neobsahuje zdrojáky emulátoru, jen GitHub Actions workflow
(`.github/workflows/build-kytyps5.yml`). Ten na Windows runneru postaví
[KytyPS5/KytyPS5](https://github.com/KytyPS5/KytyPS5) `main` @ `9e41d83` stejným postupem jako
oficiální CI (clang-cl, Release, LTO).

Proč `main`: ostatní větve repa (`add-self-updater`, `fix-windows-compilation-2`) jsou staré
feature větve, 70–93 commitů za `main`. Nejnovější shader a renderer fixy, a tím i nejvyšší
výkon v Demon's Souls, jsou v `main`.

## Jak získat exe

1. Otevři záložku **Actions**, workflow „Build KytyPS5 for Demon's Souls testing“, poslední běh.
2. Dole v **Artifacts** stáhni `KytyPS5-official-Windows-x64` a rozbal ho.
3. Spusť `launcher.exe`.

Jiný commit postavíš přes **Run workflow** (`workflow_dispatch`) a vyplnění `official_ref`.

Hru si musíš legálně dumpnout ze svého PS5. Emulátor žádné hry ani systémový software
neobsahuje. KytyPS5 je pod licencí GPL-2.0 (viz `LICENSE` v artifactu).
