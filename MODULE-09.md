# Module 9 : Supervision et Performance

> **Durée estimée :** 4 heures

---

## Description

Ce module couvre la supervision et l'optimisation des performances. Vous apprendrez à configurer des alertes, analyser les métriques de performance (CPU, mémoire, disque, réseau), utiliser les logs pour le troubleshooting et optimiser votre infrastructure.

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Configurer des alertes dans vCenter
2. Analyser les performances des hôtes et VM
3. Utiliser les logs pour le troubleshooting
4. Configurer la collecte de métriques

---

## Prérequis

- vCenter Server opérationnel (Module 3)
- Au moins un hôte ESXi avec des VM

---

## Contenu théorique

### 1. Supervision dans vSphere

vCenter collecte des métriques de performance en temps réel et historiques.

**Métriques principales :**
- CPU : Utilisation, prêt, co-stop
- Mémoire : Active, partagée, ballonnée
- Disque : Latence, IOPS, débit
- Réseau : Utilisation, paquets, erreurs

### 2. Niveaux de statistiques

| Niveau | Durée | Granularité | Usage |
|--------|-------|-------------|-------|
| 1 | 1 jour | 5 min | Défaut |
| 2 | 1 semaine | 30 min | |
| 3 | 1 mois | 2 h | |
| 4 | 1 an | 1 jour | |

### 3. Types d'alertes

| Type | Description |
|------|-------------|
| Warning | Seuil bas dépassé |
| Alarm | Seuil haut dépassé |
| Event | Événement système |

---

## Travaux pratiques

### TP 1 : Configuration d'alertes

**Objectif :** Créer des alertes pour surveiller l'infrastructure.

**Étapes :**
1. Menu → "Alerts" → "Alarm Definitions"
2. Cliquer sur "New Alarm" → "VM"
3. Nommer : `CPU-High-Usage`
4. Configurer le trigger :
   - Condition : "CPU Usage" > 80%
   - Durée : 5 minutes
5. Configurer les actions :
   - Warning : Envoyer un email
   - Alarm : Envoyer un email + SNMP trap
6. Appliquer à toutes les VM
7. Répéter pour :
   - `Memory-High-Usage`
   - `Datastore-Low-Space`

**Critères de réussite :**
- [ ] Les alertes sont créées
- [ ] Les emails sont configurés

### TP 2 : Analyse des performances

**Objectif :** Analyser les performances d'une VM.

**Étapes :**
1. Sélectionner une VM
2. Onglet "Monitor" → "Performance"
3. Analyser les graphiques :
   - CPU : Usage, Ready, Co-stop
   - Memory : Active, Balloon, Swapped
   - Disk : Latency, IOPS
   - Network : Throughput, Packets
4. Identifier les bottlenecks :
   - CPU Ready > 5% = problème
   - Memory Balloon > 0 = contention
   - Disk Latency > 20ms = problème

**Critères de réussite :**
- [ ] Vous pouvez lire les graphiques
- [ ] Identifier un bottleneck

### TP 3 : Utilisation des logs

**Objectif :** Accéder aux logs pour le troubleshooting.

**Étapes :**
1. Sélectionner l'hôte
2. Onglet "Monitor" → "Logs"
3. Consulter les logs :
   - `hostd.log` : Service de gestion
   - `vpxa.log` : Agent vCenter
   - `vmkernel.log` : Noyau ESXi
4. Filtrer par niveau : Error, Warning
5. Exporter les logs si nécessaire

**Critères de réussite :**
- [ ] Vous pouvez accéder aux logs
- [ ] Identifier une erreur

### TP 4 : Configuration de la collecte de métriques

**Objectif :** Configurer les niveaux de statistiques.

**Étapes :**
1. Menu → "Administration" → "Global Settings" → "Statistics"
2. Configurer :
   - Statistics Level : 1 (défaut) ou 2 (plus détaillé)
   - Statistics Duration : 1 an
3. Appliquer
4. Vérifier que les données sont collectées

**Critères de réussite :**
- [ ] Les statistiques sont configurées
- [ ] Les données historiques sont disponibles

---

## Résumé

- vCenter collecte des métriques en temps réel et historiques
- Les alertes notifient les problèmes
- L'analyse des performances identifie les bottlenecks
- Les logs aident au troubleshooting

---

## Ressources complémentaires

- [Performance Best Practices](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/files/pdf/techpaper/VMware-vSphere65-Performance-Best-Practices.pdf)
- [Troubleshooting Guide](https://docs.vmware.com/en/VMware-vSphere/7.0/vsphere-troubleshooting.pdf)

---

## Évaluation

- Quiz sur les métriques de performance
- Exercice pratique : configuration d'alertes + analyse de performance
