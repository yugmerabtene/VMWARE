# Module 4 : Configuration Réseau Virtuel

> **Durée estimée :** 4 heures

---

## Description

Ce module explore la configuration réseau dans vSphere. Vous apprendrez à configurer des vSwitch standards et distribués, gérer les VLAN, configurer les adaptateurs VMkernel pour différents types de trafic et assurer la redondance réseau.

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Configurer un vSwitch standard
2. Comprendre et configurer les VMkernel adapters
3. Configurer les VLAN et le trunking
4. Déployer un vSphere Distributed Switch (VDS)

---

## Prérequis

- vCenter Server opérationnel (Module 3)
- Au moins un hôte ESXi
- Connaissances réseau de base (VLAN, TCP/IP)

---

## Contenu théorique

### 1. Composants réseau vSphere

| Composant | Rôle |
|-----------|------|
| vSwitch | Commutateur virtuel (standard ou distribué) |
| Port Group | Regroupement logique de ports VM |
| VMkernel Adapter | Interface pour trafic ESXi (management, vMotion, etc.) |
| Uplink | Carte physique connectée au vSwitch |

### 2. Types de vSwitch

| Type | vSphere Standard Switch (VSS) | vSphere Distributed Switch (VDS) |
|------|-------------------------------|----------------------------------|
| Scope | Hôte unique | Datacenter entier |
| Configuration | Par hôte | Centralisée |
| Fonctionnalités | Basiques | Avancées (Network I/O Control, port mirroring) |
| Licence | Incluse | Requiert licence Enterprise+ |

### 3. Types de trafic VMkernel

| Type | Usage |
|------|-------|
| Management | Accès à l'hôte (SSH, Web Client) |
| vMotion | Migration à chaud des VM |
| vSAN | Trafic de stockage vSAN |
| FT | Fault Tolerance logging |
| iSCSI/NFS | Trafic de stockage |

---

## Travaux pratiques

### TP 1 : Configuration d'un vSwitch standard

**Objectif :** Créer et configurer un vSwitch avec uplinks et port groups.

**Étapes :**
1. Se connecter à l'hôte ESXi via vCenter
2. Onglet "Configure" → "Networking" → "Virtual switches"
3. Cliquer sur "Add standard switch"
4. Nommer le vSwitch : `vSwitch-Data`
5. Assigner les uplinks physiques (vmnic1, vmnic2)
6. Créer un port group :
   - Nom : `VM-Network-Data`
   - VLAN ID : 10
7. Créer un second port group :
   - Nom : `VM-Network-Mgmt`
   - VLAN ID : 20

**Critères de réussite :**
- [ ] Le vSwitch est créé avec 2 uplinks
- [ ] Les port groups sont configurés avec les VLAN

### TP 2 : Configuration des VMkernel adapters

**Objectif :** Créer des adaptateurs VMkernel pour différents types de trafic.

**Étapes :**
1. Onglet "Configure" → "VMkernel adapters"
2. Cliquer sur "New VMkernel adapter"
3. Créer l'adaptateur Management :
   - Nom : `vmk0-management`
   - Port group : `Management-Network`
   - Activer : Management traffic
   - IP : 192.168.1.11/24
4. Créer l'adaptateur vMotion :
   - Nom : `vmk1-vmotion`
   - Port group : `vMotion-Network`
   - Activer : vMotion traffic
   - IP : 192.168.10.11/24

**Critères de réussite :**
- [ ] Les adaptateurs VMkernel sont créés
- [ ] Le trafic vMotion est activé

### TP 3 : Configuration du teaming et failover

**Objectif :** Configurer la redondance des uplinks.

**Étapes :**
1. Sélectionner le vSwitch → "Properties"
2. Onglet "Teaming and failover"
3. Configurer :
   - Active uplinks : vmnic0, vmnic1
   - Standby uplinks : vmnic2
4. Choisir la politique : "Route based on IP hash" ou "Route based on originating virtual port"

**Critères de réussite :**
- [ ] La configuration de teaming est active
- [ ] Tester la redondance en déconnectant un uplink

### TP 4 : Déploiement d'un Distributed Switch

**Objectif :** Déployer un VDS pour une gestion centralisée.

**Étapes :**
1. Dans vCenter, onglet "Networking"
2. Clic droit sur le datacenter → "New Distributed Switch"
3. Nommer : `DSwitch-01`
4. Version : 7.0 (ou dernière disponible)
5. Configurer les uplinks : 2 uplinks par défaut
6. Ajouter les hôtes au VDS :
   - Sélectionner les hôtes
   - Assigner les uplinks physiques
7. Créer un Distributed Port Group :
   - Nom : `DVPG-Production`
   - VLAN : 100

**Critères de réussite :**
- [ ] Le VDS est créé et visible dans l'inventaire
- [ ] Les hôtes sont membres du VDS

---

## Résumé

- vSwitch standard = configuration par hôte
- vSwitch distribué = configuration centralisée
- VMkernel adapters = trafic ESXi (management, vMotion, stockage)
- Le teaming assure la redondance réseau

---

## Ressources complémentaires

- [Guide réseau vSphere](https://docs.vmware.com/en/VMware-vSphere/7.0/vsphere-networking.pdf)
- [VDS best practices](https://kb.vmware.com/s/article/10176)

---

## Évaluation

- Quiz sur les composants réseau
- Exercice pratique : configuration complète du réseau avec VDS
