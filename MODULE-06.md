# Module 6 : Clusters et Ressources (HA/DRS)

> **Auteur :** yugmerabtene
> **Version :** 2.0
> **Durée estimée :** 4 heures

---

## Description

Ce module présente les fonctionnalités avancées de clustering : High Availability (HA) pour la tolérance aux pannes et Distributed Resource Scheduler (DRS) pour l'équilibrage automatique des charges. Vous apprendrez à configurer ces services essentiels pour la production.

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Configurer vSphere High Availability (HA)
2. Configurer Distributed Resource Scheduler (DRS)
3. Créer des storage policies
4. Gérer les pools de ressources

---

## Prérequis

- vCenter Server opérationnel (Module 3)
- Cluster avec au moins 2 hôtes ESXi
- Stockage partagé configuré (Module 5)

---

## Contenu théorique

### 1. vSphere High Availability (HA)

HA assure la disponibilité des VM en cas de panne d'un hôte.

**Fonctionnement :**
- Un agent (FDM) est installé sur chaque hôte
- Les hôtes échangent des signaux (heartbeat)
- En cas de panne, les VM sont redémarrées sur un autre hôte

**Paramètres clés :**
- **Host Monitoring** : Surveillance des hôtes
- **Admission Control** : Garantit les ressources en cas de panne
- **VM Restart Priority** : Ordre de redémarrage des VM

### 2. Distributed Resource Scheduler (DRS)

DRS équilibre automatiquement les charges de travail entre les hôtes.

**Modes :**
- **Fully Automated** : Migration automatique des VM
- **Partially Automated** : Recommandations manuelles
- **Manual** : Pas d'automatisation

**Règles DRS :**
- **Affinity** : VM ensemble sur le même hôte
- **Anti-affinity** : VM séparées sur des hôtes différents

### 3. Pools de ressources

Permettent d'allouer des ressources garanties aux VM.

**Types :**
- **Reservation** : Ressources garanties
- **Limit** : Maximum de ressources utilisables
- **Shares** : Priorité relative en cas de contention

---

## Travaux pratiques

### TP 1 : Configuration de vSphere HA

**Objectif :** Activer et configurer HA sur un cluster.

**Étapes :**
1. Dans vCenter, sélectionner le cluster
2. Onglet "Configure" → "vSphere HA"
3. Cliquer sur "Edit"
4. Activer vSphere HA
5. Configurer :
   - **Datastores for heartbeat** : Sélectionner les datastores partagés
   - **Host monitoring** : Enabled
   - **VM monitoring** : Disabled (pour lab)
   - **Admission control** : Enable
   - **Failover capacity** : 1 host
6. Terminer l'assistant

**Critères de réussite :**
- [ ] HA est activé sur le cluster
- [ ] L'état HA est "Green"

### TP 2 : Test de basculement HA

**Objectif :** Vérifier le fonctionnement de HA.

**Étapes :**
1. Créer une VM de test sur l'hôte 1
2. Démarrer la VM et noter son hôte
3. Simuler une panne :
   - Déconnecter l'hôte 1 du réseau, OU
   - Arrêter brutalement l'hôte 1
4. Observer le comportement :
   - La VM redémarre automatiquement sur l'hôte 2
5. Vérifier les événements dans vCenter

**Critères de réussite :**
- [ ] La VM a redémarré automatiquement
- [ ] Le temps de basculement est < 2 minutes

### TP 3 : Configuration de DRS

**Objectif :** Activer DRS et créer des règles.

**Étapes :**
1. Sélectionner le cluster → "Configure" → "vSphere DRS"
2. Cliquer sur "Edit"
3. Activer DRS
4. Mode : "Fully Automated"
5. Automation level : Level 3 (balanced)
6. Créer une règle d'affinité :
   - Type : "Keep VMs together"
   - VMs : VM-Web, VM-App
7. Créer une règle d'anti-affinité :
   - Type : "Separate VMs"
   - VMs : VM-DB-Primary, VM-DB-Replica

**Critères de réussite :**
- [ ] DRS est activé
- [ ] Les règles sont appliquées

### TP 4 : Création d'un pool de ressources

**Objectif :** Allouer des ressources garanties.

**Étapes :**
1. Sélectionner le cluster → "Resource Pools"
2. Clic droit → "New Resource Pool"
3. Configurer :
   - Nom : `Pool-Production`
   - CPU Reservation : 4 GHz
   - Memory Reservation : 4 GB
   - Shares : Normal
4. Déplacer des VM dans le pool

**Critères de réussite :**
- [ ] Le pool est créé avec les réservations
- [ ] Les VM sont assignées au pool

---

## Résumé

- HA = redémarrage automatique des VM en cas de panne
- DRS = équilibrage automatique des charges
- Admission control = garantie de ressources en cas de panne
- Les pools de ressources permettent d'isoler les workloads

---

## Ressources complémentaires

- [Guide HA/DRS](https://docs.vmware.com/en/VMware-vSphere/7.0/vsphere-availability.pdf)
- [DRS best practices](https://blogs.vmware.com/vsphere/2019/11/drs-quickstart-guide.html)

---

## Évaluation

- Quiz sur HA et DRS
- Exercice pratique : configuration complète HA + DRS avec test de basculement
