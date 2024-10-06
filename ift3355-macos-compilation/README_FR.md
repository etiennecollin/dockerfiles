# IFT3355 macOS Compiler

[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/etiennecollin/dockerfiles/blob/main/ift3355-macos-compilation/README.md)

Si vous utilisez macOS, vous allez de rencontrer un problème de _linking_ lors de la compilation du TP, et ce, même si l'exécutable est généré. Ça risque de vous causer des problèmes plus tard dans le TP.

Pour éviter cela, j'ai créé une image Docker qui permet de compiler le code correctement. Il vous suffit de cloner ce repo et de suivre les instructions. Pas de stress, c'est littéralement une commande dans le terminal. Tout est géré par un script!

N'hésitez pas à me faire signe si vous rencontrez des problèmes. De mon côté, tout fonctionne bien sur mon MacBook Pro M1.

## Instructions

1. Installer [Docker Desktop](https://www.docker.com/products/docker-desktop/) (ou simplement s'assurer que docker fonctionne sur votre ordinateur).
2. Placer tous les fichiers contenus dans le directory `./to-install` à la racine du TP2 (dans le même directory que `CMakeLists.txt`).
   - Remplacer le fichier `CMakeLists.txt` si l'ordinateur le demande.
   - Le fichier `CMakeLists.txt` ne contient qu'une addition: la ligne `set(CMAKE_TOOLCHAIN_FILE "${CMAKE_CURRENT_SOURCE_DIR}/toolchain.cmake")` est ajoutée au dessus de la ligne `project(...)` afin d'importer le fichier `toolchain.cmake`.
3. Maintenant, pour compiler le projet, exécuter: `docker compose run ift3355 ./build.sh` à partir de la racine du TP2.

Il est possible de créer un **alias** de cette longue commande. Pour cela, ajouter la ligne suivante aux fichiers `~/.bashrc` et/ou `~/.zshrc`:

```bash
alias ift3355="docker compose run ift3355 ./build.sh"
```

Après avoir redémarré votre terminal, vous pourrez simplement utiliser la commande `ift3355` à partir de la racine du TP2 pour compiler votre code.
