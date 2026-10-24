# Références

> **Annexe - Références et sources**  
> Dossier parent : [`README.md`](../README.md) · Fiche associée : [`glossaire.md`](./glossaire.md)

---

## 1. Objet

Cette annexe recense les références utilisées pour conduire l'analyse EBIOS Risk Manager de la plateforme cloud ERP/CRM de Rhénalis SAS. Elle distingue les **référentiels méthodologiques**, les **référentiels réglementaires**, les **cadres techniques** et les **sources documentaires internes** au rendu.

---

## 2. Référentiels méthodologiques

### 2.1 EBIOS Risk Manager

| Référence | Description | Lien |
|---|---|---|
| **ANSSI - EBIOS Risk Manager, guide méthodologique** | Guide officiel de la méthode, version 1.5 (mars 2024) | [cyber.gouv.fr](https://messervices.cyber.gouv.fr/guides/la-methode-ebios-risk-manager-le-guide) |
| **ANSSI - Fiche méthode atelier 1** | Définir le périmetre metier et technique | [cyber.gouv.fr](https://messervices.cyber.gouv.fr/documents-guides/Fiche_methode-Identifier_le_perimetre_metier_et_technique-atelier_1.pdf) |
| **ANSSI - Fiche méthode atelier 2** | Identifier et caracteriser les sources de risque | [cyber.gouv.fr](https://messervices.cyber.gouv.fr/documents-guides/Fiche_methode-Identifier_et_caracteriser_les_sources_de_risque-atelier_2.pdf) |
| **ANSSI - Fiche méthode atelier 3** | Scénarios stratégiques et écosystème | [cyber.gouv.fr](https://messervices.cyber.gouv.fr/documents-guides/Fiche_methode-Construire_lestimation_de_la_dangerosite_des_parties_prenantes_de_l_ecosysteme-atelier_3.pdf) |
| **ANSSI - Fiche méthode atelier 4** | Scénarios opérationnels et vraisemblance | [cyber.gouv.fr](https://messervices.cyber.gouv.fr/documents-guides/Fiche_methode-Scenarios_operationnels_et_vraisemblance-atelier_4.pdf) |
| **ANSSI - Fiche méthode atelier 5** | Traitement du risque et cadre de suivi | [cyber.gouv.fr](https://messervices.cyber.gouv.fr/documents-guides/Fiche_methode-Structurer_les_mesures_de_traitement_du_risque-atelier_5.pdf) |

> La méthode EBIOS RM v1.5 est **conforme à ISO/IEC 27005:2022** pour le management du risque lié à la sécurité de l'information.

### 2.2 Normes internationales

| Référence | Description | Lien |
|---|---|---|
| **ISO/IEC 27005:2022** | Management du risque lié à la sécurité de l'information | [ISO/IEC 27005:2022](https://www.karlancer.com/api/file/1683114859-CH6u.pdf) |
| **ISO/IEC 27001:2022** | Systèmes de management de la sécurité de l'information — Exigences | [iso.org](https://www.iso.org/fr/standard/88435.html) |
| **ISO/IEC 27002:2022** | Mesures de sécurité de l'information | [iso.org](https://www.iso.org/fr/standard/75652.html) |

> L'analyse EBIOS RM de cette étude s'appuie sur les concepts d'ISO/IEC 27005:2022 (risque, gravité, vraisemblance, traitement, acceptation).

---

## 3. Référentiels réglementaires

### 3.1 Protection des données personnelles

| Référence | Description | Lien |
|---|---|---|
| **RGPD - Règlement UE 2016/679** | Règlement général sur la protection des données | [eur-lex.europa.eu](https://eur-lex.europa.eu/eli/reg/2016/679/oj/fra) |
| **CNIL - Guide de la sécurité des données personnelles** | Bonnes pratiques pour la protection des données | [cnil.fr](https://www.cnil.fr/fr/guide-de-la-securite-des-donnees-personnelles) |
| **CNIL - Notification de violation** | Procédure de notification sous 72 h | [cnil.fr](https://www.cnil.fr/fr/services-en-ligne/notifier-une-violation-de-donnees-personnelles) |

> Le RGPD est mobilisé dans l'étude pour le fichier clients (VM2) : registre des traitements, notification de violation, droits des personnes. C'est l'écart **GAP09**.

### 3.2 Obligations comptables et fiscales

| Référence | Description | Lien |
|---|---|---|
| **Code de commerce** | Obligation de conservation des pièces comptables pendant 10 ans | [L123-22](https://www.legifrance.gouv.fr/codes/article_lc/LEGIARTI000006219327/) |
| **Livre des procédures fiscales** | Obligations de conservation des documents fiscaux | [L102](https://www.legifrance.gouv.fr/codes/article_lc/LEGIARTI000041471233/) |
| **Réforme de la facturation électronique** | Obligation de dématérialisation des factures | [impots.gouv.fr](https://www.impots.gouv.fr/depliant-la-facturation-electronique-en-4-questions) |

> Ces obligations sont mobilisées pour VM3 (facturation) et VM4 (comptabilité). Elles fondent le besoin **T4** (traçabilité légale) de l'ER6 et l'écart **GAP10**.

### 3.3 Qualification des fournisseurs cloud

| Référence | Description | Lien |
|---|---|---|
| **SecNumCloud** | Qualification ANSSI des fournisseurs de services cloud | [SecNumCloud-Anssi](https://cyber.gouv.fr/enjeux-technologiques/cloud/) |
| **Directive NIS 2** | Directive européenne sur la sécurité des réseaux et des systèmes d'information | [eur-lex.europa.eu](https://eur-lex.europa.eu/eli/dir/2022/2555/oj?locale=fr) |

> SecNumCloud est mobilisé pour la vérification de l'hébergeur IaaS (écart **GAP12**, information manquante **H14**). NIS 2 n'est pas directement applicable à Rhénalis, mais peut le devenir si l'activité évolue.

---

## 4. Cadres techniques

### 4.1 MITRE ATT&CK

| Référence | Description | Lien |
|---|---|---|
| **MITRE ATT&CK** | Base de connaissances des tactiques et techniques d'attaque | [attack.mitre.org](https://attack.mitre.org) |
| **MITRE ATT&CK - Enterprise** | Techniques visant les systèmes d'entreprise | [attack.mitre.org/matrices/enterprise/](https://attack.mitre.org/matrices/enterprise/) |

> MITRE ATT&CK est utilisé comme **cadre de référence** pour les scénarios opérationnels de l'atelier 4. Les quatre phases de l'ANSSI (Connaître, Rentrer, Trouver, Exploiter) sont **cohérentes** avec les tactiques ATT&CK (Reconnaissance, Initial Access, Privilege Escalation / Lateral Movement, Impact / Exfiltration), sans s'y substituer.

### 4.2 Bonnes pratiques ANSSI

| Référence | Description | Lien |
|---|---|---|
| **ANSSI - Guide d'hygiène informatique (42 mesures)** | Mesures de base pour la sécurité d'un SI | [Guide d'hygiène informatique](https://messervices.cyber.gouv.fr/documents-guides/guide_hygiene_informatique_anssi.pdf) |
| **ANSSI - Recommandations relatives à l'authentification multifacteur** | Bonnes pratiques MFA | [Recommandations relatives à l'authentification multifacteur](https://messervices.cyber.gouv.fr/guides/recommandations-relatives-lauthentification-multifacteur-et-aux-mots-de-passe) |
| **ANSSI - Recommandations sur le télétravail** | Sécurité des accès distants | [Recommandations sur le nomadisme numérique](https://messervices.cyber.gouv.fr/guides/recommandations-sur-le-nomadisme-numerique) |
| **ANSSI - Recommandations de sécurité pour l’architecture d’un système de journalisation** | Bonnes pratiques de journalisation | [Recommandations de sécurité pour l’architecture d’un système de journalisation](https://messervices.cyber.gouv.fr/guides/recommandations-de-securite-pour-larchitecture-dun-systeme-de-journalisation) |
| **ANSSI - Recommandations sur les sauvegardes** | Bonnes pratiques de sauvegarde, test de restauration | [Sauvegarde des systèmes d’information](https://messervices.cyber.gouv.fr/guides/fondamentaux-sauvegarde-systemes-dinformation) |

> Le guide d'hygiène informatique est mobilisé pour huit écarts (GAP01 à GAP08). Les recommandations sur les sauvegardes fondent l'écart **GAP03** et la mesure **M15**.

---

## 5. Sources documentaires internes

### 5.1 Documents du rendu

| Document | Description | Emplacement |
|---|---|---|
| **README.md** | Présentation du rendu, consignes, structure du dossier | Racine |
| **EBIOS_RM_Classeur.xlsx** | Classeur EBIOS RM complété (livrable principal) | Racine |
| **Dossier de synthèse** | Compilation des fiches d'atelier (23 pages) | `dossier_synthese.pdf` |
| **Support de soutenance** | Présentation orale | `soutenance.pptx` |

### 5.2 Fiches d'atelier

| Fiche | Atelier | Emplacement |
|---|---|---|
| `A1_perimetre_metier_technique.md` | A1 - Périmètre métier et technique | `01_atelier1_cadrage_socle/` |
| `A1_evenements_redoutes.md` | A1 - Événements redoutés | `01_atelier1_cadrage_socle/` |
| `A1_socle_securite_gaps.md` | A1 - Socle de sécurité et écarts | `01_atelier1_cadrage_socle/` |
| `A2_couples_SR_OV.md` | A2 - Couples SR/OV | `02_atelier2_sources_risque/` |
| `A3_parties_prenantes.md` | A3 - Parties prenantes | `03_atelier3_scenarios_strategiques/` |
| `A3_scenarios_strategiques.md` | A3 - Scénarios stratégiques | `03_atelier3_scenarios_strategiques/` |
| `A3_mesures_ecosysteme.md` | A3 - Mesures sur l'écosystème | `03_atelier3_scenarios_strategiques/` |
| `A4_scenarios_operationnels.md` | A4 - Scénarios opérationnels | `04_atelier4_scenarios_operationnels/` |
| `A4_vraisemblance.md` | A4 - Vraisemblance | `04_atelier4_scenarios_operationnels/` |
| `A5_synthese_risques.md` | A5 - Synthèse des risques | `05_atelier5_traitement/` |
| `A5_PTR.md` | A5 - Plan de traitement du risque | `05_atelier5_traitement/` |
| `A5_risques_residuels.md` | A5 - Risques résiduels | `05_atelier5_traitement/` |
| `A5_cadre_suivi.md` | A5 - Cadre de suivi | `05_atelier5_traitement/` |

### 5.3 Annexes

| Fiche | Description | Emplacement |
|---|---|---|
| `glossaire.md` | Glossaire des termes | `annexes/` |
| `references.md` | Références (ce document) | `annexes/` |

---

## 6. Le cas fictif Rhénalis SAS

| Élément | Statut | Source |
|---|---|---|
| **Nom de l'organisation** | Fictif | Énoncé du TP |
| **Activité (distribution B2B de matériel électrique)** | Fictif | Énoncé du TP |
| **Objet de l'étude (plateforme cloud ERP/CRM)** | Fictif | Énoncé du TP |
| **Périmètre technique (postes, serveurs, base de données, annuaire, sauvegardes, infogérance)** | Fictif | Énoncé du TP |
| **Chiffre d'affaires (22 M€)** | Hypothèse `[H]` | H01 |
| **Nombre de salariés (90)** | Hypothèse `[H]` | H01 |
| **Implantation (Colmar, Mulhouse)** | Hypothèse `[H]` | H01 |
| **Noms des personnes (Claire Muller, Sophie Haas, Thomas Weber, Julien Roth, Laura Meyer)** | Fictifs | Énoncé du TP |
| **InfoGest Services (infogérant)** | Fictif | Énoncé du TP |

> **Avertissement** : toutes les données de ce dossier sont **fictives**. Les éléments ajoutés par le groupe sont signalés comme hypothèses `[H]`, déclarations `[D]` ou informations manquantes `[M]`. Seuls les éléments fournis par le sujet sont des **faits établis** `[F]`.

---

## 7. Avertissement

> Ce travail s'appuie sur le référentiel EBIOS RM de l'ANSSI ; il **ne se substitue pas** aux guides techniques, politiques de sécurité et réglementations en vigueur. Les conclusions de l'analyse ne valent que dans le cadre posé : cas fictif, hypothèses de travail non vérifiées, absence de données historiques.

---

## 8. Références croisées

| Fiche | Référence |
|---|---|
| [`glossaire.md`](./glossaire.md) | Glossaire des termes |
| [`../README.md`](../README.md) | Présentation du rendu |
