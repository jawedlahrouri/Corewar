[![Academic Year](https://img.shields.io/badge/Epitech-Tek1-blue?style=for-the-badge&logo=epitech&logoColor=white)](https://www.epitech.eu/)
[![Language: C](https://img.shields.io/badge/Language-C-00599C.svg?style=for-the-badge&logo=c)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Module](https://img.shields.io/badge/Module-B--CPE--200-informational?style=for-the-badge)](#)

# ⚔️ Corewar — Machine Virtuelle & Arène de Combat de Bytecode

**Corewar** est une machine virtuelle en C dans laquelle s'affrontent simultanément de 1 à 4 programmes compilés ("champions"). Les processus partagent un espace d'adressage circulaire en mémoire vive (6144 octets / `MEM_SIZE`) et exécutent du bytecode d'instructions machine jusqu'à ce qu'un seul champion survive.

---

## ⚙️ Mécaniques de la Machine Virtuelle

- **Arène Circulaire (`MEM_SIZE = 6144`)** : Espace mémoire continu où chaque adresse s'enroule modulo `MEM_SIZE`. Les champions sont chargés à des adresses espacées de manière équidistante ou spécifiées via l'option `-a`.
- **Processus & Registres** : Chaque processus possède son propre compteur de programme (PC), son indicateur de retenue (*Carry*), et 16 registres de données (`REG_NUMBER = 16`).
- **Jeu de 16 Instructions Bytecode** :
  - `live` (10 cycles) : Proclame que le joueur est en vie.
  - `ld`, `lld` : Charge une valeur depuis la mémoire dans un registre.
  - `st` : Stocke un registre en mémoire.
  - `add`, `sub` : Opérations arithmétiques sur registres.
  - `and`, `or`, `xor` : Opérations logiques bit-à-bit.
  - `zjmp` : Saut conditionnel si le drapeau Carry est actif.
  - `ldi`, `lldi`, `sti` : Adressage indirect indexé.
  - `fork`, `lfork` : Duplication d'un processus combattant.
  - `aff` : Affiche un caractère sur la sortie standard.
- **Cycle de Vie & Arbitrage** :
  - Le temps s'écoule par cycles.
  - Après chaque période `CYCLE_TO_DIE`, tout processus n'ayant pas exécuté au moins un `live` est tué.
  - Si un certain nombre de `live` cumulés (`NBR_LIVE = 40`) est atteint, `CYCLE_TO_DIE` diminue de `CYCLE_DELTA = 5`.
  - Le dernier joueur ayant proclamé `live` remporte la partie.

---

## 💻 Options de Lancement

```bash
./corewar [-dump nbr_cycle] [[-n prog_number] [-a load_address] prog_name.cor] ...
```

- `-dump <nbr_cycle>` : Vide la mémoire de l'arène en hexadécimal (32 octets par ligne) au cycle spécifié et interrompt la partie.
- `-n <prog_number>` : Attribue un numéro de joueur explicite au champion.
- `-a <load_address>` : Force l'adresse mémoire de chargement du champion.

---

## 🛠️ Compilation

```bash
make        # Génère le binaire 'corewar'
make clean  # Supprime les fichiers objets
make fclean # Supprime les fichiers objets et l'exécutable
make re     # Recompile l'ensemble
```
