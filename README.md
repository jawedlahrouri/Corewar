# ⚔️ Corewar — Virtual Machine & Bytecode Arena

[![Academic Year](https://img.shields.io/badge/Epitech-Tek1-blue?style=for-the-badge&logo=epitech&logoColor=white)](https://www.epitech.eu/)
[![Module](https://img.shields.io/badge/Module-B--CPE--200-informational?style=for-the-badge)](#)
[![Language](https://img.shields.io/badge/Language-C-00599C?style=for-the-badge&logo=c&logoColor=white)](#)

## 📘 Description
**Corewar** est l'un des projets emblématiques d'Epitech inspiré du jeu de programmation de D. G. Jones et A. K. Dewdney. Deux à quatre programmes champions s'affrontent au sein d'une machine virtuelle dotée d'une mémoire circulaire de 6 Ko (arène). Le but ultime est de survivre en exécutant périodiquement l'instruction `live` tout en altérant le code des champions adverses.

## ⚙️ Architecture
- **Assembleur (`asm`)** : Analyseur lexical et syntaxique traduisant le code source assembleur (`.s`) en bytecode exécutable (`.cor`) avec calcul des offsets d'adresses et gestion des labels.
- **Machine Virtuelle (`corewar`)** :
  - Simulation de l'arène circulaire de `MEM_SIZE` octets.
  - Ordonnancement des processus et cycles d'exécution (`CYCLE_TO_DIE`).
  - Décodage des 16 instructions standards (registres, direct, indirect, codage octet `CB`).

## 🔨 Compilation & Utilisation
```bash
make
./corewar/corewar champion1.cor champion2.cor
```
