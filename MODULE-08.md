# Module 8 : Sécurité et Conformité

> **Auteur :** yugmerabtene
> **Contact :** yug.merabtene@gmail.com
> **Version :** 2.0
> **Durée estimée :** 3 heures

---

## Objectifs pédagogiques

À la fin de ce module, vous serez capable de :
1. Configurer les rôles et permissions dans vCenter
2. Activer le Lockdown Mode sur les hôtes
3. Configurer l'authentification centralisée (Active Directory)
4. Auditer la sécurité de l'infrastructure

---

## Prérequis

- vCenter Server opérationnel (Module 3)
- Au moins un hôte ESXi
- Connaissances de base en sécurité informatique

---

## Contenu théorique

### 1. Modèle de sécurité vSphere

vSphere utilise un modèle RBAC (Role-Based Access Control).

**Composants :**
- **Users/Groups** : Identités (local ou AD/LDAP)
- **Roles** : Ensemble de privilèges
- **Permissions** : Association User/Group + Role sur un objet

### 2. Rôles par défaut

| Rôle | Privilèges |
|------|------------|
| Administrator | Tous les privilèges |
| Read-Only | Lecture seule |
| No Access | Aucun accès |
| Virtual Machine Power User | Gestion des VM |
| Resource Pool Administrator | Gestion des pools |

### 3. Lockdown Mode

Restreint l'accès direct aux hôtes ESXi.

| Mode | Description |
|------|-------------|
| Disabled | Accès normal |
| Normal | Accès root limité via DCUI |
| Strict | Aucun accès root, uniquement vCenter |

### 4. Bonnes pratiques de sécurité

- Utiliser l'authentification AD/LDAP
- Activer le Lockdown Mode en production
- Désactiver les services inutiles (SSH, Shell)
- Chiffrer les VM (VM Encryption)
- Auditer régulièrement les accès

---

## Travaux pratiques

### TP 1 : Configuration des rôles et permissions

**Objectif :** Créer un rôle personnalisé et l'assigner.

**Étapes :**
1. Menu → "Administration" → "Roles"
2. Cliquer sur l'icône "+" pour créer un rôle
3. Nommer : `Operator-VM`
4. Sélectionner les privilèges :
   - Virtual Machine → Interaction → Power On/Off
   - Virtual Machine → Snapshot → Create/Remove
   - Datastore → Allocate space
5. Enregistrer le rôle
6. Menu → "Global Permissions"
7. Ajouter un utilisateur ou groupe
8. Assigner le rôle `Operator-VM`
9. Propager aux objets enfants

**Critères de réussite :**
- [ ] Le rôle personnalisé est créé
- [ ] L'utilisateur a les permissions correctes

### TP 2 : Configuration du Lockdown Mode

**Objectif :** Activer le Lockdown Mode sur un hôte.

**Étapes :**
1. Sélectionner l'hôte ESXi
2. Onglet "Configure" → "System" → "Security Profile"
3. Section "Lockdown Mode" → "Edit"
4. Sélectionner "Normal" (pour lab) ou "Strict" (production)
5. Confirmer
6. Tester l'accès :
   - Tenter de se connecter directement à l'hôte
   - Vérifier que seul vCenter fonctionne

**Critères de réussite :**
- [ ] Le Lockdown Mode est activé
- [ ] L'accès direct est restreint

### TP 3 : Configuration de l'authentification AD

**Objectif :** Intégrer vCenter à Active Directory.

**Étapes :**
1. Menu → "Administration" → "Single Sign-On" → "Identity Sources"
2. Cliquer sur "Add Identity Source"
3. Type : "Active Directory over LDAP"
4. Configurer :
   - Domain name : `lab.local`
   - Primary URL : `ldap://dc.lab.local`
   - Username : `administrator@lab.local`
   - Password : mot de passe AD
5. Tester la connexion
6. Enregistrer
7. Ajouter des groupes AD aux permissions vCenter

**Critères de réussite :**
- [ ] La source d'identité AD est configurée
- [ ] Les utilisateurs AD peuvent se connecter

### TP 4 : Audit de sécurité

**Objectif :** Vérifier la configuration de sécurité.

**Étapes :**
1. Menu → "Administration" → "Security"
2. Vérifier :
   - **Users and Groups** : Comptes actifs
   - **Roles** : Rôles assignés
   - **Global Permissions** : Permissions globales
3. Vérifier les services actifs sur l'hôte :
   - SSH : Disabled (sauf maintenance)
   - Shell : Disabled
4. Vérifier les certificats :
   - Menu → "Administration" → "Certificates"

**Critères de réussite :**
- [ ] L'audit est complété
- [ ] Les bonnes pratiques sont respectées

---

## Résumé

- vSphere utilise un modèle RBAC
- Lockdown Mode restreint l'accès direct aux hôtes
- L'intégration AD centralise l'authentification
- Auditer régulièrement la sécurité

---

## Ressources complémentaires

- [Security Guide vSphere](https://docs.vmware.com/en/VMware-vSphere/7.0/vsphere-security.pdf)
- [Lockdown Mode KB](https://kb.vmware.com/s/article/100610)

---

## Évaluation

- Quiz sur les concepts de sécurité
- Exercice pratique : configuration RBAC + Lockdown + audit
