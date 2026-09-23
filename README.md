# Volley 5-1 — Révision des positions (réception)

Application web statique (un seul fichier `index.html`, sans build ni backend) pour réviser
le placement en **réception** dans le système **5-1**, sur les 6 rotations (P1→P6).
Positions d'après les schémas de Bayonne Volley-Ball.

- Choix du poste : Passeur, Central, Réceptionneuse (R4), Pointu, Libéro.
- Mode **Quiz** : les autres joueuses sont déjà placées, tu glisses ton poste à la bonne position.
- Mode **Référence** : alignement complet, rotation par rotation.
- Contour **rouge = ligne arrière**, **bleu = ligne avant**.

## Lancer en local

```powershell
python -m http.server 8777
# puis ouvrir http://localhost:8777/
```

## Héberger (repo privé + site public, gratuit)

Le plan GitHub gratuit ne permet pas GitHub Pages depuis un repo privé.
On garde donc le **code privé** sur GitHub et on publie via **Cloudflare Pages** (ou Netlify).

### Cloudflare Pages (recommandé)

1. Sur https://dash.cloudflare.com → **Workers & Pages** → **Create** → **Pages** →
   **Connect to Git**, autorise l'accès au repo privé `VincentGvr/volley-5-1`.
2. Build settings : **Framework preset = None**, **Build command = (vide)**,
   **Build output directory = /** (racine).
3. **Save and Deploy** → URL publique `https://volley-5-1.pages.dev`.
4. Les en-têtes de sécurité sont appliqués automatiquement via le fichier `_headers`.

### Netlify (alternative)

1. https://app.netlify.com → **Add new site** → **Import from Git** → repo privé.
2. Build command vide, publish directory `/`. Le fichier `_headers` est également pris en charge.

## Sécurité

- Aucune dépendance externe, aucun script tiers, aucune donnée personnelle collectée.
- CSP restrictive (`default-src 'none'`) + en-têtes (`_headers`) : HSTS, `X-Frame-Options: DENY`,
  `X-Content-Type-Options: nosniff`, `Referrer-Policy: no-referrer`, `Permissions-Policy` verrouillé.
- HTTPS fourni par l'hébergeur.
- Rappel : le code côté client reste visible via « Afficher la source » ; le repo privé protège
  le dépôt Git, pas le HTML servi. Ne jamais mettre de secret dans ce fichier.
