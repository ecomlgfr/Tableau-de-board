# Calculateur de Marges et Bénéfices

Une application web complète pour calculer les bénéfices et marges de vos produits revendus sur internet, avec import automatique de fichiers CSV.

## Fonctionnalités

### 📊 Calculs principaux
- **Prix et marges** : Calcul automatique du prix de vente HT, prix d'achat TTC, marge brute et taux de marge
- **TVA** : Gestion complète de la TVA encaissée, décaissée et à reverser
- **Frais** : Prise en compte des commissions marketplace et frais de port
- **Bénéfice net** : Calcul précis de votre gain réel après tous les frais et taxes

### 🎯 Options flexibles
- **Commissions** : Choisissez entre pourcentage ou montant fixe
- **Frais de port** : Choisissez entre pourcentage ou montant fixe
- **TVA personnalisable** : Définissez vos propres taux de TVA à l'achat et à la vente
- **Achats à l'étranger (UE)** : Gestion des achats intracommunautaires (Allemagne, Belgique, etc.) avec ou sans numéro intracommunautaire
- **Ventes à l'étranger** : Support complet de l'OSS (One Stop Shop) pour les ventes dans l'UE

### 📂 Import de fichiers (NOUVEAU)
- **Support Excel (.xlsx)** : Importez vos fichiers d'achats au format Excel
- **Multi-fichiers de ventes** : Importez plusieurs fichiers CSV de ventes Amazon simultanément
- **Prévisualisation** : Aperçu des 5 premières lignes pour valider l'import
- **Logique inversée** : Part des achats pour chercher les ventes correspondantes
- **Analyse globale** : Résumé complet avec statistiques détaillées
- **Séparation achats/ventes** : Visualisation claire avec sections distinctes
- **Gestion des achats Allemagne** : Calcul automatique de l'autoliquidation de la TVA
- **Commissions Amazon** : Prise en compte automatique des commissions avec TVA
- **Statut de vente** : Identification des achats vendus et non vendus

## Utilisation

### Mode Calculateur manuel

1. Ouvrez le fichier `index.html` dans votre navigateur web
2. Restez sur l'onglet "Calculateur manuel"
3. **Si vous achetez à l'étranger** : Cochez "Achat à l'étranger (UE)" et sélectionnez :
   - Le pays d'achat (Allemagne, Belgique, Espagne, etc.)
   - Si vous avez un numéro intracommunautaire ou non
4. Remplissez les champs obligatoires :
   - Prix d'achat HT
   - Prix de vente TTC
5. Ajustez les paramètres selon vos besoins :
   - Taux de TVA (mis à jour automatiquement selon le pays)
   - Commissions marketplace (€ ou %)
   - Frais de port (€ ou %)
6. **Pour une vente à l'étranger** : Cochez "Vente à l'étranger (UE)" et indiquez le taux de TVA du pays de destination
7. Cliquez sur "Calculer les bénéfices"

### Mode Import fichiers

1. Cliquez sur l'onglet "Import fichiers CSV"
2. **Importez votre fichier d'achats Excel (.xlsx)**
   - Le fichier doit contenir :
     - Colonne F "Montant d'origine" (montant HT)
     - Colonne J "Réf CDE client" (référence de commande)
   - Les frais de port de 11€ HT seront automatiquement déduits
3. **Importez un ou plusieurs fichiers de ventes Amazon (CSV)**
   - Vous pouvez sélectionner plusieurs fichiers en même temps
   - Le fichier doit contenir les colonnes :
     - C : Type de transaction
     - D : Numéro de la commande
     - F : Total des frais produit (HT)
     - H : Commissions Amazon (TTC)
     - I : TVA de la vente
4. **Prévisualisez les données**
   - Vérifiez les 5 premières lignes d'achats
   - Visualisez les ventes correspondantes trouvées
5. Cliquez sur "Analyser les fichiers"
6. Consultez les résultats :
   - **Résumé global** : Total achats, ventes trouvées, bénéfices, TVA
   - **Section ACHATS** : Détail de tous les achats avec statut (vendu/non vendu)
   - **Section VENTES** : Calculs détaillés pour chaque vente avec TVA et bénéfices

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

### Import CSV - Calculs automatiques

Pour chaque commande, le système calcule :

1. **Achat HT net** = Montant d'origine - 11€ (frais de port)
2. **TVA autoliquidée** = (Achat HT + Frais port HT) × 20%
3. **TVA déductible** = TVA autoliquidée (car achat intracommunautaire)
4. **Commission HT** = Commission TTC / 1.20
5. **TVA sur commission** = Commission TTC - Commission HT
6. **TVA à reverser** = TVA encaissée - TVA déductible
7. **Bénéfice net** = Vente HT - Achat HT - Frais port HT - Commission HT - TVA commission - TVA à reverser

**Note importante** : Les calculs supposent un achat en Allemagne avec numéro intracommunautaire (autoliquidation de la TVA) et une vente en France.

### Nouveautés de l'import

**Logique inversée** : Le système part du fichier d'achats et cherche les ventes correspondantes. Cela permet de :
- Identifier tous les achats, même non vendus
- Suivre votre stock invendu
- Avoir une vision complète de vos opérations

**Multi-fichiers** : Importez plusieurs fichiers de ventes en une seule fois pour retrouver toutes les commandes correspondant à vos achats, même si elles sont réparties sur plusieurs périodes.

## Pays supportés pour les achats UE

- 🇩🇪 **Allemagne** : TVA 19%
- 🇧🇪 **Belgique** : TVA 21%
- 🇪🇸 **Espagne** : TVA 21%
- 🇮🇹 **Italie** : TVA 22%
- 🇳🇱 **Pays-Bas** : TVA 21%
- 🇵🇱 **Pologne** : TVA 23%
- 🌍 **Autre pays UE** : TVA personnalisable

## Technologies utilisées

- HTML5
- CSS3 (avec animations et design responsive)
- JavaScript vanilla (aucune dépendance)

## Responsive Design

L'application s'adapte automatiquement à tous les types d'écrans :
- Ordinateurs de bureau
- Tablettes
- Smartphones

## Licence

MIT License - Libre d'utilisation
