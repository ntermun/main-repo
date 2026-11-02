# ntermun/main-repo

Артефакты pacman-репозитория **ntermun** для `aarch64` (статические
бинари, собранные `aarch64-linux-musl`).

* Пакеты, `ntermun.db.tar.gz`, `ntermun.files.tar.gz` и симлинки —
  ветка **`gh-pages`**, каталог `aarch64/`.
* Публичный URL (GitHub Pages):
  <https://ntermun.github.io/main-repo/aarch64>
* Инфраструктура сборки, PKGBUILD-шаблоны и CI:
  <https://github.com/ntermun/packages>
* Исходники терминала: <https://github.com/ntermun/ntermun>

Ветка `gh-pages` генерируется workflow из `ntermun/packages`
(`makepkg.sh` → `mkrepo.sh` → `rsync` в `aarch64/`). Вручную её лучше
не править: следующая сборка перезапишет содержимое `aarch64/`.

## Состав

| пакет | назначение |
|---|---|
| `zlib` `bzip2` `xz` `zstd` | библиотеки и утилиты сжатия |
| `openssl` | `openssl`, libcrypto/libssl (статические) |
| `sqlite` | `sqlite3`, libsqlite3 (база libalpm) |
| `ncurses` | libncursesw, terminfo |
| `libarchive` `curl` | зависимости libalpm |
| `pacman` | `pacman`, `repo-add`, `makepkg` |
| `bash` `coreutils` `grep` `sed` `gawk` `tar` `gzip` `findutils` `diffutils` `make` | GNU userland |
| `openssh` | клиент ssh/scp/sftp/ssh-keygen |
| `openssh-server` | `sshd` + `sshd-session`/`sshd-sftp` |

## Подключение

`pacman.conf` лежит в `<files>/etc/pacman.conf` (приходит с пакетом
`pacman`):

```ini
[options]
Architecture = aarch64
SigLevel = Never

[ntermun]
Server = https://ntermun.github.io/main-repo/aarch64
```

Корень pacman — каталог приложения:

```sh
PREFIX=/data/data/nnn.ntermun/files
$PREFIX/usr/bin/pacman --root "$PREFIX" -Sy
$PREFIX/usr/bin/pacman --root "$PREFIX" -S bash coreutils grep sed gawk \
    tar gzip findutils diffutils make openssl openssh openssh-server pacman
```

## Установка пакетов вручную (без pacman)

```sh
curl -fLO https://ntermun.github.io/main-repo/aarch64/bash-5.3-1-aarch64.pkg.tar.zst
tar --zstd -xf bash-5.3-1-aarch64.pkg.tar.zst -C /data/data/nnn.ntermun/files
```
