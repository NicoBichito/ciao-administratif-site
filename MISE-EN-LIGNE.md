# Mettre en ligne ciao-administratif.fr

Les fichiers du site sont dans `ciao-site/site/` : `index.html` et `mentions-legales.html`.

## 1. Acheter les domaines (OVH)
1. Va sur ovhcloud.com, puis cherche `ciao-administratif.fr` et ajoute-le au panier. Fais pareil avec `ciaoadministratif.fr`.
2. Décoche les options d'hébergement et d'e-mail payantes. Le domaine seul suffit.
3. Paie (environ 7 à 10 € par an et par domaine) et valide ton identité si OVH te le demande. C'est obligatoire pour les .fr.

## 2. Créer le dépôt GitHub
1. Sur github.com, clique sur **New repository** et nomme-le `ciao-administratif-site`. Choisis **Public** ou **Private**, les deux fonctionnent avec Netlify.
2. Préviens-moi quand c'est fait : j'y pousse le site.

## 3. Brancher Netlify
1. Sur netlify.com, connecte-toi avec GitHub.
2. Clique sur **Add new project** puis **Import an existing project**, choisis GitHub et sélectionne `ciao-administratif-site`.
3. Laisse **Build command** vide et mets **Publish directory** = `site`. Clique sur **Deploy**.
4. Dans **Domain management**, clique sur **Add a domain**, saisis `ciao-administratif.fr` et fais-en le domaine principal.
5. Ajoute aussi `ciaoadministratif.fr` comme **domain alias**. Netlify le redirigera automatiquement vers le domaine principal.

## 4. Régler les DNS chez OVH (pour chacun des deux domaines)
Dans l'espace client OVH, va dans **Noms de domaine**, choisis le domaine, puis ouvre l'onglet **Zone DNS** :
- Supprime les enregistrements **A** et **AAAA** existants sur le domaine nu, ainsi que le **CNAME** de `www` s'il y en a un.
- Ajoute un enregistrement **A**, sous-domaine vide, qui pointe vers l'adresse IP indiquée par Netlify. Au moment de l'écriture, c'était `75.2.60.5`, mais prends celle affichée dans Netlify.
- Ajoute un enregistrement **CNAME** `www` qui pointe vers `<nom-du-site>.netlify.app.` (sans oublier le point final).
- Attends entre 1 et 24 h. Netlify active ensuite le HTTPS tout seul (Let's Encrypt).

## 5. Recevoir les mails de contact@ciao-administratif.fr
Chez OVH, dans **E-mails**, puis **Redirection**, ajoute `contact@ciao-administratif.fr` vers ton adresse Gmail.
Les demandes envoyées par le formulaire arrivent dans Netlify (**Forms**). Active-y la notification par e-mail : **Forms**, puis **Form notifications**, puis **Email notification**.

## 6. Avant d'ouvrir le site au public
- Remplis les champs `[…]` de `mentions-legales.html` (nom, SIRET, adresse). C'est obligatoire.
- Vérifie la marque « Ciao Administratif » sur data.inpi.fr.
