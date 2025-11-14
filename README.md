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
- **Ventes à l'étranger** : Support complet de l'OSS (One Stop Shop) pour les ventes dans l'UE

## Utilisation

1. Ouvrez le fichier `index.html` dans votre navigateur web
2. Remplissez les champs obligatoires :
   - Prix d'achat HT
   - Prix de vente TTC
3. Ajustez les paramètres selon vos besoins :
   - Taux de TVA (par défaut 20%)
   - Commissions marketplace (€ ou %)
   - Frais de port (€ ou %)
4. Pour une vente à l'étranger, cochez la case "Vente à l'étranger (UE)" et indiquez le taux de TVA du pays de destination
5. Cliquez sur "Calculer les bénéfices"

## Détails des calculs

### Vente en France
- **Prix de vente HT** = Prix de vente TTC / (1 + TVA vente%)
- **Prix d'achat TTC** = Prix d'achat HT × (1 + TVA achat%)
- **Marge brute** = Prix de vente HT - Prix d'achat HT
- **TVA encaissée** = Prix de vente TTC - Prix de vente HT
- **TVA décaissée** = Prix d'achat HT × TVA achat%
- **TVA à reverser** = TVA encaissée - TVA décaissée
- **Bénéfice net** = Prix de vente HT - Prix d'achat HT - Frais totaux - TVA à reverser

### Vente à l'étranger (OSS)
- La TVA du pays de destination s'applique
- La TVA collectée doit être intégralement reversée au pays de destination via l'OSS
- Le système calcule automatiquement la TVA selon le taux du pays de destination

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
