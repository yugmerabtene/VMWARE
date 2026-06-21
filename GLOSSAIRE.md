# Glossaire VMware vSphere

> **Auteur :** yugmerabtene

---

## Termes techniques

### A
- **Admission Control** : Mécanisme HA garantissant les ressources en cas de panne
- **Anti-affinity Rule** : Règle DRS forçant des VM à être sur des hôtes différents

### B
- **Bare-Metal** : Hyperviseur installé directement sur le matériel (Type 1)

### C
- **Cluster** : Regroupement de plusieurs hôtes ESXi gérés ensemble
- **Clone** : Copie exacte d'une machine virtuelle
- **Co-stop** : Métrique CPU indiquant qu'une VM attend plusieurs vCPU simultanément

### D
- **Datacenter** : Conteneur logique regroupant hôtes, VM et ressources
- **Datastore** : Espace de stockage pour les fichiers VM (VMFS, NFS, vSAN)
- **DCUI** : Direct Console User Interface - interface locale d'ESXi
- **DRS** : Distributed Resource Scheduler - équilibrage automatique des charges

### E
- **EVC** : Enhanced vMotion Compatibility - compatibilité CPU pour vMotion
- **ESXi** : Hyperviseur bare-metal de VMware

### F
- **FDM** : Fault Domain Manager - agent HA sur chaque hôte
- **FT** : Fault Tolerance - tolérance aux pannes continue

### H
- **HA** : High Availability - redémarrage automatique des VM en cas de panne
- **Host Client** : Interface web locale d'ESXi

### L
- **Lockdown Mode** : Mode restreignant l'accès direct aux hôtes ESXi

### N
- **NFS** : Network File System - protocole de stockage fichier

### P
- **Port Group** : Regroupement logique de ports sur un vSwitch
- **vMotion** : Migration à chaud d'une VM entre hôtes

### R
- **RBAC** : Role-Based Access Control - contrôle d'accès basé sur les rôles
- **Resource Pool** : Allocation de ressources garanties pour les VM

### S
- **Snapshot** : Capture de l'état d'une VM à un instant T
- **SSO** : Single Sign-On - authentification centralisée vCenter
- **Storage vMotion** : Migration à chaud des fichiers VM entre datastores

### T
- **Template** : Modèle de VM non modifiable pour déploiement

### V
- **VCSA** : vCenter Server Appliance - appliance Linux pour vCenter
- **VDS** : vSphere Distributed Switch - commutateur distribué
- **VMFS** : Virtual Machine File System - système de fichiers VMware
- **VMkernel** : Noyau optimisé d'ESXi
- **vSAN** : Virtual SAN - stockage hyperconvergé VMware
- **VSS** : vSphere Standard Switch - commutateur standard
- **vSwitch** : Commutateur virtuel dans ESXi

---

## Abréviations courantes

| Abréviation | Signification |
|-------------|---------------|
| CPU | Central Processing Unit |
| RAM | Random Access Memory |
| SAN | Storage Area Network |
| NAS | Network Attached Storage |
| iSCSI | Internet Small Computer Systems Interface |
| FC | Fibre Channel |
| VLAN | Virtual Local Area Network |
| DNS | Domain Name System |
| AD | Active Directory |
| LDAP | Lightweight Directory Access Protocol |
