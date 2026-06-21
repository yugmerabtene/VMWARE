# Module 1 : Introduction à la Virtualisation

> **Auteur :** yugmerabtene
> **Version :** 2.0
> **Durée estimée :** 4 heures

---

## Description

Ce module pose les fondations de la virtualisation. Vous découvrirez les concepts clés, les différents types d'hyperviseurs et leur fonctionnement. Une introduction pratique vous permettra d'installer un hyperviseur de type 2 et de créer vos premières machines virtuelles.

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Définir la virtualisation et identifier ses avantages
2. Distinguer les hyperviseurs de type 1 (bare-metal) et type 2 (hébergé)
3. Identifier les couches d'une infrastructure virtualisée
4. Installer un hyperviseur de type 2 et créer une machine virtuelle

---

## Prérequis

- Connaissances de base en informatique
- Un poste de travail avec 8 Go de RAM minimum
- Une image ISO d'un système Linux (Ubuntu Server recommandé)

---

## Contenu théorique

### 1. Définition de la virtualisation

La virtualisation est une technologie qui permet de créer plusieurs environnements informatiques isolés (machines virtuelles) à partir d'une seule machine physique.

**Avantages principaux :**
- Optimisation des ressources matérielles
- Isolation des environnements
- Réduction des coûts matériels et énergétiques
- Flexibilité et mobilité des charges de travail

### 2. Types d'hyperviseurs

| Caractéristique | Type 1 (Bare-Metal) | Type 2 (Hébergé) |
|-----------------|---------------------|------------------|
| Installation | Directement sur le matériel | Sur un OS hôte |
| Performance | Optimale | Dépend de l'hôte |
| Usage | Production | Développement/Tests |
| Exemples | ESXi, Hyper-V, Xen | Workstation, VirtualBox, Parallels |

### 3. Couches de l'infrastructure virtualisée

```
┌─────────────────────────────────────┐
│  Couche d'administration (vCenter)  │
├─────────────────────────────────────┤
│  Machines Virtuelles (OS + Apps)    │
├─────────────────────────────────────┤
│  Hyperviseur (ESXi/Workstation)     │
├─────────────────────────────────────┤
│  Matériel physique (CPU/RAM/Storage)│
└─────────────────────────────────────┘
```

---

## Travaux pratiques

### TP 1 : Installation de VMware Workstation

**Objectif :** Installer un hyperviseur de type 2 sur votre poste de travail.

**Étapes :**
1. Télécharger VMware Workstation depuis le site officiel
2. Lancer l'installation avec les droits administrateur
3. Accepter les conditions d'utilisation
4. Choisir le type d'installation (Typical)
5. Terminer l'installation et redémarrer si nécessaire

**Critères de réussite :**
- [ ] VMware Workstation se lance sans erreur
- [ ] La licence est activée (essai gratuit ou licence)

### TP 2 : Création d'une machine virtuelle

**Objectif :** Créer et configurer une VM Linux.

**Étapes :**
1. Dans Workstation, cliquer sur "Create a New Virtual Machine"
2. Sélectionner "Custom (advanced)"
3. Configurer les ressources :
   - RAM : 2 Go minimum
   - CPU : 1 processeur
   - Disque : 20 Go
4. Sélectionner l'ISO Linux
5. Démarrer la VM et installer l'OS

**Critères de réussite :**
- [ ] La VM démarre correctement
- [ ] L'OS est installé et fonctionnel
- [ ] La VM a accès au réseau

### TP 3 : Configuration réseau

**Objectif :** Comprendre les modes réseau d'une VM.

**Modes à tester :**
1. **NAT** : La VM partage l'IP de l'hôte
2. **Bridged** : La VM obtient sa propre IP sur le réseau physique
3. **Host-Only** : La VM communique uniquement avec l'hôte

**Critères de réussite :**
- [ ] Identifier le mode réseau actuel
- [ ] Changer de mode et vérifier la connectivité

---

## Résumé

- La virtualisation permet de créer plusieurs environnements isolés sur un même matériel
- Les hyperviseurs de type 1 (bare-metal) sont pour la production
- Les hyperviseurs de type 2 (hébergés) sont pour le développement/tests
- L'infrastructure comprend 4 couches : matériel, hyperviseur, VM, administration

---

## Ressources complémentaires

- [Documentation VMware Workstation](https://docs.vmware.com/en/VMware-Workstation-Pro/)
- [Virtualisation : concepts de base](https://www.vmware.com/topics/glossary/content/virtualization)

---

## Évaluation

- Quiz de 10 questions sur les concepts de virtualisation
- Exercice pratique : créer 2 VMs et configurer leur réseau
