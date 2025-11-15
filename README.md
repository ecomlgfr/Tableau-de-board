# Calculateur de Marges et Bénéfices

Une application web complète pour calculer les bénéfices et marges de vos produits revendus sur internet, avec import automatique de fichiers Excel et visualisations graphiques.

## Fonctionnalités

### 📊 Calculs principaux
- **Prix et marges** : Calcul automatique du prix de vente HT, prix d'achat TTC, marge brute et taux de marge
- **TVA** : Gestion complète de la TVA encaissée, décaissée et à reverser
- **Frais** : Prise en compte des commissions marketplace et frais de port (achat et vente)
- **Bénéfice net** : Calcul précis de votre gain réel après tous les frais et taxes
- **Taxe routière** : Prise en compte automatique de la taxe routière de 1€

### 🎯 Options flexibles
- **Frais de port** : Montant fixe en euros (achat et vente séparés)
- **Commissions** : Montant fixe en euros
- **TVA personnalisable** : Définissez vos propres taux de TVA à l'achat et à la vente
- **Achats à l'étranger (UE)** : Gestion des achats intracommunautaires (Allemagne, Belgique, etc.) avec ou sans numéro intracommunautaire
- **Ventes à l'étranger** : Support complet de l'OSS (One Stop Shop) pour les ventes dans l'UE

### 📂 Import de fichiers Excel
- **Support Excel (.xlsx)** : Importez vos fichiers d'achats au format Excel natif
- **Multi-fichiers de ventes** : Importez plusieurs fichiers CSV de ventes Amazon simultanément
- **Multi-pays** : Support des ventes FR, DE, ES, IT, NL, BE, PT
- **Prévisualisation** : Aperçu des 5 premières lignes pour valider l'import
- **Logique inversée** : Part des achats pour chercher les ventes correspondantes
- **Deux résumés distincts** :
  - Résumé de TOUS les achats (vendus + non vendus)
  - Résumé des VENTES trouvées uniquement
- **Séparation visuelle** : Achats en jaune, ventes en bleu
- **Gestion des achats Allemagne** : Calcul automatique de l'autoliquidation de la TVA
- **Commissions Amazon** : Prise en compte automatique des commissions avec TVA
- **Statut de vente** : Identification des achats vendus (✓ vert) et non vendus (✗ rouge)

### 📈 Visualisations graphiques
- **Graphique achats** : Camembert vendus/non vendus
- **Graphique pays** : Répartition des ventes par pays
- **Graphique bénéfices** : Profits vs Pertes avec montants
- **Couleurs dynamiques** : Bénéfices en vert, pertes en rouge

## Utilisation

### Mode Calculateur manuel

1. Ouvrez le fichier `index.html` dans votre navigateur web
2. Restez sur l'onglet "Calculateur manuel"
3. **Section ACHATS (jaune)** :
   - Renseignez le prix d'achat HT
   - Ajoutez les frais de port d'achat si nécessaire
   - Si achat à l'étranger : cochez et sélectionnez le pays + mode intracommunautaire
4. **Section VENTES (bleue)** :
   - Renseignez le prix de vente TTC
   - Ajoutez les commissions marketplace (montant fixe €)
   - Ajoutez les frais de port de vente (montant fixe €)
   - Si vente à l'étranger : cochez et indiquez la TVA du pays
5. Cliquez sur "Calculer les bénéfices"

### Mode Import fichiers

1. Cliquez sur l'onglet "Import fichiers"
2. **Importez votre fichier d'achats Excel (.xlsx)**
   - Le fichier doit contenir :
     - Colonne F "Montant d'origine" (montant HT)
     - Colonne J "Réf CDE client" (référence de commande)
   - **Déductions automatiques** :
     - 11€ de frais de port HT
     - 1€ de taxe routière
     - **Total déduit : 12€**
3. **Importez un ou plusieurs fichiers de ventes Amazon (CSV)**
   - Détection automatique du pays selon le nom du fichier (FR, DE, ES, IT, NL, BE, PT)
   - Vous pouvez sélectionner plusieurs fichiers en même temps
   - Le fichier doit contenir les colonnes :
     - C : Type de transaction
     - D : Numéro de la commande
     - F : Total des frais produit (HT)
     - H : Commissions Amazon (TTC)
     - I : TVA de la vente
4. **Prévisualisez les données**
   - Vérifiez les 5 premières lignes d'achats
   - Visualisez les ventes correspondantes trouvées avec leur pays
5. Cliquez sur "Analyser les fichiers"
6. Consultez les résultats :
   - **Résumé jaune (TOUS LES ACHATS)** :
     - Achats totaux
     - Achats vendus
     - Achats non vendus
     - Coût total de tous les achats
   - **Résumé bleu (VENTES UNIQUEMENT)** :
     - Ventes trouvées
     - CA HT total
     - Coût des achats vendus
     - Bénéfice net total (vert/rouge)
     - TVA à reverser
     - Commissions totales
   - **3 graphiques circulaires** :
     - Répartition vendus/non vendus
     - Répartition par pays de vente
     - Bénéfices vs Pertes
   - **Section ACHATS** : Détail de tous les achats avec taxe routière et statut
   - **Section VENTES** : Calculs détaillés avec pays et bénéfice net coloré

## Détails des calculs

### Achat en France
- **Prix d'achat TTC** = Prix d'achat HT × (1 + TVA achat%)
- **TVA décaissée** = Prix d'achat HT × TVA achat% (déductible)

### Achat à l'étranger (UE) avec numéro intracommunautaire
- **Autoliquidation de la TVA** : Vous achetez HT sans payer de TVA au fournisseur
- **TVA à déclarer** = Prix d'achat HT × 20% (TVA française)
- Cette TVA est à la fois collectée ET déductible sur votre déclaration
- Impact neutre sur la trésorerie (TVA collectée = TVA déductible)

### Achat à l'étranger (UE) sans numéro intracommunautaire
- **Prix d'achat TTC** = Prix d'achat HT × (1 + TVA du pays étranger)
- **TVA payée** = TVA du pays étranger (NON déductible en France)
- ⚠️ La TVA étrangère constitue un coût supplémentaire pour votre entreprise
- Exemple Allemagne : 19% de TVA non récupérable

### Vente en France
- **Prix de vente HT** = Prix de vente TTC / (1 + TVA vente%)
- **TVA encaissée** = Prix de vente TTC - Prix de vente HT
- **TVA à reverser** = TVA encaissée - TVA décaissée
- **Bénéfice net** = Prix de vente HT - Prix d'achat HT - Frais totaux - TVA à reverser

### Vente à l'étranger (OSS)
- La TVA du pays de destination s'applique
- La TVA collectée doit être intégralement reversée au pays de destination via l'OSS
- Le système calcule automatiquement la TVA selon le taux du pays de destination

### Import Excel - Calculs automatiques

Pour chaque commande, le système calcule :

1. **Achat HT net** = Montant d'origine - 11€ (frais de port) - 1€ (taxe routière)
2. **TVA autoliquidée** = (Achat HT + Frais port HT + Taxe routière) × 20%
3. **TVA déductible** = TVA autoliquidée (car achat intracommunautaire)
4. **Commission HT** = Commission TTC / 1.20
5. **TVA sur commission** = Commission TTC - Commission HT
6. **TVA à reverser** = TVA encaissée - TVA déductible
7. **Bénéfice net** = Vente HT - Achat HT - Frais port HT - Taxe routière - Commission HT - TVA commission - TVA à reverser

**Note importante** : Les calculs supposent un achat en Allemagne avec numéro intracommunautaire (autoliquidation de la TVA) et des ventes multi-pays.

### Nouveautés de l'import

**Logique inversée** : Le système part du fichier d'achats et cherche les ventes correspondantes. Cela permet de :
- Identifier tous les achats, même non vendus
- Suivre votre stock invendu
- Avoir une vision complète de vos opérations

**Multi-pays** : Détection automatique du pays de vente selon le nom du fichier :
- Nommez vos fichiers avec le code pays (ex: ventes_FR.csv, ventes_DE.csv)
- Import simultané de tous les pays pour recherche globale

**Deux résumés** :
- Un résumé pour TOUS vos achats (incluant invendus)
- Un résumé pour les ventes trouvées uniquement (avec bénéfices réels)

**Couleurs et graphiques** :
- Bénéfices en vert, pertes en rouge
- 3 graphiques circulaires pour visualiser rapidement vos données
- Sections colorées (jaune=achats, bleu=ventes)

## Pays supportés

### Pour les achats UE
- 🇩🇪 **Allemagne** : TVA 19%
- 🇧🇪 **Belgique** : TVA 21%
- 🇪🇸 **Espagne** : TVA 21%
- 🇮🇹 **Italie** : TVA 22%
- 🇳🇱 **Pays-Bas** : TVA 21%
- 🇵🇱 **Pologne** : TVA 23%
- 🌍 **Autre pays UE** : TVA personnalisable

### Pour les ventes Amazon
- 🇫🇷 **France**
- 🇩🇪 **Allemagne**
- 🇪🇸 **Espagne**
- 🇮🇹 **Italie**
- 🇳🇱 **Pays-Bas**
- 🇧🇪 **Belgique**
- 🇵🇹 **Portugal**

## Technologies utilisées

- HTML5
- CSS3 (avec animations et design responsive)
- JavaScript vanilla
- **SheetJS (xlsx)** : Pour lire les fichiers Excel natifs
- **Chart.js** : Pour les graphiques circulaires et camemberts

## Responsive Design

L'application s'adapte automatiquement à tous les types d'écrans :
- Ordinateurs de bureau
- Tablettes
- Smartphones

## Licence

MIT License - Libre d'utilisation
