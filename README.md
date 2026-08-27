# Liza Rena’s Candy

Boutique de photographie numérique, conçue pour un frontend statique + backend sécurisé.

## Architecture

- `frontend/` : site public HTML/CSS/JS, compatible GitHub Pages.
- `backend/` : API Node.js/Express pour produits, administration, PayPal et téléchargements.
- `storage/private/` : fichiers originaux **à ne jamais publier**.
- `storage/previews/` : aperçus publics.
- `data/` : stockage local de démonstration (à remplacer par PostgreSQL/stockage objet en production).
- `.env.example` : variables à configurer.

## Important

Le frontend peut être servi par GitHub Pages, mais GitHub Pages est statique. Le backend et le stockage privé doivent être déployés séparément.

La partie PayPal est préparée pour le flux officiel PayPal Checkout : création et capture côté serveur, avec le secret PayPal uniquement côté serveur.

Avant de vendre réellement, configure PayPal Sandbox, un backend HTTPS, une base de données de production et un stockage privé.

## Développement local

1. Copier `.env.example` vers `.env`.
2. Installer les dépendances :

```bash
cd backend
npm install
```

3. Démarrer :

```bash
npm run dev
```

4. Servir le frontend avec un serveur statique, par exemple :

```bash
cd ../frontend
python3 -m http.server 5500
```

Puis ouvrir `http://localhost:5500`.

Le backend est par défaut sur `http://localhost:3000`.

## Configuration

Les valeurs `XXXXX` sont des placeholders à remplacer.

Ne commit jamais `.env`.

## PayPal

Créer une application dans le PayPal Developer Dashboard et renseigner les identifiants Sandbox dans `.env`.

Variables principales :

- `PAYPAL_CLIENT_ID`
- `PAYPAL_CLIENT_SECRET`
- `PAYPAL_ENVIRONMENT`
- `PAYPAL_WEBHOOK_ID`

Ne jamais exposer `PAYPAL_CLIENT_SECRET`.

## Production

Le stockage local inclus ici est adapté au développement et à la démonstration. En production, utiliser un stockage objet privé et une vraie base de données.

