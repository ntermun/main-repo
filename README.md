# ntermun/main-repo

Артефакты pacman-репозитория **nterminal** для `aarch64` (статические
бинари, собранные `aarch64-linux-musl`).

* Пакеты, `nterminal.db.tar.gz`, `nterminal.files.tar.gz` и симлинки —
  ветка **`gh-pages`**, каталог `aarch64/`.
* Публичный URL (GitHub Pages):
  <https://ntermun.github.io/main-repo/aarch64>
* Инфраструктура сборки, PKGBUILD-шаблоны и CI:
  <https://github.com/ntermun/packages>

Ветка `gh-pages` генерируется workflow из `ntermun/packages`
(`ci-build.sh` → `mkrepo.sh` → `rsync` в `aarch64/`). Вручную её лучше
не править: следующая сборка перезапишет содержимое `aarch64/`.

## Подключение

```ini
[options]
Architecture = aarch64
SigLevel = Never

[nterminal]
Server = https://ntermun.github.io/main-repo/aarch64
```

```sh
pacman -Sy
pacman -S bash coreutils grep sed gawk tar gzip findutils diffutils make openssl openssh
```
