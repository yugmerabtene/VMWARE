# Module 5 : Gestion du Stockage

> **Auteur :** yugmerabtene
> **Version :** 2.0
> **Durée estimée :** 4 heures

---

## Description

Ce module traite de la gestion du stockage dans vSphere. Vous découvrirez les différents types de datastores (VMFS, NFS, iSCSI, vSAN), leur configuration et leurs cas d'usage respectifs pour optimiser le stockage de vos machines virtuelles.

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Configurer un datastore VMFS
2. Monter un datastore NFS
3. Configurer le stockage iSCSI
4. Comprendre et déployer vSAN

---

## Prérequis

- vCenter Server opérationnel (Module 3)
- Au moins un hôte ESXi
- Stockage disponible (SAN, NAS ou disques locaux)

---

## Contenu théorique

### 1. Types de stockage vSphere

| Type | Protocole | Usage |
|------|-----------|-------|
| VMFS | Bloc (FC, iSCSI, local) | Datastores VMware natifs |
| NFS | Fichier (NFS v3/v4.1) | Partage réseau simple |
| vSAN | Objet | Stockage distribué hyperconvergé |
| vVols | Objet | Stockage défini par logiciel |

### 2. VMFS (Virtual Machine File System)

Système de fichiers optimisé pour les VM.

**Caractéristiques :**
- Supporte jusqu'à 64 TB par datastore
- Multi-accès (plusieurs hôtes simultanément)
- Supporte les snapshots et clones

### 3. Comparaison des protocoles de stockage

| Critère | Fibre Channel | iSCSI | NFS |
|---------|---------------|-------|-----|
| Performance | Très haute | Haute | Moyenne |
| Coût | Élevé | Faible | Faible |
| Complexité | Élevée | Moyenne | Faible |
| Distance | Limitée | Illimitée | Illimitée |

---

## Travaux pratiques

### TP 1 : Création d'un datastore VMFS local

**Objectif :** Créer un datastore sur un disque local.

**Étapes :**
1. Se connecter à l'hôte ESXi via vCenter
2. Onglet "Storage" → "Datastores"
3. Cliquer sur "New datastore"
4. Type : "VMFS"
5. Sélectionner le disque local disponible
6. Nommer : `datastore-local-01`
7. Version VMFS : 6 (recommandé)
8. Taille : utiliser tout l'espace disponible
9. Terminer l'assistant

**Critères de réussite :**
- [ ] Le datastore est créé et monté
- [ ] L'espace est visible dans "Capacity"

### TP 2 : Configuration d'un datastore NFS

**Objectif :** Monter un partage NFS comme datastore.

**Étapes :**
1. Onglet "Storage" → "Datastores"
2. Cliquer sur "New datastore"
3. Type : "NFS"
4. Version : NFS 3
5. Configurer :
   - Nom : `datastore-nfs-01`
   - Serveur : `nas.lab.local`
   - Dossier : `/exports/vmware`
6. Terminer l'assistant

**Critères de réussite :**
- [ ] Le datastore NFS est monté
- [ ] Les VM peuvent écrire sur le datastore

### TP 3 : Configuration iSCSI logiciel

**Objectif :** Configurer un adaptateur iSCSI logiciel.

**Étapes :**
1. Onglet "Configure" → "Storage adapters"
2. Cliquer sur "Add software adapter"
3. Sélectionner "Add software iSCSI adapter"
4. Configurer l'adaptateur :
   - Activer l'adaptateur
   - Ajouter les cibles iSCSI :
     - Adresse : `san.lab.local`
     - iQN : `iqn.2024-01.lab:san.target01`
5. Configurer le réseau iSCSI :
   - Créer un port group dédié
   - Assigner un VMkernel adapter
6. Rescan pour découvrir les LUN

**Critères de réussite :**
- [ ] L'adaptateur iSCSI est actif
- [ ] Les LUN sont découvertes et accessibles

### TP 4 : Introduction à vSAN

**Objectif :** Comprendre les bases de vSAN.

**Prérequis vSAN :**
- Minimum 3 hôtes ESXi
- Chaque hôte : 1 disque cache (SSD) + 1 disque capacité
- Réseau dédié 10 GbE

**Étapes de configuration :**
1. Créer un cluster et activer vSAN
2. Ajouter les hôtes au cluster
3. Configurer les disques :
   - SSD → tier cache
   - HDD/SSD → tier capacité
4. Créer une storage policy

**Critères de réussite :**
- [ ] vSAN est activé sur le cluster
- [ ] Le datastore vSAN est créé

---

## Résumé

- VMFS = système de fichiers natif VMware
- NFS = stockage fichier simple à configurer
- iSCSI = stockage bloc sur IP
- vSAN = stockage hyperconvergé distribué

---

## Ressources complémentaires

- [Guide stockage vSphere](https://docs.vmware.com/en/VMware-vSphere/7.0/vsphere-storage.pdf)
- [vSAN design guide](https://core.vmware.com/vsan-design-guide)

---

## Évaluation

- Quiz sur les types de stockage
- Exercice pratique : configuration d'un datastore VMFS et NFS
