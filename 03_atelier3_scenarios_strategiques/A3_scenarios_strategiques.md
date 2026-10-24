# A3 - Scénarios stratégiques

> **Atelier 3 - Étape 3.2 : Scénarios stratégiques**  
> Feuille du classeur : `Atelier 3 - SS` (+ support graphique `Atelier 3 - SS1`)  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`A3_parties_prenantes.md`](./A3_parties_prenantes.md) · Fiches associées : [`A3_mesures_ecosysteme.md`](./A3_mesures_ecosysteme.md), [`04_atelier4_scenarios_operationnels/A4_scenarios_operationnels.md`](../04_atelier4_scenarios_operationnels/A4_scenarios_operationnels.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS *(cas fictif)* |
| **Atelier** | Atelier 3 - Scénarios stratégiques |
| **Étape** | 3.2 - Construction des chemins d'attaque stratégiques |
| **Livrable** | Cinq scénarios stratégiques SS1 à SS5, cotés en gravité, reliés aux couples SR/OV, aux ER et aux PP |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - Un **scénario stratégique (SS)** décrit un **chemin d'attaque** de haut niveau, de la source de risque à l'événement redouté, en passant ou non par une partie prenante. Il est coté par la **gravité** de l'ER visé et sert de base aux scénarios opérationnels de l'atelier 4.  
> Chaque SS est rattaché à un **couple SR/OV retenu** (atelier 2), à une ou plusieurs **parties prenantes** (atelier 3), à un ou plusieurs **ER** (atelier 1) et à un **risque final** (atelier 5).

---

## 2. Vue d'ensemble

### 2.1 Tableau récapitulatif

| Code | Couple SR/OV | Intermédiaire(s) | Valeur métier visée | ER atteint(s) | Gravité | Risque final |
|:-:|---|---|---|:-:|:-:|:-:|
| **SS1** | SR1/OV1 - Rançongiciel | **InfoGest Services** (zone danger) + **console IaaS** de l'hébergeur (zone contrôle) | VM4 - Données comptables et financières | ER6, ER1, ER3 | 🔴 **G4** | **R1** |
| **SS2** | SR1/OV1 - Rançongiciel | **Éditeur de l'ERP** (zone contrôle) | VM1 - Prise et traitement des commandes | ER1 | 🟠 **G3** | **R2** |
| **SS3** | SR1/OV1 - Rançongiciel | *Aucun* (chemin direct par un salarié) | VM4 - Données comptables et financières | ER6, ER1 | 🔴 **G4** | **R3** |
| **SS4** | SR2/OV2 - Fraude financière | *Aucun* (messagerie d'un salarié ; grands comptes **victimes**) | VM3 - Facturation et recouvrement | ER5 | 🟠 **G3** | **R4** |
| **SS5** | SR3/OV3 - Menace interne | *Aucun* (accès légitime au CRM) | VM2 - Fichier clients et prospects | ER3 | 🟠 **G3** | **R5** |

### 2.2 Cartographie des scénarios stratégiques

![Scénarios stratégiques — de la source de risque à l'événement redouté](captures/A3_scenarios_strategiques.png)

> Cette cartographie correspond à la page 11 du dossier de synthèse. Elle montre les cinq chemins, les parties prenantes traversées (trait plein) ou non (pointillés), et les ER visés.

### 2.3 Lecture

- **Deux scénarios passent par un tiers** : SS1 (via l'infogérant et la console de l'hébergeur) et SS2 (via l'éditeur de l'ERP). Ils sont directement liés aux mesures sur l'écosystème de l'atelier 3.
- **Trois scénarios sont directs** : SS3 (via un salarié piégé), SS4 (via la messagerie d'un salarié, avec les grands comptes comme victimes) et SS5 (via un accès légitime au CRM). Ils ne donnent pas lieu à une mesure de l'atelier 3, mais à des mesures sur les biens supports (atelier 5).
- **Deux scénarios atteignent un ER coté G4** : SS1 et SS3, tous deux visant la perte définitive des données comptables (ER6). Ce sont les deux risques élevés (R1, R3).

---

## 3. Description détaillée des scénarios

### 3.1 SS1 - Rançongiciel via l'infogérant

| Champ | Valeur |
|---|---|
| **Code** | SS1 |
| **Couple SR/OV** | SR1/OV1 - Organisation criminelle (rançongiciel) / Gain financier par rançon et double extorsion |
| **Parties prenantes** | **PP1 - InfoGest Services** (zone danger, indice 4,00) ; **PP2 - Hébergeur IaaS** (zone contrôle, indice 1,78) |
| **Valeur métier visée** | VM4 - Données comptables et financières |
| **ER atteints** | **ER6** (perte définitive des données, G4), **ER1** (ERP indisponible > 1 semaine, G3), **ER3** (vol du fichier clients, G3) |
| **Gravité** | 🔴 **G4** |
| **Risque final** | **R1** |

**Chemin d'attaque stratégique** :

1. **Compromission de l'infogérant** : hameçonnage d'un technicien, ou exploitation du VPN d'administration sans MFA (H04) et du compte administrateur partagé (H05).
2. **Prise de contrôle de l'annuaire et des serveurs** : avec les accès de l'infogérant, l'attaquant dispose des droits d'administration sur l'annuaire, les serveurs d'application et la base de données.
3. **Exfiltration des données ERP/CRM** : les données comptables, commerciales et clients sont copiées avant le chiffrement, pour la double extorsion.
4. **Chiffrement et destruction des sauvegardes** : l'attaquant chiffre l'ERP/CRM, puis supprime les sauvegardes et instantanés **via la console de l'hébergeur IaaS**, à laquelle l'infogérant a accès. Les sauvegardes étant hébergées sur la même infrastructure (H08), elles ne permettent pas la restauration.

**Biens supports concernés** : accès distant d'administration de l'infogérant, annuaire, serveurs d'application, base de données, système de sauvegarde, console IaaS.

**Facteurs favorisants** (GAP de l'atelier 1) : GAP01 (pas de MFA), GAP02 (compte admin partagé), GAP03 (sauvegardes non testées, pas de copie hors ligne), GAP05 (pas de supervision), GAP11 (contrat sans clause de sécurité).

**Mesures de l'atelier 3** : ECO1 (avenant au contrat d'infogérance), ECO2 (bastion et comptes nominatifs), ECO3 (vérification de l'hébergeur, MFA console, sauvegarde immuable).

**Mesures du PTR** : M01, M04, M06, M07, M11, M13, M15, M16, M17.

---

### 3.2 SS2 - Rançongiciel via l'éditeur de l'ERP

| Champ | Valeur |
|---|---|
| **Code** | SS2 |
| **Couple SR/OV** | SR1/OV1 - Organisation criminelle (rançongiciel) / Gain financier par rançon |
| **Partie prenante** | **PP3 - Éditeur de l'ERP** (zone contrôle, indice 1,33) |
| **Valeur métier visée** | VM1 - Prise et traitement des commandes clients |
| **ER atteint** | **ER1** (ERP indisponible > 1 semaine, G3) |
| **Gravité** | 🟠 **G3** |
| **Risque final** | **R2** |

**Chemin d'attaque stratégique** :

1. **Compromission de l'éditeur** : compte de télémaintenance compromis (H17) ou mise à jour piégée.
2. **Accès administrateur au serveur d'application** : l'attaquant obtient les droits d'administration sur le serveur ERP, via l'accès de télémaintenance.
3. **Chiffrement de l'ERP** : l'application est chiffrée. L'annuaire et les sauvegardes ne sont **pas** atteints, car l'éditeur n'a pas ces droits.
4. **Restauration longue** : faute de test de restauration documenté (H07), la reconstruction du serveur et la réinstallation de l'ERP avec l'éditeur dépasseraient **une semaine** `[H]`.

**Biens supports concernés** : accès de télémaintenance de l'éditeur, serveurs d'application, modules Ventes et Facturation de l'ERP.

**Facteurs favorisants** : GAP03 (sauvegardes non testées), GAP05 (pas de supervision), GAP07 (pas de PCA/PRA), H17 (télémaintenance ouverte sans validation interne).

**Facteur limitant** : l'éditeur, plus mature (maturité 3), doit d'abord être compromis. La pénétration reste à 3, car les droits d'administration sur le serveur demeurent.

**Mesures de l'atelier 3** : ECO4 (télémaintenance à la demande, via le bastion, après validation interne).

**Mesures du PTR** : M07, M08, M15, M16.

---

### 3.3 SS3 - Rançongiciel via l'hameçonnage d'un salarié

| Champ | Valeur |
|---|---|
| **Code** | SS3 |
| **Couple SR/OV** | SR1/OV1 - Organisation criminelle (rançongiciel) / Gain financier par rançon |
| **Partie prenante** | *Aucune* : chemin direct, sans intermédiaire |
| **Valeur métier visée** | VM4 - Données comptables et financières |
| **ER atteints** | **ER6** (perte définitive des données, G4), **ER1** (ERP indisponible > 1 semaine, G3) |
| **Gravité** | 🔴 **G4** |
| **Risque final** | **R3** |

**Chemin d'attaque stratégique** :

1. **Hameçonnage d'un salarié** : un commercial nomade ou un comptable ouvre une pièce jointe ou un lien malveillant.
2. **Prise de contrôle du poste** : l'attaquant prend la main sur le poste de travail.
3. **Élévation de privilèges** : à partir du poste, il obtient des droits dans l'annuaire et atteint le niveau administrateur du domaine.
4. **Chiffrement** : il chiffre les serveurs ERP/CRM et les sauvegardes hébergées sur la même infrastructure (H08). Le chemin est direct : aucune partie prenante n'est nécessaire.

**Biens supports concernés** : personnel, postes de travail (ADV, portables des commerciaux), liaisons VPN, annuaire, serveurs d'application, base de données, système de sauvegarde.

**Facteurs favorisants** : GAP01 (pas de MFA), GAP03 (sauvegardes non testées), GAP04 (pas d'EDR), GAP05 (pas de supervision), GAP06 (correctifs non vérifiés), GAP07 (pas de PCA/PRA).

**Mesures de l'atelier 3** : *aucune* - le scénario est direct, sans partie prenante intermédiaire. Les mesures relèvent des biens supports.

**Mesures du PTR** : M05 (sensibilisation), M06 (MFA), M11 (durcissement annuaire), M12 (EDR), M13 (supervision), M15 (sauvegarde immuable), M16 (PCA/PRA), M19 (correctifs).

---

### 3.4 SS4 - Fraude au RIB

| Champ | Valeur |
|---|---|
| **Code** | SS4 |
| **Couple SR/OV** | SR2/OV2 - Organisation criminelle (fraude financière) / Détourner les paiements clients |
| **Partie prenante** | *Aucune* comme intermédiaire : la messagerie d'un salarié est compromise. Les **grands comptes** (PP6, zone veille) sont les **victimes** de la fraude, pas un point d'appui. |
| **Valeur métier visée** | VM3 - Facturation et recouvrement |
| **ER atteint** | **ER5** (fraude au RIB, G3) |
| **Gravité** | 🟠 **G3** |
| **Risque final** | **R4** |

**Chemin d'attaque stratégique** :

1. **Compromission d'une boîte de messagerie** : hameçonnage d'un comptable ou d'un commercial, sur une messagerie sans MFA (GAP01).
2. **Observation des échanges** : l'attaquant surveille les échanges de facturation et repère les grands comptes, les montants et les RIB.
3. **Fausse facture ou faux changement de RIB** : il envoie de fausses factures ou un faux changement de RIB aux grands comptes, ou modifie le RIB dans l'ERP avec le compte volé.
4. **Paiement par le client** : les grands comptes paient sur le compte de l'attaquant. Ils sont les **victimes** de la fraude, pas un intermédiaire.

**Biens supports concernés** : personnel, messagerie, postes de la comptabilité, module Facturation de l'ERP.

**Facteurs favorisants** : GAP01 (pas de MFA sur la messagerie), GAP13 (aucune vérification des changements de RIB, clients jamais informés).

**Mesures de l'atelier 3** : ECO5 (courrier aux grands comptes : Rhénalis ne change jamais de RIB par e-mail).

**Mesures du PTR** : M05 (sensibilisation), M06 (MFA), M10 (courrier), M17 (cyber-assurance), M18 (double validation des RIB).

---

### 3.5 SS5 - Export du fichier clients par un commercial

| Champ | Valeur |
|---|---|
| **Code** | SS5 |
| **Couple SR/OV** | SR3/OV3 - Collaborateur malveillant (commercial sur le départ) / Emporter le fichier clients et les tarifs |
| **Partie prenante** | *Aucune* : le commercial utilise ses **droits légitimes** sur le CRM |
| **Valeur métier visée** | VM2 - Fichier clients et prospects |
| **ER atteint** | **ER3** (vol et divulgation du fichier clients, G3) |
| **Gravité** | 🟠 **G3** |
| **Risque final** | **R5** |

**Chemin d'attaque stratégique** :

1. **Accès légitime au CRM** : le commercial se connecte avec ses propres identifiants. Aucune effraction n'est nécessaire.
2. **Repérage du fichier clients et des tarifs** : il identifie les données de valeur (fichier clients, conditions tarifaires négociées).
3. **Export massif** : il exporte tout le fichier clients et les tarifs, grâce à des droits trop larges (GAP08).
4. **Sortie des données** : il les copie sur une clé USB ou les envoie vers une messagerie personnelle avant son départ.

**Biens supports concernés** : personnel, application CRM, base de données, portables des commerciaux.

**Facteurs favorisants** : GAP08 (droits d'export trop larges, exports et supports USB non contrôlés), GAP09 (registre RGPD incomplet).

**Mesures de l'atelier 3** : *aucune* - le scénario est direct, sans partie prenante intermédiaire. Les mesures relèvent des biens supports.

**Mesures du PTR** : M03 (registre RGPD), M09 (restriction des exports, revue des droits, blocage USB), M14 (alerte sur les exports volumineux).

---

## 4. Rattachement aux ER et aux risques

### 4.1 Tableau de correspondance ER → SS → R

| ER | Gravité | Scénario(s) stratégique(s) | Risque(s) final(aux) |
|:-:|:-:|:-:|:-:|
| **ER6** - Perte définitive des données | 🔴 G4 | SS1, SS3 | **R1, R3** |
| **ER1** - ERP indisponible > 1 semaine | 🟠 G3 | SS1, SS2, SS3 | **R1, R2, R3** |
| **ER3** - Vol du fichier clients | 🟠 G3 | SS1, SS5 | **R1, R5** |
| **ER5** - Fraude au RIB | 🟠 G3 | SS4 | **R4** |
| **ER2, ER4, ER7** | 🟡 G2 | *Non retenus en scénario stratégique* | - |

> Un même ER peut être atteint par **plusieurs scénarios** (ER6 par SS1 et SS3, ER1 par SS1, SS2 et SS3, ER3 par SS1 et SS5). La synthèse des risques de l'atelier 5 agrège ces chemins en cinq risques R1 à R5.

### 4.2 Les cinq risques finaux

| Risque | Description | SS | Gravité | Vraisemblance | Niveau initial |
|:-:|---|:-:|:-:|:-:|:-:|
| **R1** | Perte définitive des données de gestion, via l'infogérant | SS1 | G4 | V3 | 🔴 **Élevé** |
| **R2** | ERP indisponible > 1 semaine, via l'éditeur | SS2 | G3 | V2 | 🟡 **Modéré** |
| **R3** | Perte définitive des données de gestion, à partir d'un salarié | SS3 | G4 | V3 | 🔴 **Élevé** |
| **R4** | Détournement de paiements clients (fraude au RIB) | SS4 | G3 | V3 | 🟡 **Modéré** |
| **R5** | Départ d'un commercial avec le fichier clients | SS5 | G3 | V3 | 🟡 **Modéré** |

> La cotation de la **vraisemblance** est traitée dans l'atelier 4 (méthode expresse). La synthèse des risques et les niveaux initiaux sont détaillés dans [`05_atelier5_traitement/A5_synthese_risques.md`](../05_atelier5_traitement/A5_synthese_risques.md).

---

## 5. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Codes SS1 à SS5 | `Atelier 3 - SS` | Colonne A |
| Source de risque / objectif visé | `Atelier 3 - SS` | Colonne B |
| Chemin d'attaque stratégique | `Atelier 3 - SS` | Colonne C |
| Gravité | `Atelier 3 - SS` | Colonne D |
| Support graphique SS1 | `Atelier 3 - SS1` | Feuille vide, ne pas modifier |
| Risques finaux | `Atelier 5 - Risques` | Colonnes A à L |

---

## 6. Checklist de validation

- [x] Les **5 scénarios stratégiques** de la feuille `Atelier 3 - SS` sont repris et décrits.
- [x] Chaque SS est relié à un **couple SR/OV retenu** de l'atelier 2.
- [x] Chaque SS est relié à un ou plusieurs **ER** de l'atelier 1, avec leur gravité.
- [x] Chaque SS identifie les **parties prenantes** traversées (ou l'absence d'intermédiaire).
- [x] Les scénarios **G4** (SS1, SS3) sont distingués des scénarios **G3** (SS2, SS4, SS5).
- [x] Les **chemins directs** (SS3, SS4, SS5) sont identifiés comme tels.
- [x] Le rôle des **grands comptes comme victimes** dans SS4 est explicité.
- [x] Les **facteurs favorisants** (GAP de l'atelier 1) sont cités pour chaque SS.
- [x] Les **mesures de l'atelier 3** (ECO1 à ECO5) sont rattachées aux SS concernés.
- [x] Les **mesures du PTR** sont citées pour chaque SS.
- [x] Les scénarios sont **cohérents avec les risques R1 à R5** de l'atelier 5.
- [x] La **cartographie** des scénarios est produite (page 11 du dossier de synthèse).

---

## 7. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Scénarios stratégiques » (atelier 3).
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Atelier 3 - SS`, `Atelier 3 - SS1`.
- Dossier de synthèse - § 5.3 « Scénarios stratégiques » (pages 11-12) et figure page 11.
- Fiche amont : [`A3_parties_prenantes.md`](./A3_parties_prenantes.md).
- Fiche associée : [`A3_mesures_ecosysteme.md`](./A3_mesures_ecosysteme.md).
- Fiche aval : [`04_atelier4_scenarios_operationnels/A4_scenarios_operationnels.md`](../04_atelier4_scenarios_operationnels/A4_scenarios_operationnels.md).