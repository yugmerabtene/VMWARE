# Module 2 : Installation et Configuration d'ESXi

> **Auteur :** yugmerabtene
> **Version :** 2.0
> **Durée estimée :** 4 heures

---

## Description

Ce module vous guide dans l'installation et la configuration initiale d'ESXi, l'hyperviseur bare-metal de VMware. Vous apprendrez à préparer le matériel, installer l'hyperviseur, configurer le réseau de base et accéder à l'interface de gestion.

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Préparer un serveur pour l'installation d'ESXi
2. Installer ESXi sur un serveur physique
3. Configurer les paramètres réseau de base via DCUI
4. Accéder à l'interface de gestion web (Host Client)

---

## Prérequis

- Serveur physique compatible ESXi (voir [HCL VMware](https://www.vmware.com/resources/compatibility/search.php))
- Image ISO d'ESXi (téléchargeable depuis le portail VMware)
- Clé USB bootable ou accès iLO/iDRAC/IPMI
- Adresse IP statique réservée pour l'hôte

---

## Contenu théorique

### 1. Matériel requis pour ESXi

| Composant | Minimum | Recommandé |
|-----------|---------|------------|
| CPU | 2 cœurs x86-64 | 4+ cœurs |
| RAM | 4 Go | 16+ Go |
| Stockage | 8 Go (boot) | SSD dédié |
| Réseau | 1 GbE | 10 GbE |

### 2. Architecture ESXi

ESXi est un hyperviseur de type 1 (bare-metal) qui s'installe directement sur le matériel.

```
┌─────────────────────────────────────┐
│      Machines Virtuelles            │
├─────────────────────────────────────┤
│      ESXi Kernel (vmkernel)         │
├─────────────────────────────────────┤
│      Matériel physique              │
└─────────────────────────────────────┘
```

**Composants clés :**
- **vmkernel** : Noyau optimisé pour la virtualisation
- **VMFS** : Système de fichiers pour les datastores
- **vSwitch** : Commutateur virtuel intégré

### 3. DCUI (Direct Console User Interface)

Interface locale accessible physiquement sur le serveur pour :
- Configurer le réseau
- Réinitialiser les mots de passe
- Activer/désactiver Shell et SSH
- Voir les logs

---

## Travaux pratiques

### TP 1 : Préparation du support d'installation

**Objectif :** Créer une clé USB bootable avec ESXi.

**Étapes :**
1. Télécharger l'ISO d'ESXi depuis le portail VMware
2. Utiliser Rufus (Windows) ou dd (Linux) pour créer la clé bootable
   - Linux : `dd if=VMware-ESXi.iso of=/dev/sdX bs=4M status=progress`
3. Vérifier que le serveur peut démarrer sur USB

**Critères de réussite :**
- [ ] La clé USB est créée correctement
- [ ] Le serveur démarre sur l'installateur ESXi

### TP 2 : Installation d'ESXi

**Objectif :** Installer ESXi sur le serveur physique.

**Étapes :**
1. Démarrer le serveur sur la clé USB
2. Attendre le chargement de l'installateur (écran jaune/gris)
3. Appuyer sur Entrée pour continuer
4. Accepter le contrat de licence (F11)
5. Sélectionner le disque d'installation
6. Configurer la disposition du clavier (US par défaut)
7. Définir le mot de passe root
8. Confirmer l'installation (F11)
9. Retirer la clé USB et redémarrer

**Critères de réussite :**
- [ ] ESXi démarre et affiche l'écran DCUI
- [ ] L'adresse IP est affichée à l'écran

### TP 3 : Configuration réseau via DCUI

**Objectif :** Configurer l'adresse IP et le réseau.

**Étapes :**
1. Appuyer sur F2 pour accéder à la configuration
2. S'authentifier avec root et le mot de passe
3. Aller dans "Configure Management Network"
4. Configurer :
   - **Network Adapters** : Sélectionner la carte réseau
   - **IPv4 Configuration** : IP statique, masque, passerelle
   - **DNS Configuration** : Serveurs DNS
5. Appliquer et redémarrer le réseau (Y)

**Critères de réussite :**
- [ ] L'adresse IP est configurée
- [ ] Le serveur est accessible depuis le réseau

### TP 4 : Accès à l'interface web (Host Client)

**Objectif :** Accéder à la gestion web d'ESXi.

**Étapes :**
1. Ouvrir un navigateur sur un poste du réseau
2. Accéder à `https://<IP-ESXi>`
3. Accepter le certificat auto-signé
4. S'authentifier avec root / mot de passe
5. Explorer l'interface

**Critères de réussite :**
- [ ] L'interface web est accessible
- [ ] Vous pouvez vous authentifier

---

## Résumé

- ESXi s'installe directement sur le matériel (bare-metal)
- Le DCUI permet la configuration locale (réseau, mot de passe)
- L'interface web (Host Client) permet la gestion à distance
- Toujours utiliser une IP statique pour ESXi

---

## Ressources complémentaires

- [Guide d'installation ESXi](https://docs.vmware.com/en/VMware-vSphere/7.0/vsphere-esxi-vcenter-server-70-installation-guide.pdf)
- [Hardware Compatibility List](https://www.vmware.com/resources/compatibility/search.php)

---

## Évaluation

- Quiz sur les prérequis matériels
- Exercice pratique : installation complète d'ESXi sur serveur physique ou virtuel (nested)
