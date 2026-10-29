# Le Carnet — version simple (HTML, sans outil de construction)

Un site d'articles sobre, composé de simples fichiers. Il n'y a **rien à installer ni à compiler** :
`index.html` est déjà à la racine, GitHub n'a qu'à le publier.

> PHP ne peut pas être utilisé ici : GitHub Pages est un service d'hébergement de sites *statiques*
> ([GitHub Docs](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages)).
> Le site fonctionne donc en HTML, CSS et JavaScript.

```
index.html          page d'accueil (les derniers articles en haut)
article.html        page de lecture (affiche n'importe quel article)
ajouter.html        outil pour préparer un nouvel article
articles.json       la liste des articles + les réglages du site
articles/           un fichier .md par article (texte en Markdown)
pages/              pages fixes (« À propos »)
images/             vos images
assets/             style.css, carnet.js, polices
```

## 1. Mettre le site en ligne (une seule fois)

1. Créez un compte sur github.com, puis un **nouveau dépôt** (« New repository »), en **public**.
2. Dans le dépôt : **Add file → Upload files** ([documentation](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)).
   Glissez le **contenu** du dossier du site (`index.html`, `articles.json`, les dossiers…), pas le dossier lui-même :
   `index.html` doit se trouver à la racine du dépôt. Validez avec **Commit changes**
   (choisissez « Commit directly to the main branch »). Limites : 100 fichiers par envoi et 25 Mio par fichier.
3. **Settings → Pages → Build and deployment → Source : « Deploy from a branch »**, branche **main**,
   dossier **/(root)**, puis **Save** ([documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)).
4. Patientez une à deux minutes : l'adresse du site s'affiche en haut de la page Settings → Pages
   (de la forme `https://votre-compte.github.io/nom-du-depot/`).

## 2. Ajouter un article

1. Ouvrez `https://votre-adresse/ajouter.html`.
2. Saisissez le titre et la date, puis écrivez le texte, **ou** copiez-le dans Word et collez-le dans la zone
   « Depuis Word » : l'outil le convertit en Markdown. Contrôlez l'aperçu à droite.
3. **Étape 1** : sur GitHub, **Add file → Create new file**, copiez le nom du fichier proposé
   (par exemple `articles/2026-11-03-mon-titre.md`) dans le champ du nom, collez le contenu, puis **Commit changes**
   ([documentation](https://docs.github.com/en/repositories/working-with-files/managing-files/creating-new-files)).
4. **Étape 2** : ouvrez `articles.json`, cliquez sur le crayon, sélectionnez tout, collez le texte fourni par l'outil,
   puis **Commit changes** ([documentation](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files)).
5. Une minute plus tard, l'article est en tête de la page d'accueil.

**Images :** déposez-les d'abord dans le dossier `images` (Add file → Upload files, après avoir ouvert ce dossier),
avec des noms simples (lettres, chiffres, tirets), puis écrivez `![description](images/nom.jpg)` dans le texte.
Pour la vignette de l'accueil, renseignez le champ « Vignette » avec `images/nom.jpg`.

**Modifier un article :** ouvrez son fichier dans `articles/`, cliquez sur le crayon, corrigez, validez.
Pour changer le titre, la date ou le résumé, modifiez aussi sa ligne dans `articles.json`.

**Supprimer un article :** supprimez son fichier et son bloc dans `articles.json`.

### Syntaxe Markdown

| Pour obtenir | Écrire |
|---|---|
| intertitre | `## Mon intertitre` (et `### ` pour un sous-intertitre) |
| **gras** / *italique* | `**gras**` / `*italique*` |
| lien | `[texte](https://…)` |
| image avec légende | `![description](images/nom.jpg "Légende")` |
| citation | `> texte cité` |
| liste | `- élément` ou `1. élément` |
| note de bas de page | `[^1]` dans le texte, puis `[^1]: texte de la note` en fin de fichier |

Les espaces avant `: ; ! ?` et dans les guillemets « » sont corrigées automatiquement.

## 3. Réglages

Dans `articles.json`, la partie `"site"` contient le titre, le slogan, le nom de l'auteur, la mention de pied de
page et les pages fixes (chaque page `xxx` correspond à un fichier `pages/xxx.md`).
Les couleurs se changent dans les variables au début de `assets/style.css`.

## 4. À savoir

* **JavaScript requis** : les articles sont affichés par le navigateur. Conséquences : pas de flux RSS, et un
  référencement par les moteurs de recherche moins fiable qu'avec des pages générées à l'avance.
* **Ne pas ouvrir `index.html` par double-clic** : le navigateur interdit alors la lecture des articles.
  Testez sur l'adresse GitHub, ou lancez `python3 -m http.server` dans le dossier et visitez `http://localhost:8000`.
* **« Depuis Word »** : la conversion gère titres, gras, italique, listes, liens, citations et (en principe) les notes
  de bas de page, mais elle a été vérifiée avec un collage simulé, pas avec toutes les versions de Word. Relisez
  toujours le résultat. Les images collées ne passent pas : l'outil laisse un emplacement à compléter.
* **Dépôt public** : avec l'offre gratuite, GitHub Pages n'est disponible que pour les dépôts publics
  ([GitHub Docs](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages)) : tout ce que
  vous y déposez est lisible par tous, brouillons compris. Gardez vos brouillons sur votre ordinateur.
* **Nom de domaine personnalisé** : Settings → Pages → *Custom domain*, puis enregistrement DNS chez votre registraire
  ([GitHub Docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)).
* **Limites de GitHub Pages** : site de 1 Go au plus, 100 Go de trafic par mois (limite « souple »), usage commercial
  interdit ([GitHub Docs](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits)).
* `ajouter.html` n'est pas lié dans les menus mais reste accessible à qui connaît l'adresse ; il ne permet de rien
  publier, seulement de préparer du texte à copier.

## 5. Propriété intellectuelle

* Vos articles vous appartiennent du seul fait de leur création (art. L. 111-1 du Code de la propriété intellectuelle).
* Police **Lora** : licence SIL Open Font License 1.1 (`assets/fonts/Lora-OFL.txt`).
* Le code et les images d'exemple ont été créés pour ce projet ; n'y ajoutez pas d'éléments appartenant à des tiers
  sans autorisation.
