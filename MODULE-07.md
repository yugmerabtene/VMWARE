# Module 7 : Migration et Mobilité

> **Auteur :** yugmerabtene
> **Contact :** yug.merabtene@gmail.com
> **Version :** 2.0
> **Durée estimée :** 3 heures

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Configurer et utiliser vMotion
2. Configurer et utiliser Storage vMotion
3. Créer des templates de VM
4. Cloner et convertir des VM

---

## Prérequis

- vCenter Server opérationnel (Module 3)
- Cluster avec au moins 2 hôtes ESXi
- Stockage partagé configuré (Module 5)
- Réseau vMotion configuré (Module 4)

---

## Contenu théorique

### 1. vMotion (Compute Migration)

Permet de déplacer une VM en cours d'exécution d'un hôte à un autre sans interruption.

**Prérequis :**
- Stockage partagé accessible par les deux hôtes
- Réseau vMotion dédié configuré
- CPU compatibles (EVC activé si nécessaire)

**Fonctionnement :**
1. Copie de la mémoire de la VM vers l'hôte destination
2. Synchronisation des pages modifiées
3. Basculement rapide (< 1 seconde)

### 2. Storage vMotion

Permet de déplacer les fichiers d'une VM d'un datastore à un autre sans interruption.

**Prérequis :**
- Les deux datastores doivent être accessibles
- Espace suffisant sur le datastore destination

### 3. Templates et Clones

| Type | Description |
|------|-------------|
| Template | Modèle non modifiable pour déploiement |
| Clone | Copie exacte d'une VM (modifiable) |
| Clone personnalisé | Copie avec modification des paramètres |

---

## Travaux pratiques

### TP 1 : Configuration du réseau vMotion

**Objectif :** Configurer un adaptateur VMkernel dédié à vMotion.

**Étapes :**
1. Sélectionner l'hôte → "Configure" → "VMkernel adapters"
2. Créer un nouvel adaptateur :
   - Nom : `vmk-vmotion`
   - Port group : `vMotion-Network`
   - Activer : "vMotion"
   - IP : 10.0.10.11/24
3. Répéter sur le second hôte (IP : 10.0.10.12)
4. Vérifier la connectivité entre les hôtes

**Critères de réussite :**
- [ ] L'adaptateur vMotion est créé sur chaque hôte
- [ ] Les hôtes peuvent se joindre sur le réseau vMotion

### TP 2 : Migration vMotion

**Objectif :** Migrer une VM d'un hôte à un autre.

**Étapes :**
1. Créer une VM de test sur l'hôte 1
2. Démarrer la VM et générer de la charge (ping continu)
3. Clic droit sur la VM → "Migrate"
4. Sélectionner "Change compute resource only"
5. Choisir l'hôte destination
6. Vérifier la priorité de migration
7. Lancer la migration
8. Observer le ping : aucune perte de paquets

**Critères de réussite :**
- [ ] La VM a migré sans interruption
- [ ] Le ping n'a pas été interrompu

### TP 3 : Storage vMotion

**Objectif :** Déplacer les fichiers d'une VM vers un autre datastore.

**Étapes :**
1. Sélectionner la VM
2. Clic droit → "Migrate"
3. Sélectionner "Change storage only"
4. Choisir le datastore destination
5. Format : "Same format as source" ou "Thick/Lazy/Thin"
6. Lancer la migration

**Critères de réussite :**
- [ ] La VM a migré vers le nouveau datastore
- [ ] La VM est restée accessible pendant la migration

### TP 4 : Création de templates

**Objectif :** Créer un template pour déploiement rapide.

**Étapes :**
1. Créer une VM de référence :
   - Installer l'OS
   - Configurer les paramètres de base
   - Installer les outils (VMware Tools)
2. Éteindre la VM
3. Clic droit → "Template" → "Convert to Template"
4. Déployer une VM depuis le template :
   - Clic droit sur le template → "New VM from this template"
   - Suivre l'assistant

**Critères de réussite :**
- [ ] Le template est créé
- [ ] Une VM a été déployée depuis le template

---

## Résumé

- vMotion = migration à chaud des VM entre hôtes
- Storage vMotion = migration des fichiers entre datastores
- Templates = modèles pour déploiement rapide
- Clone = copie exacte d'une VM

---

## Ressources complémentaires

- [Guide vMotion](https://kb.vmware.com/s/article/100369)
- [vMotion best practices](https://kb.vmware.com/s/article/100368)

---

## Évaluation

- Quiz sur les types de migration
- Exercice pratique : vMotion + Storage vMotion + création de template
