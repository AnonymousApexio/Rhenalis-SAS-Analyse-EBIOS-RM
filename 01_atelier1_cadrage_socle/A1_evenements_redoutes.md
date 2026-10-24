# A1 - Événements redoutés et gravité

> **Atelier 1 - Étape 1.3 : Événements redoutés**
> Feuille du classeur : `Atelier 1 - ER` (+ échelles de la feuille `Métriques`)
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`A1_perimetre_metier_technique.md`](./A1_perimetre_metier_technique.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS  |
| **Atelier** | Atelier 1 - Cadrage et socle de sécurité |
| **Étape** | 1.3 - Identification et cotation des événements redoutés |
| **Livrable** | Tableau des ER cotés en gravité, reliés aux besoins D-I-C-T |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - Un **événement redouté (ER)** est ce que l'on cherche à éviter pour une valeur métier donnée. Il se cote par sa **gravité** (impact métier) et se rattache aux **besoins de sécurité** D-I-C-T de la feuille `Métriques`.

---

## 2. Échelles de cotation (rappel - feuille `Métriques`)

### 2.1 Échelle de gravité

| Niveau | Définition (échelle ANSSI) |
|---|---|
| **G4 - Critique** | Incapacité pour la société d'assurer tout ou partie de son activité, avec d'éventuels impacts graves sur la sécurité des personnes et des biens. La société ne surmontera vraisemblablement pas la situation (**survie menacée**). |
| **G3 - Grave** | Forte dégradation des performances de l'activité, avec d'éventuels impacts significatifs. La société surmontera la situation **avec de sérieuses difficultés** (mode très dégradé). |
| **G2 - Significative** | Dégradation des performances de l'activité sans impact sur la sécurité des personnes et des biens. La société surmontera la situation **malgré quelques difficultés** (mode dégradé). |
| **G1 - Mineure** | Aucun impact opérationnel. La société surmontera la situation **sans trop de difficultés** (consommation des marges). |

> ⚠️ **Note de lecture** : l'échelle du classeur ne comporte que **4 niveaux** (G1 à G4). Le guide méthodologique mentionne une échelle à 5 niveaux (jusqu'à G5 - Catastrophique) pour les crises majeures ; cette étude utilise l'échelle à 4 niveaux du classeur modèle.

### 2.2 Besoins de sécurité D-I-C-T (niveaux 1 à 4)

| Niveau | Disponibilité (D) | Intégrité (I) | Confidentialité (C) | Traçabilité (T) |
|:-:|---|---|---|---|
| **1** | Pas de disponibilité requise | Pas d'intégrité nécessaire | Le bien est accessible publiquement | Pas de traçabilité nécessaire |
| **2** | Le bien ne peut être indisponible plus d'**une semaine** | L'intégrité doit être **connue** | L'accès doit être limité aux **employés** uniquement | Traçabilité nécessaire pour des besoins **qualité ou techniques** |
| **3** | Le bien ne peut être indisponible plus d'**une journée** | L'intégrité doit être **connue et récupérable** | L'accès doit être limité à un **groupe restreint** d'employés | Traçabilité nécessaire pour des besoins **métier ou contractuels** |
| **4** | Le bien ne peut être indisponible plus d'**une heure** | L'intégrité doit être **garantie** | L'accès doit être **interdit pour tous** | Traçabilité nécessaire pour des besoins **légaux ou réglementaires** |

---

## 3. Tableau des événements redoutés

| Code | Valeur métier | Événement redouté | Impact métier | Besoin D-I-C-T | Gravité |
|:-:|---|---|---|:-:|:-:|
| **ER1** | VM1 - Prise et traitement des commandes clients | Impossibilité de prendre et traiter les commandes **pendant plus d'une semaine** (ERP indisponible, par exemple après un chiffrement par rançongiciel) | Arrêt d'environ **70 % des ventes**, soit **~300 k€ de CA par semaine** (70 % × 22 M€ / 52). Engagements de livraison J+1 non tenus, pénalités et perte de grands comptes au profit de concurrents. Mode dégradé papier tenable **1 journée seulement** (H03). La société survit mais avec de sérieuses difficultés. | **D3** | 🟠 **G3** |
| **ER2** | VM1 - Prise et traitement des commandes clients | **Altération des commandes en cours** (quantités, prix, adresses de livraison modifiés) | Erreurs de livraison et de facturation, retours et litiges, temps de contrôle manuel. Erreurs détectables et corrigeables : dégradation de l'activité sans mise en danger de la société. | **I3** | 🟡 **G2** |
| **ER3** | VM2 - Fichier clients et prospects | **Vol et divulgation du fichier clients et prospects** (exfiltration puis revente ou publication) | **Violation de données personnelles** : notification à la CNIL sous 72 h, sanction possible. Tarifs négociés exposés aux concurrents, perte de confiance des clients et démarchage ciblé par la concurrence. Atteinte durable à l'image et à la position commerciale. | **C3** | 🟠 **G3** |
| **ER4** | VM3 - Facturation et recouvrement | **Interruption de l'émission des factures et du suivi des encaissements** pendant plus de 2 semaines | Retard d'encaissement d'environ **850 k€** (2 semaines de CA), tension de trésorerie. Non-respect possible des obligations de facturation. Les factures sont décalées et non perdues : rattrapage possible, mode dégradé. | **D2** | 🟡 **G2** |
| **ER5** | VM3 - Facturation et recouvrement | **Modification frauduleuse des coordonnées bancaires** sur les factures émises (**fraude au RIB**) | Paiements clients détournés vers le compte de l'attaquant, potentiellement **plusieurs centaines de k€** avant détection. Litiges avec les clients qui ont payé de bonne foi, perte financière souvent non récupérable. | **I4** | 🟠 **G3** |
| **ER6** | VM4 - Données comptables et financières | **Perte définitive des données comptables et de gestion** (base de données chiffrée ou détruite, sauvegardes inutilisables) | Impossible de reconstituer les comptes clients, les encours, les stocks et la comptabilité. **Manquement à l'obligation légale de conservation (10 ans)**, comptes annuels non établis, créances non recouvrables. **Survie de la société menacée.** Cotation dépendante de H07-H08 (aucun test de restauration documenté, pas de copie hors ligne). | **I4 + T4** | 🔴 **G4** |
| **ER7** | VM5 - Gestion des stocks et approvisionnements | **Indisponibilité de la gestion des stocks et des commandes fournisseurs** pendant plus de 3 jours | Ruptures de stock, réapprovisionnements bloqués, inventaire manuel des 2 dépôts. Retards de livraison mais activité maintenue en mode dégradé. | **D2** | 🟡 **G2** |

### 3.1 Justification des cotations

| Code | Justification de la gravité | Justification du besoin D-I-C-T |
|:-:|---|---|
| **ER1** | 70 % du CA s'arrête dès la 1ère semaine ; le mode dégradé papier ne tient qu'**une journée** (H03) → sérieuses difficultés | **D3** : le bien ne peut être indisponible plus d'une journée |
| **ER2** | Altérations **détectables et corrigeables** → mode dégradé, pas de mise en danger | **I3** : l'intégrité doit être connue et récupérable |
| **ER3** | Violation RGPD + perte de confiance + exposition tarifaire → atteinte durable | **C3** : accès réservé à un groupe restreint (direction commerciale) |
| **ER4** | Factures **décalées et non perdues** ; rattrapage possible après 2 semaines | **D2** : une semaine tenable en mode dégradé |
| **ER5** | Pertes financières **non récupérables**, litiges clients | **I4** : l'intégrité du RIB doit être **garantie** |
| **ER6** | Perte **irréversible** + manquement légal + survie menacée | **I4 + T4** : intégrité garantie et traçabilité légale (conservation 10 ans) |
| **ER7** | Inventaire manuel possible quelques jours ; ruptures au-delà d'une semaine | **D2** : le seuil de 3 jours se situe entre D2 et D3 → **D2 retenu** (mode dégradé tenable) |

---

## 4. Analyse de la gravité

### 4.1 Répartition par niveau

| Gravité | Nombre d'ER | Codes | Poids |
|:-:|:-:|:-:|---|
| 🔴 **G4 - Critique** | **1** | ER6 | 14 % |
| 🟠 **G3 - Grave** | **3** | ER1, ER3, ER5 | 43 % |
| 🟡 **G2 - Significative** | **3** | ER2, ER4, ER7 | 43 % |
| 🟢 **G1 - Mineure** | 0 | - | 0 % |

### 4.2 Événement critique : ER6 (VM4 - Perte définitive des données comptables)

**Un seul ER est coté G4** dans l'étude : **ER6** - la perte définitive des données comptables et de gestion, qui empêcherait de reconstituer les comptes clients, les encours et la comptabilité, et placerait la société en situation de survie.

**Cette cotation dépend directement de deux facteurs :**
- **H07** `[M]` : aucun test de restauration documenté → information manquante
- **H08** `[H]` : sauvegardes sur la même infrastructure, sans copie hors ligne

> 💡 **Si une sauvegarde immuable testée existait**, cet événement redescendrait à **G3**. C'est exactement ce que corrige la mesure **M15** (sauvegarde immuable externalisée + test trimestriel), qui fait passer R1 et R3 de G4 à G3 dans l'atelier 5.

### 4.3 Événements G3 : atteinte sérieuse à l'activité ou aux données

Trois ER sont cotés **G3 - Grave** :

- **ER1** (VM1) : arrêt de 70 % du CA au-delà d'une journée
- **ER3** (VM2) : violation RGPD + perte de confiance commerciale
- **ER5** (VM3) : fraude au RIB avec pertes financières souvent irrécupérables

Ces trois ER sont **directement visés par les scénarios stratégiques** de l'atelier 3 (SS1, SS2, SS3, SS5) et deviennent les risques **R1, R3, R4, R5** de l'atelier 5.

### 4.4 Événements G2 : mode dégradé maîtrisable

Trois ER sont cotés **G2 - Significative** :

- **ER2** (VM1) : altérations détectables et corrigeables
- **ER4** (VM3) : factures décalées mais non perdues
- **ER7** (VM5) : inventaire manuel possible quelques jours

Ces ER sont **tolérables en mode dégradé** et n'engagent pas la survie de l'organisation. Ils ne font pas l'objet d'un scénario stratégique dédié dans l'atelier 3 (aucun risque R ne leur est associé dans la synthèse de l'atelier 5).

---

## 5. Rattachement aux scénarios stratégiques (aperçu atelier 3)

Les événements redoutés **G3 et G4** sont repris comme cibles des scénarios stratégiques de l'atelier 3.

| ER | Gravité | Scénario stratégique associé | Risque final (atelier 5) |
|:-:|:-:|:-:|:-:|
| **ER6** | 🔴 G4 | SS1 (via infogérant), SS3 (via salarié) | **R1, R3** |
| **ER1** | 🟠 G3 | SS2 (via éditeur ERP) | **R2** |
| **ER3** | 🟠 G3 | SS5 (commercial sur le départ) | **R5** |
| **ER5** | 🟠 G3 | SS4 (fraude au RIB) | **R4** |
| **ER2, ER4, ER7** | 🟡 G2 | *Non retenus en scénario stratégique* | - |

> Ce tableau est donné **à titre d'aperçu** : la construction détaillée des scénarios stratégiques fait l'objet de la fiche [`03_atelier3_scenarios_strategiques/A3_scenarios_strategiques.md`](../03_atelier3_scenarios_strategiques/A3_scenarios_strategiques.md).

---

## 6. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Codes ER1 à ER7 | `Atelier 1 - ER` | Colonne B (Evenement redouté) |
| Valeur métier associée | `Atelier 1 - ER` | Colonne A |
| Impact détaillé | `Atelier 1 - ER` | Colonne C |
| Gravité | `Atelier 1 - ER` | Colonne D |
| Besoin D-I-C-T | `Atelier 1 - ER` | Colonne E |
| Justification | `Atelier 1 - ER` | Colonne F |
| Échelles de gravité et D-I-C-T | `Métriques` | Bloc « Besoins de sécurité » et bloc « Gravité » |

---

## 7. Checklist de validation

- [x] **Chaque valeur métier** est couverte par au moins un ER (VM1 : 2 ER ; VM2 : 1 ER ; VM3 : 2 ER ; VM4 : 1 ER ; VM5 : 1 ER).
- [x] Chaque ER est **coté en gravité** selon l'échelle de la feuille `Métriques` (G1 à G4).
- [x] Chaque ER est **rattaché à un besoin D-I-C-T** justifié.
- [x] L'**impact métier** est décrit de façon concrète (chiffres, conséquences opérationnelles).
- [x] Les ER cotés **G3 et G4** sont clairement identifiés comme cibles des scénarios stratégiques.
- [x] Les **dépendances aux hypothèses** (H07, H08) sont explicitées pour le seul ER coté G4.
- [x] L'échelle de gravité utilisée est **cohérente avec celle du classeur** (4 niveaux).

---

## 8. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Évaluer la gravité des événements redoutés » (Ateliers 1 et 3)
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Métriques`, `Atelier 1 - ER`
- Dossier de synthèse - § 3.2 « Événements redoutés et gravité » (pages 6-7)
- Fiche amont : [`A1_perimetre_metier_technique.md`](./A1_perimetre_metier_technique.md)
- Fiche aval : [`A1_socle_securite_gaps.md`](./A1_socle_securite_gaps.md)