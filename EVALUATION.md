# Évaluation du cours VMware vSphere


---

## Quiz général

### Module 1 : Introduction à la Virtualisation

1. Qu'est-ce que la virtualisation ?
2. Quelle est la différence entre un hyperviseur de type 1 et type 2 ?
3. Citez 3 avantages de la virtualisation.
4. Nommez 2 hyperviseurs de type 1 et 2 de type 2.

### Module 2 : Installation d'ESXi

5. Quel est le rôle du DCUI ?
6. Quelle est la configuration matérielle minimale recommandée pour ESXi ?
7. Comment configurer l'adresse IP d'un hôte ESXi ?

### Module 3 : vCenter Server

8. Quel est le rôle de vCenter dans une infrastructure vSphere ?
9. Qu'est-ce que VCSA ?
10. Pourquoi un DNS est-il requis pour vCenter ?

### Module 4 : Réseau Virtuel

11. Quelle est la différence entre VSS et VDS ?
12. À quoi servent les VMkernel adapters ?
13. Citez 3 types de trafic VMkernel.

### Module 5 : Stockage

14. Quelle est la différence entre VMFS et NFS ?
15. Qu'est-ce que vSAN ?
16. Quel protocole est utilisé pour le stockage bloc sur IP ?

### Module 6 : HA/DRS

17. Comment fonctionne vSphere HA ?
18. Quels sont les modes de DRS ?
19. Qu'est-ce qu'une règle d'anti-affinité ?

### Module 7 : Migration

20. Quels sont les prérequis pour vMotion ?
21. Quelle est la différence entre vMotion et Storage vMotion ?
22. Qu'est-ce qu'un template ?

### Module 8 : Sécurité

23. Qu'est-ce que le Lockdown Mode ?
24. Expliquez le modèle RBAC de vSphere.
25. Pourquoi intégrer vCenter à Active Directory ?

### Module 9 : Supervision

26. Quelles métriques surveiller pour détecter un problème CPU ?
27. À quoi servent les alertes dans vCenter ?
28. Quels logs consulter en premier pour troubleshooting ?

---

## Exercices pratiques

### Exercice 1 : Installation complète (4h)

**Objectif :** Déployer une infrastructure vSphere complète.

**Tâches :**
1. Installer ESXi sur un serveur physique ou nested
2. Déployer vCenter Server Appliance
3. Ajouter l'hôte à vCenter
4. Configurer le réseau (vSwitch, port groups)
5. Créer un datastore VMFS
6. Créer une VM et l'installer

**Critères de réussite :**
- [ ] ESXi installé et configuré
- [ ] vCenter déployé et accessible
- [ ] Hôte ajouté à vCenter
- [ ] Réseau configuré
- [ ] Datastore créé
- [ ] VM fonctionnelle

### Exercice 2 : Configuration HA/DRS (2h)

**Objectif :** Configurer la haute disponibilité et l'équilibrage.

**Tâches :**
1. Créer un cluster avec 2+ hôtes
2. Activer et configurer HA
3. Activer et configurer DRS
4. Tester le basculement HA
5. Vérifier l'équilibrage DRS

**Critères de réussite :**
- [ ] HA activé et fonctionnel
- [ ] DRS activé et équilibrant
- [ ] Test de basculement réussi

### Exercice 3 : Migration et Templates (2h)

**Objectif :** Maîtriser la mobilité des VM.

**Tâches :**
1. Créer une VM de référence
2. Convertir en template
3. Déployer 2 VM depuis le template
4. Migrer une VM avec vMotion
5. Migrer une VM avec Storage vMotion

**Critères de réussite :**
- [ ] Template créé
- [ ] VM déployées depuis le template
- [ ] Migrations réussies sans interruption

### Exercice 4 : Sécurité et Supervision (2h)

**Objectif :** Sécuriser et superviser l'infrastructure.

**Tâches :**
1. Créer un rôle personnalisé
2. Configurer les permissions
3. Activer le Lockdown Mode
4. Créer des alertes (CPU, mémoire, stockage)
5. Analyser les performances

**Critères de réussite :**
- [ ] Rôle créé et assigné
- [ ] Lockdown activé
- [ ] Alertes configurées
- [ ] Analyse de performance réalisée

---

## Critères d'évaluation

| Compétence | Niveau attendu |
|------------|----------------|
| Installation ESXi | Autonome |
| Déploiement vCenter | Autonome |
| Configuration réseau | Autonome |
| Gestion stockage | Autonome |
| Configuration HA/DRS | Autonome |
| Migration VM | Autonome |
| Sécurité | Conscient |
| Supervision | Autonome |

---

## Barème

- Quiz : 28 questions × 1 point = 28 points
- Exercices pratiques : 4 exercices × 18 points = 72 points
- **Total : 100 points**

**Note de réussite : 70/100**
