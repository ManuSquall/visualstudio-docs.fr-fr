# <a name="contributing"></a>Contribution

Nous vous remercions de l’intérêt que vous portez à la documentation Visual Studio à travers vos contributions.

Dans cette rubrique, vous allez découvrir le processus de base pour ajouter ou mettre à jour le contenu sur le [site de documentation Visual Studio](https://docs.microsoft.com/visualstudio).

Dans cette rubrique, nous allons aborder les sujets suivants :

* [Processus de contribution](#process-for-contributing)
* [Liste de recommandations](#guidance-checklist)
* [Élaboration des documents](#building-the-docs)
* [Contribution aux exemples](#contributing-to-samples)
* [Contrat de licence de contributeur](#contributor-license-agreement)

## <a name="process-for-contributing"></a>Processus de contribution

**Étape 1 :** Ouvrez un dossier décrivant l’article que vous voulez rédiger et son rapport avec le contenu existant.
Le contenu situé dans le dossier **docs** est organisé en sections, qui sont elles-mêmes organisées par domaine de contenu (par exemple, débogueur). Essayez de déterminer le dossier qui correspond le mieux à votre nouveau contenu. Obtenez des commentaires sur votre proposition. 

Vous pouvez ignorer cette première étape pour les petites modifications.

**Étape 2 :** Dupliquez (fork) le dépôt `MicrosoftDocs/visualstudio-docs`.

**Étape 3 :** Créez une branche (`branch`) pour votre article.

**Étape 4 :** Rédigez votre article.

S’il s’agit d’une nouvelle rubrique, vous pouvez utiliser ce [fichier de modèle](./styleguide/template.md) comme point de départ. Il contient les recommandations rédactionnelles et explique aussi les métadonnées nécessaires pour chaque article, comme les informations sur l’auteur.

Accédez au dossier qui correspond à l’emplacement de la table des matières de votre article déterminé à l’étape 1.
Ce dossier contient les fichiers Markdown de tous les articles de la section. Si nécessaire, créez un nouveau dossier pour y placer les fichiers de votre contenu.

Ajoutez les images et autres ressources statiques au sous-dossier appelé **media**. Si vous créez un dossier pour le contenu, ajoutez un dossier media au nouveau dossier.

Veillez à respecter la syntaxe Markdown appropriée. Pour plus d’informations, consultez le [guide de style](./styleguide/template.md).

### <a name="example-structure"></a>Exemple de structure

    docs
      /debugger
          debugging-installed-app-package.md
          /media
              debugging-installed-app-package.png

**Étape 5 :** Soumettez une demande de tirage de votre branche à `MicrosoftDocs/visualstudio-docs/master`.

Si votre demande de tirage (pull request) répond à un problème existant, ajoutez le mot clé `Fixes #Issue_Number` au message de validation ou à la description de la demande de tirage. Le dossier pourra ainsi être clôturé automatiquement dès que la demande de tirage aura été fusionnée. Pour plus d’informations, consultez [Closing issues via commit messages](https://help.github.com/articles/closing-issues-via-commit-messages/).

L’équipe Visual Studio examine votre demande de tirage et vous fait savoir si la modification est recevable en l’état ou si d’autres mises à jour/modifications sont nécessaires à son approbation.

**Étape 6 :** Mettez à jour votre branche comme l’équipe vous l’y a invité.

Les personnes chargées de la maintenance fusionneront votre demande de tirage dans la branche principale une fois que les commentaires auront été appliqués et que votre modification sera correcte.

Nous envoyons (push) toutes les validations de la branche principale à la branche en ligne à une certaine fréquence. Vous pourrez voir vos contributions en ligne sur https://docs.microsoft.com/visualstudio/.

## <a name="dos-and-donts"></a>À faire et à ne pas faire

Voici une courte liste de règles directrices que vous devez garder à l’esprit quand vous contribuez à la documentation .NET.

- **À ne pas faire** : Nous surprendre avec des demandes de tirage démesurées. Déposez plutôt un dossier et démarrez une discussion pour convenir avec nous de la direction à prendre avant d’investir beaucoup de votre temps.
- **À faire** : Lire le [guide de style](./styleguide/template.md) et les recommandations sur le [style et le ton](./styleguide/voice-tone.md).
- **À faire** : Utiliser le fichier de [modèle](./styleguide/template.md) comme point de départ de votre travail.
- **À faire** : Créer une branche distincte dans votre fourche avant de travailler sur les articles.
- **À faire** : Suivre le [workflow GitHub Flow](https://guides.github.com/introduction/flow/).
- **À faire** : Bloguer et tweeter (ou autre) régulièrement à propos de vos contributions.

> [!NOTE]
> Vous remarquerez peut-être que certaines rubriques ne respectent pas toutes les recommandations spécifiées ici et dans le [guide de style](./styleguide/template.md). Nous travaillons actuellement à une cohérence globale du site. Consultez la liste des [dossiers ouverts](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) que nous voulons amener vers cet objectif.

## <a name="building-the-docs"></a>Élaboration des documents

La documentation est écrite en [GFM (GitHub Flavored Markdown)](https://help.github.com/categories/writing-on-github/) et générée à l’aide de [DocFX](https://dotnet.github.io/docfx/) et d’autres outils de publication/génération internes. Elle est hébergée sur [docs.microsoft.com](https://docs.microsoft.com/dotnet).

Si vous souhaitez générer les documents localement, vous devez installer [DocFX](https://dotnet.github.io/docfx/) ; les dernières versions sont les plus indiquées.

Il existe plusieurs façons d’utiliser DocFX, dont vous trouverez une description dans le [guide de prise en main de DocFX](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html) pour la plupart d’entre elles.
Les instructions suivantes s’appliquent à la version [en ligne de commande](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html#2-use-docfx-as-a-command-line-tool) de l’outil.
Si vous êtes plus à l’aise avec les autres méthodes indiquées dans le lien ci-dessus, n’hésitez pas à les utiliser.

**Remarque :** DocFX nécessite actuellement le .NET Framework sur Windows ou Mono (pour Linux ou macOS). Nous espérons le porter vers .NET Core dans l’avenir.

Vous pouvez générer le site et le prévisualiser localement en utilisant un serveur web intégré. Accédez au dossier core-docs sur votre ordinateur et tapez la commande suivante :

```
docfx -t default --serve
```

La prévisualisation locale démarre sur [localhost:8080](http://localhost:8080). Vous pouvez ensuite examiner les modifications en accédant à `http://localhost:8080/[path]`, par exemple http://localhost:8080/articles/welcome.html.

**Remarque :** La prévisualisation locale ne contient actuellement aucun thème. L’apparence ne sera donc pas la même que sur le site de documentation. Nous travaillons actuellement à l’amélioration de cette expérience.

# <a name="contributing-to-samples"></a>Contribution aux exemples

Pour le moment, intégrez les exemples de code nécessaires sous forme de blocs de code inline dans l’article. Le dépôt contient un dossier codesnippets, mais il n’est pas prêt pour les contributions publiques.
