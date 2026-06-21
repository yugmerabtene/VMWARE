# Module 3 : Déploiement de vCenter Server

> **Auteur :** yugmerabtene
> **Contact :** yug.merabtene@gmail.com
> **Version :** 2.0
> **Durée estimée :** 4 heures

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Décrire le rôle de vCenter dans une infrastructure vSphere
2. Déployer vCenter Server Appliance (VCSA)
3. Ajouter des hôtes ESXi à vCenter
4. Créer des datacenters, clusters et dossiers

---

## Prérequis

- Au moins un hôte ESXi installé et configuré (Module 2)
- Serveur Windows ou appliance Linux pour VCSA
- Adresse IP statique pour vCenter
- Serveur DNS fonctionnel (requis pour VCSA)

---

## Contenu théorique

### 1. Rôle de vCenter Server

vCenter est l'outil de gestion centralisée de l'infrastructure vSphere.

**Fonctionnalités principales :**
- Gestion centralisée de plusieurs hôtes ESXi
- Fonctionnalités avancées : vMotion, HA, DRS
- Gestion des rôles et permissions
- Templates et déploiement automatisé

### 2. Éditions de vCenter

| Édition | Usage |
|---------|-------|
| vCenter Standard | Jusqu'à 1000 hôtes, 15000 VM |
| vCenter Foundation | Jusqu'à 3 hôtes (petites infrastructures) |

### 3. Architecture VCSA

VCSA est une appliance Linux basée sur Photon OS qui inclut :
- **vpxd** : Service principal vCenter
- **PostgreSQL** : Base de données
- **STS** : Service de tokens de sécurité
- **Web Client** : Interface HTML5

---

## Travaux pratiques

### TP 1 : Préparation de l'environnement

**Objectif :** Préparer les prérequis pour VCSA.

**Étapes :**
1. Créer une entrée DNS pour vCenter :
   ```
   vcenter.lab.local  IN  A  192.168.1.10
   ```
2. Vérifier la résolution DNS depuis le poste d'administration
3. Télécharger l'ISO de vCenter depuis le portail VMware
4. Monter l'ISO et localiser l'installateur VCSA

**Critères de réussite :**
- [ ] Le DNS résout correctement le nom de vCenter
- [ ] L'ISO est téléchargé et monté

### TP 2 : Déploiement de VCSA

**Objectif :** Déployer vCenter Server Appliance.

**Étapes :**
1. Lancer l'installateur VCSA (Stage 1)
2. Sélectionner "Deploy a new vCenter Server Appliance"
3. Configurer :
   - Nom de l'appliance
   - Type de déploiement (Tiny pour lab)
   - Mot de passe root
4. Connecter à l'hôte ESXi cible
5. Configurer le nom de la VM et le datastore
6. Configurer le réseau :
   - Mode : Static
   - IP, masque, passerelle, DNS
7. Lancer le déploiement et attendre (15-30 min)
8. Configurer le vCenter (Stage 2) :
   - Configurer le SSO (domaine vsphere.local)
   - Lier une licence
   - Rejoindre le CEIP (optionnel)

**Critères de réussite :**
- [ ] VCSA est déployé et accessible
- [ ] L'interface web fonctionne sur `https://vcenter.lab.local`

### TP 3 : Ajout d'hôtes ESXi

**Objectif :** Ajouter un ou plusieurs hôtes ESXi à vCenter.

**Étapes :**
1. Se connecter à vCenter via le Web Client
2. Clic droit sur le datacenter → "Add Host"
3. Saisir l'adresse IP ou le nom de l'hôte ESXi
4. Saisir les identifiants root
5. Accepter le certificat
6. Assigner une licence
7. Configurer le lockdown mode (Disabled pour lab)
8. Terminer l'assistant

**Critères de réussite :**
- [ ] L'hôte apparaît dans l'inventaire
- [ ] L'état est "Connected"

### TP 4 : Organisation de l'inventaire

**Objectif :** Structurer l'inventaire vCenter.

**Étapes :**
1. Créer un datacenter : `Datacenter-LAB`
2. Créer un cluster : `Cluster-01`
3. Créer des dossiers pour organiser les VM :
   - `VMs-Production`
   - `VMs-Tests`
4. Déplacer les hôtes dans le cluster

**Critères de réussite :**
- [ ] L'inventaire est organisé
- [ ] Les hôtes sont dans le cluster

---

## Résumé

- vCenter permet la gestion centralisée de l'infrastructure
- VCSA est une appliance Linux (Photon OS)
- Le déploiement se fait en 2 étapes : déploiement OVF + configuration
- Un DNS fonctionnel est obligatoire pour vCenter

---

## Ressources complémentaires

- [Guide d'installation vCenter](https://docs.vmware.com/en/VMware-vSphere/7.0/vsphere-vcenter-server-70-appliance-deployment-guide.pdf)
- [Configuration requise pour vCenter](https://configmax.esp.vmware.com/guest/home)

---

## Évaluation

- Quiz sur l'architecture vCenter
- Exercice pratique : déploiement complet de VCSA et ajout de 2 hôtes
