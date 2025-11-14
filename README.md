# Calculateur de Marges et Bénéfices

Une application web simple et complète pour calculer les bénéfices et marges de vos produits revendus sur internet.

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

## Utilisation

1. Ouvrez le fichier `index.html` dans votre navigateur web
2. **Si vous achetez à l'étranger** : Cochez "Achat à l'étranger (UE)" et sélectionnez :
   - Le pays d'achat (Allemagne, Belgique, Espagne, etc.)
   - Si vous avez un numéro intracommunautaire ou non
3. Remplissez les champs obligatoires :
   - Prix d'achat HT
   - Prix de vente TTC
4. Ajustez les paramètres selon vos besoins :
   - Taux de TVA (mis à jour automatiquement selon le pays)
   - Commissions marketplace (€ ou %)
   - Frais de port (€ ou %)
5. **Pour une vente à l'étranger** : Cochez "Vente à l'étranger (UE)" et indiquez le taux de TVA du pays de destination
6. Cliquez sur "Calculer les bénéfices"

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
