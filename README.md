# README - Analyse EBIOS Risk Manager

### Appréciation et traitement du risque cyber de la plateforme cloud ERP/CRM de **Rhénalis SAS**

[![Formation](https://img.shields.io/badge/Formation-BUT_3_Cybersécurité-blue.svg)](#)
[![Année](https://img.shields.io/badge/Année_Universitaire-2026--2027-orange.svg)](#)
[![Méthode](https://img.shields.io/badge/Méthode-EBIOS_RM_v1.5-red.svg)](#)
[![Norme](https://img.shields.io/badge/Norme-ISO%2FIEC_27005%3A2022-green.svg)](#)

---

## 1. Objet de l'étude

| Élément | Description |
|---|---|
| **Objet étudié** | Plateforme cloud hébergeant l'ERP et le CRM de **Rhénalis SAS** - PME de distribution B2B de matériel électrique |
| **Périmètre technique** | Postes de travail (~75), serveurs d'application (ERP/CRM), base de données, annuaire Active Directory, sauvegardes, prestataire d'infogérance (InfoGest Services) |
| **Périmètre fonctionnel** | Processus métier supportés par l'ERP et le CRM : ventes, achats, stocks, facturation, relation client, comptabilité |
| **Hors périmètre** | Paie/RH, site vitrine, équipements d'entrepôt, hébergement physique (relève de l'hébergeur IaaS) |
| **Cadre temporel** | 19/10/2026 – 24/10/2026 · PTR sur 12 mois (échéance 31/10/2027) |
| **Méthode** | EBIOS Risk Manager v1.5 (ANSSI, mars 2024) - conforme ISO/IEC 27005:2022 |

---


## 2. Structure du dossier de rendu

```
/rendu_EBIOS_RM_Rhenalis/
│
├── README.md                          ← ce fichier
├── EBIOS_RM_Ateliers_modele.xlsx      ← classeur complété (livrable principal)
│
├── 00_cadrage/
│   ├── fiche_objet_etude.md           ← objet, périmètre, cadre temporel
│   └── matrice_participants.png       ← capture feuille « Organisation »
│
├── 01_atelier1_cadrage_socle/
│   ├── A1_perimetre_metier_technique.md
│   ├── A1_evenements_redoutes.md
│   ├── A1_socle_securite_gaps.md
│   └── captures/
│       ├── A1_missions.png
│       ├── A1_ER.png
│       └── A1_GAP.png
│
├── 02_atelier2_sources_risque/
│   ├── A2_couples_SR_OV.md            ← tableau + justifications de sélection
│   ├── A2_cartographie_SR.png
│   └── captures/
│       └── A2_SROV.png
│
├── 03_atelier3_scenarios_strategiques/
│   ├── A3_parties_prenantes.md        ← cotations + indice de menace
│   ├── A3_scenarios_strategiques.md   ← SS1 à SS5 avec chemin d'attaque
│   ├── A3_mesures_ecosysteme.md
│   └── captures/
│       ├── A3_PP.png
│       └── A3_carto_PP.png            ← cartographie radar avant/après
│
├── 04_atelier4_scenarios_operationnels/
│   ├── A4_scenarios_operationnels.md  ← SO1 à SO5 en 4 phases
│   ├── A4_vraisemblance.md            ← méthode expresse + cotation
│   └── captures/
│       └── A4_graphes_attaque.png
│
├── 05_atelier5_traitement/
│   ├── A5_synthese_risques.md         ← R1 à R5, niveau de risque
│   ├── A5_PTR.md                      ← 19 actions SMART, 4 groupes
│   ├── A5_risques_residuels.md
│   ├── A5_cadre_suivi.md
│   └── captures/
│       ├── A5_carto_risque_initial.png
│       └── A5_carto_risque_residuel.png
│
├── annexes/
│   ├── glossaire.md                   ← VM, BS, ER, SR, OV, PP, SS, SO, PTR
│   └── references.md                  ← liens ANSSI, EBIOS RM, MITRE ATT&CK
│
├── soutenance.pdf / .pptx             ← support oral
└── dossier_synthese.pdf               ← Dossier de synthèse global (23 pages)
```

---

## 3. Synthèse des résultats

### 3.1 Valeurs métier et biens supports (Atelier 1)

**5 valeurs métier** identifiées : VM1 (commandes), VM2 (fichier clients), VM3 (facturation), VM4 (comptabilité), VM5 (stocks).
**18 biens supports** recensés, dont **4 transverses critiques** : annuaire AD, base de données, sauvegardes, accès d'administration - **tous administrés par InfoGest Services**.
**13 écarts de conformité** relevés sur 6 référentiels (hygiène ANSSI, RGPD, Code de commerce, contrat d'infogérance, contrat d'hébergement, contrôle interne).

### 3.2 Sources de risque retenues (Atelier 2)

**3 couples SR/OV retenus** sur 8 évalués :
- **SR1 / OV1** - Crime organisé (rançongiciel) - gain financier
- **SR2 / OV2** - Crime organisé (fraude financière) - détournement de paiements
- **SR3 / OV3** - Collaborateur malveillant (commercial sur le départ) - exfiltration du fichier clients

**5 couples exclus** (SR4 à SR8), justifiés dans `A2_couples_SR_OV.md`.

### 3.3 Écosystème (Atelier 3)

**9 parties prenantes** cotées - indice de menace = (dépendance × pénétration) / (maturité × confiance).

| Zone | Parties prenantes | Indices |
|---|---|---|
| 🔴 **Danger** | InfoGest Services (infogérant) | 4,00 |
| 🟠 **Contrôle** | Hébergeur IaaS · Éditeur de l'ERP | 1,78 · 1,33 |
| 🟢 **Veille** | 6 PP (transporteurs, cabinet comptable, grands comptes, PDP, messagerie, banque) | 0,19 à 0,67 |

**5 scénarios stratégiques** (SS1 à SS5), dont 2 passant par un tiers (SS1 via l'infogérant, SS2 via l'éditeur) et 3 directs (SS3, SS4, SS5).

### 3.4 Scénarios opérationnels (Atelier 4)

**5 scénarios SO1 à SO5** structurés en 4 phases (Connaître / Rentrer / Trouver / Exploiter), cotés en **méthode expresse** (V1 à V4).

| Code | Scénario | Vraisemblance |
|---|---|---|
| SO1 | Rançongiciel via l'infogérant | **V3** |
| SO2 | Rançongiciel via l'éditeur de l'ERP | V2 |
| SO3 | Rançongiciel via hameçonnage d'un salarié | **V3** |
| SO4 | Fraude au RIB | **V3** |
| SO5 | Export du fichier clients par un commercial | **V3** |

### 3.5 Synthèse des risques (Atelier 5)

| Code | Risque | G | V | Niveau initial | Niveau résiduel |
|---|---|:-:|:-:|---|---|
| **R1** | Perte définitive des données via l'infogérant | G4 | V3 | 🔴 **Élevé** | 🟠 Modéré |
| **R2** | ERP indisponible > 1 semaine via l'éditeur | G3 | V2 | 🟠 Modéré | 🟡 Significatif |
| **R3** | Perte définitive des données via un salarié | G4 | V3 | 🔴 **Élevé** | 🟠 Modéré |
| **R4** | Fraude au RIB | G3 | V3 | 🟠 Modéré | 🟠 Modéré |
| **R5** | Départ d'un commercial avec le fichier clients | G3 | V3 | 🟠 Modéré | 🟠 Modéré |

### 3.6 Plan de traitement du risque (PTR)

**19 actions** réparties en 4 groupes de la défense en profondeur :

| Groupe | Nombre | Exemples |
|---|:-:|---|
| **Gouvernance** | 6 | M01 avenant infogérance · M02 PSSI · M10 courrier RIB |
| **Protection** | 7 | M06 MFA · M07 bastion · M09 restriction exports CRM |
| **Défense** | 3 | M12 EDR · M13 SOC managé · M14 alerte exports |
| **Résilience** | 3 | M15 sauvegarde immuable · M16 PCA/PRA · M17 cyber-assurance |

**9 actions prioritaires (P1)**, dont 4 à coût quasi nul (M10, M18, M19, M04).

**Budget estimé** [H] : ~33 k€ d'investissement + ~51 à 56 k€/an de fonctionnement, soit **~0,4 % du CA la 1ʳᵉ année** (22 M€), puis ~0,25 %/an.

### 3.7 Décisions attendues de la direction

- ✅ Valider le plan de traitement du risque et son budget.
- ✅ Mandater le DAF pour renégocier le contrat d'infogérance (**M01**) avant fin janvier 2027.
- ✅ Désigner formellement un référent sécurité et instaurer un comité sécurité trimestriel.
- ✅ **Accepter explicitement les risques résiduels** R1, R3, R4 et R5 (tous modérés après traitement).

---

## 4. Livrables et pondération

| Atelier | Livrable | Pondération |
|---|---|:-:|
| **A1** - Cadrage & socle | Périmètre documenté, ER cotés, écarts de conformité | **20 %** |
| **A2** - Sources de risque | Couples SR/OV retenus et justifiés | **15 %** |
| **A3** - Scénarios stratégiques | Cartographie PP + SS cotés + mesures écosystème | **20 %** |
| **A4** - Scénarios opérationnels | Graphes d'attaque 4 phases + vraisemblance | **20 %** |
| **A5** - Traitement | Synthèse risques, PTR SMART, résiduel, suivi | **20 %** |
| **Restitution orale** | Clarté, argumentation, priorisation budgétaire | **5 %** |

---

## 5. Mode opératoire - démarrage rapide

1. **Ouvrir** `EBIOS_RM_Ateliers_modele.xlsx` avec **macros activées** (Excel ou LibreOffice Calc). Les feuilles de calcul automatique (indice de menace, cartographies) requièrent les macros.
2. **Ne pas renommer** ni **supprimer** de feuilles. Ne pas modifier les formules.
3. Lire **dans l'ordre** : `00_cadrage/` → `01_atelier1/` → `02_atelier2/` → `03_atelier3/` → `04_atelier4/` → `05_atelier5/`.
4. **Sauvegarder au format `.xlsm`** (le format `.xlsx` supprime les macros).
5. Consulter `dossier_synthese.pdf` (23 pages) pour la vue consolidée et `annexes/glossaire.md` pour le vocabulaire EBIOS RM.

---

## 6. Échelles de cotation

### 6.1 Gravité

| Niveau | Définition (échelle ANSSI) |
|---|---|
| **G1** - Mineure | Conséquences négligeables, aucun impact opérationnel |
| **G2** - Significative | Mode dégradé, difficultés surmontables |
| **G3** - Grave | Mode très dégradé, sérieuses difficultés |
| **G4** - Critique | Survie de l'organisation menacée |
| **G5** - Catastrophique | Conséquences sectorielles *(non utilisé dans ce TP)* |

### 6.2 Vraisemblance

| Niveau | Définition |
|---|---|
| **V1** - Peu vraisemblable | Très peu de chance d'atteindre l'objectif |
| **V2** - Vraisemblable | Susceptible d'atteindre l'objectif |
| **V3** - Très vraisemblable | Va probablement atteindre l'objectif |
| **V4** - Quasi-certain | Va certainement atteindre l'objectif |

### 6.3 Niveaux de risque (feuille Métriques)

Du plus haut au plus bas : **Élevé (4)** > **Modéré (3)** > **Significatif (2)** > **Faible (1)**.

### 6.4 Besoins de sécurité D-I-C-T

Niveaux 1 à 4 pour **D**isponibilité, **I**ntégrité, **C**onfidentialité, **T**raçabilité.

---

## 7. Limites de l'analyse

- **Cas fictif** : hormis l'objet d'étude et ses composants, tout repose sur les **23 hypothèses** du journal en annexe A du dossier de synthèse. Aucune n'a été vérifiée auprès d'un interlocuteur réel.
- **Écarts de sécurité supposés, non audités** : les vérifier (tests de restauration, configuration des accès distants, revue des droits du CRM) serait la première étape d'une mission réelle.
- **Vraisemblance en méthode expresse** : une cotation action par action (méthode standard) donnerait un résultat plus fin, en particulier pour les chaînes longues.
- **Coûts et délais = ordres de grandeur**, non des devis. Le budget sert à situer l'effort, pas à engager la dépense.
- **2 informations manquantes bloquent une conclusion ferme** : le dernier compte rendu de test de restauration (**H07**) et le niveau de qualification de l'hébergeur (**H14**). La cotation de R1 dépend directement de H07.

---

## 8. Références

- **ANSSI** - *EBIOS Risk Manager*, guide et fiches méthodes des ateliers 1 à 5 : [EBIOS RM](https://messervices.cyber.gouv.fr/guides/la-methode-ebios-risk-manager-le-guide)
- **ANSSI** - *Guide d'hygiène informatique* (42 mesures)
- **Classeur modèle officiel** `EBIOS_RM_Ateliers_modele.xlsx`
- **MITRE ATT&CK** - cadre de référence pour les scénarios opérationnels : [attack.mitre.org](https://attack.mitre.org)
- **ISO/IEC 27005:2022** - management du risque lié à la sécurité de l'information
- **RGPD** - règlement UE 2016/679

---