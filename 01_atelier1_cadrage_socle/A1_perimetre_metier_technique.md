# A1 - Périmètre métier et technique

> **Atelier 1 - Étape 1.2 : Périmètre métier et technique**  
> Feuilles du classeur : `Atelier 1 - Missions` (+ feuille `Organisation` pour les responsables)  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`00_cadrage/fiche_objet_etude.md`](../00_cadrage/fiche_objet_etude.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS  |
| **Atelier** | Atelier 1 - Cadrage et socle de sécurité |
| **Étape** | 1.2 - Recensement des missions, valeurs métier et biens supports |
| **Livrable** | Périmètre métier et technique documenté, typologie ANSSI respectée |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> Rappel méthodologique : une **valeur métier (VM)** est un processus ou une information ; un **bien support (BS)** est le composant technique, humain ou physique qui la porte. Une VM peut reposer sur **plusieurs BS**, et un BS peut porter **plusieurs VM**.

---

## 2. Mission de l'organisation

**Rhénalis SAS** - *vendre, livrer et facturer du matériel électrique aux professionnels du Grand Est* [F].

Cette mission se décompose en cinq valeurs métier, couvrant le cycle commercial complet : de la prise de commande jusqu'à la comptabilité, en passant par la relation client, la facturation et la gestion des stocks.

---

## 3. Valeurs métier

| Code | Dénomination | Nature | Description | Responsable |
|---|---|---|---|---|
| **VM1** | Prise et traitement des commandes clients | Processus | Saisie des commandes (téléphone, e-mail, commerciaux), contrôle du stock et du crédit client, préparation et expédition. **~70 % du CA** transite par ce processus. Engagement de livraison J+1 sur stock auprès des grands comptes (H02/H03). | Julien Roth, directeur commercial (INTERNE) |
| **VM2** | Fichier clients et prospects | Information | Coordonnées, historique d'achats, conditions tarifaires négociées, devis et opportunités de **~3 500 comptes professionnels**. Contient des **données personnelles (RGPD)** et des informations commercialement sensibles. | Julien Roth, directeur commercial (INTERNE) |
| **VM3** | Facturation et recouvrement | Processus | Émission des factures à partir des commandes livrées, envoi aux clients, suivi des encaissements et relances. Soumis aux **obligations fiscales** et à la **réforme de la facturation électronique**. | Thomas Weber, DAF (INTERNE) |
| **VM4** | Données comptables et financières | Information | Écritures comptables, grand livre, comptes clients et fournisseurs, trésorerie. **Intégrité et conservation légale de 10 ans** exigées ; base des déclarations fiscales et des comptes annuels. | Thomas Weber, DAF (INTERNE) |
| **VM5** | Gestion des stocks et approvisionnements | Processus | Suivi des niveaux de stock des **2 dépôts** (Colmar, Mulhouse), réapprovisionnement, commandes fournisseurs et réception des marchandises. | Responsable logistique **[M]** (INTERNE) |

### 3.1 Priorisation des valeurs métier

| Rang | VM | Criticité | Justification |
|---|---|---|---|
| 1 | **VM4** | 🔴 Critique | Perte définitive → survie de l'organisation menacée (G4, cf. atelier 1 - ER) |
| 2 | **VM1** | 🔴 Critique | Arrêt de 70 % du CA (~300 k€/semaine) dès la 1ʳᵉ semaine (G3) |
| 3 | **VM3** | 🟠 Élevée | Fraude au RIB possible plusieurs centaines de k€ (G3) ; indisponibilité de 2 semaines reste tolérable (G2) |
| 4 | **VM2** | 🟠 Élevée | Violation RGPD, perte de confiance, atteinte à la position commerciale (G3) |
| 5 | **VM5** | 🟡 Modérée | Mode dégradé possible plusieurs jours ; rupture de stock au-delà d'une semaine (G2) |

---

## 4. Biens supports - typologie ANSSI

### 4.1 Vue d'ensemble

| Catégorie ANSSI | Nombre de biens supports | Exemples dans l'étude |
|---|:-:|---|
| **Matériels** | 4 | Postes ADV, portables commerciaux, postes comptabilité, postes entrepôt |
| **Logiciels** | 7 | Module Ventes ERP, CRM, module Facturation, annuaire AD, BDD, sauvegardes, modules Stocks/Achats |
| **Réseaux / canaux** | 1 | Liaisons VPN (site à site et nomades) |
| **Organisations** | 3 | Accès distant infogérant, accès télémaintenance éditeur, personnel |
| **Locaux** | 0 | *Hors périmètre* (hébergement physique chez l'hébergeur IaaS - traité en partie prenante) |

### 4.2 Détail par valeur métier

#### VM1 - Prise et traitement des commandes clients

| Code | Bien support | Type | Description | Responsable |
|---|---|---|---|---|
| BS01 | **Module Ventes de l'ERP** | Logiciel | Saisie et suivi des commandes, contrôle stock et encours | Sophie Haas (INTERNE) |
| BS02 | **Postes de travail de l'ADV** | Matériel | ~10 postes Windows du service administration des ventes, accès à l'ERP via VPN site à site | Sophie Haas (INTERNE) |
| BS03 | **Serveurs d'application ERP/CRM (IaaS)** | Matériel / Logiciel | Machines virtuelles hébergeant l'ERP et le CRM chez un hébergeur IaaS français - **partagé par toutes les VM** | InfoGest Services (EXTERNE) |
| BS04 | **Messagerie (SaaS)** | Logiciel | Canal d'entrée des commandes par e-mail | Fournisseur de messagerie (EXTERNE) |

#### VM2 - Fichier clients et prospects

| Code | Bien support | Type | Description | Responsable |
|---|---|---|---|---|
| BS05 | **Application CRM et portables commerciaux** | Logiciel / Matériel | CRM + 12 portables nomades connectés en VPN | Sophie Haas (INTERNE) |
| BS06 | **Base de données ERP/CRM** | Logiciel | SGBD stockant les données ERP et CRM - **transverse** | InfoGest Services (EXTERNE) |

#### VM3 - Facturation et recouvrement

| Code | Bien support | Type | Description | Responsable |
|---|---|---|---|---|
| BS07 | **Module Facturation de l'ERP + plateforme de facturation électronique** | Logiciel | Génération et émission des factures, connecteur vers la plateforme de dématérialisation (H1) | Sophie Haas (INTERNE) |
| BS08 | **Annuaire Active Directory** | Logiciel | Authentification de tous les utilisateurs et administrateurs - **transverse** | InfoGest Services (EXTERNE) |
| BS09 | **Postes de la comptabilité** | Matériel | Postes du service comptable | Sophie Haas (INTERNE) |
| BS04 | Messagerie (SaaS) | Logiciel | Canal d'envoi des factures | Fournisseur de messagerie (EXTERNE) |

#### VM4 - Données comptables et financières

| Code | Bien support | Type | Description | Responsable |
|---|---|---|---|---|
| BS10 | **Base de données ERP/CRM** | Logiciel | SGBD stockant les données comptables - **transverse** | InfoGest Services (EXTERNE) |
| BS11 | **Système de sauvegarde** | Logiciel / Stockage | Sauvegardes quotidiennes déclarées (H06), **non testées** (H07) - **transverse** | InfoGest Services (EXTERNE) |
| BS12 | **Accès distant d'administration de l'infogérant** | Organisation | VPN d'administration, **sans MFA** supposé (H04), **compte admin partagé** (H05) - **transverse** | InfoGest Services (EXTERNE) |
| BS09 | Postes de la comptabilité | Matériel | Idem VM3 | Sophie Haas (INTERNE) |

#### VM5 - Gestion des stocks et approvisionnements

| Code | Bien support | Type | Description | Responsable |
|---|---|---|---|---|
| BS13 | **Modules Stocks et Achats de l'ERP** | Logiciel | Niveaux de stock, réassort, commandes fournisseurs | Sophie Haas (INTERNE) |
| BS14 | **Postes de l'entrepôt** | Matériel | Postes de réception et préparation des 2 dépôts | Sophie Haas (INTERNE) |

### 4.3 Biens supports complémentaires (transverses)

Ces biens supports, **non rattachés à une seule VM**, portent sur l'ensemble du périmètre et constituent des **points d'entrée privilégiés** pour un attaquant.

| Code | Bien support | Type ANSSI | VM couvertes | Responsable |
|---|---|---|---|---|
| BS15 | **Console d'administration IaaS** | Logiciel | Toutes | InfoGest Services / hébergeur (EXTERNE) |
| BS16 | **Accès de télémaintenance de l'éditeur** | Organisation | VM1, VM3, VM5 | Éditeur de l'ERP (EXTERNE) |
| BS17 | **Personnel (utilisateurs et administrateurs)** | Personnes (Organisation) | Toutes | Direction (INTERNE) |
| BS18 | **Liaisons VPN (site à site et nomades)** | Réseau | Toutes | InfoGest Services (EXTERNE) |

---

## 5. Analyse : biens supports critiques

### 5.1 Biens supports transverses à fort effet de levier

Quatre biens supports sont **communs à toutes les valeurs métier** et concentrent l'essentiel de la menace :

| Bien support | Type | Menace principale | Lien avec atelier 3 |
|---|---|---|---|
| **Annuaire Active Directory** (BS08) | Logiciel | Compromission → élévation de privilèges jusqu'à admin du domaine | InfoGest en zone **Danger** (indice 4,00) |
| **Base de données ERP/CRM** (BS06/BS10) | Logiciel | Chiffrement ou exfiltration → perte définitive | InfoGest en zone **Danger** |
| **Système de sauvegarde** (BS11) | Logiciel / stockage | Suppression → perte irréversible | InfoGest en zone **Danger** |
| **Accès distant d'administration de l'infogérant** (BS12) | Organisation | Point d'entrée n° 1 : pas de MFA, compte partagé | InfoGest en zone **Danger** |

> ⚠️ Ces quatre BS sont **tous administrés par InfoGest Services** (zone danger, atelier 3). Toute mesure qui les protège passe par un **avenant de sécurité** au contrat d'infogérance (M01, PTR).

### 5.2 Composants techniques vitaux à surveiller

| Bien support | Raison de la vigilance | Référence classeur |
|---|---|---|
| **Serveurs d'application ERP/CRM** (BS03) | Portés par l'IaaS, partagés par toutes les VM | Atelier 1 - Missions |
| **Console d'administration IaaS** (BS15) | Accès hyperviseur = contrôle total de la plateforme | Atelier 1 - Missions (biens complémentaires) |
| **Accès de télémaintenance de l'éditeur** (BS16) | Accès admin externe, non contrôlé par Rhénalis | H17 - atelier 3 (pénétration 3) |
| **Personnel** (BS17) | Point d'entrée des scénarios SO3, SO4, SO5 | Atelier 4 - SO |

---

## 6. Responsabilités - répartition INTERNE / EXTERNE

### 6.1 Synthèse

| Responsable | Biens supports portés | Nature |
|---|---|---|
| **Sophie Haas** (resp. informatique) | BS01, BS02, BS05, BS07, BS09, BS13, BS14 | INTERNE |
| **InfoGest Services** | BS03, BS06, BS08, BS10, BS11, BS12, BS15, BS18 | EXTERNE (infogérant) |
| **Éditeur de l'ERP** | BS16 | EXTERNE |
| **Fournisseur de messagerie** | BS04 | EXTERNE |
| **Direction** | BS17 | INTERNE |

### 6.2 Points de vigilance

- **Chaque bien support a un responsable identifié** - condition indispensable pour piloter le plan de traitement.
- **L'infogérant porte 8 des 18 biens supports** de l'étude (44 %), y compris les plus critiques (annuaire, BDD, sauvegardes, accès d'administration).
- **L'éditeur de l'ERP** accède en télémaintenance au serveur d'application (H17) - responsable d'un bien support transverse.
- **La responsabilité du personnel** (BS17) est portée par la Direction, en cohérence avec la politique de sécurité (PSSI - M02, PTR).

---

## 7. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Mission de l'organisation | `Atelier 1 - Missions` | Ligne A1 |
| Valeurs métier (VM1 à VM5) | `Atelier 1 - Missions` | Lignes B2 à N2 |
| Biens supports associés | `Atelier 1 - Missions` | Ligne 6 |
| Descriptions des BS | `Atelier 1 - Missions` | Ligne 7 |
| Responsables des BS | `Atelier 1 - Missions` | Ligne 8 |
| Biens supports complémentaires | `Atelier 1 - Missions` | Bloc « Biens supports complémentaires » (à partir de la ligne 10) |

---

## 8. Checklist de validation

- [x] Chaque valeur métier a une **nature** identifiée (processus ou information).
- [x] Chaque valeur métier a un **responsable** nommé (interne ou externe).
- [x] Chaque valeur métier est reliée à **au moins un bien support**.
- [x] La **typologie ANSSI** est respectée (matériel, logiciel, réseau, organisation, locaux).
- [x] Les **biens supports transverses** sont identifiés (annuaire, BDD, sauvegardes, accès distant, console IaaS, télémaintenance, personnel, VPN).
- [x] Les **responsables** de chaque bien support sont nommés (INTERNE / EXTERNE).
- [x] Aucune confusion entre **valeur métier** (processus / information) et **bien support** (composant).

---

## 9. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Identifier le périmètre métier et technique » (Atelier 1)  
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Organisation`, `Métriques`, `Atelier 1 - Missions`  
- Dossier de synthèse - § 3.1 « Valeurs métier et biens supports » (pages 6)  
- Fiche amont : [`00_cadrage/fiche_objet_etude.md`](../00_cadrage/fiche_objet_etude.md)
- Fiche aval : [`A1_evenements_redoutes.md`](./A1_evenements_redoutes.md) - [`A1_socle_securite_gaps.md`](./A1_socle_securite_gaps.md)