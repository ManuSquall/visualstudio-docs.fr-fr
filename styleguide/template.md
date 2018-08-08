# <a name="metadata-and-markdown-template"></a>Métadonnées et modèle Markdown

Ce modèle de documentation de base contient des exemples de syntaxe Markdown ainsi que des conseils sur la définition de métadonnées. Pour en tirer le meilleur parti, vous devez afficher à la fois le [Markdown brut](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) et la [vue rendue](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (par exemple, le Markdown brut affiche le bloc de métadonnées contrairement à la vue rendue).

Quand vous créez un fichier Markdown, vous devez copier ce modèle dans un nouveau fichier, remplir les métadonnées comme indiqué ci-dessous, définir le titre de l’article comme titre H1 ci-dessus et supprimer le contenu. 


## <a name="metadata"></a>Metadata 

L’intégralité du bloc de métadonnées se situe au-dessus (dans le [Markdown brut](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)) et est divisé en champs obligatoires et champs facultatifs. Quelques remarques importantes :

- Vous **devez** ajouter un espace entre le signe deux-points (:) et la valeur d’un élément de métadonnées.
- Si un élément de métadonnées facultatif n’a pas de valeur, commentez l’élément avec un signe # ou supprimez-le (ne le laissez pas vide et n’utilisez pas « na ») ; si vous ajoutez une valeur à un élément qui a été commenté, veillez à supprimer le signe #.
- Des signes deux-points dans une valeur (par exemple, un titre) interrompent l’analyseur de métadonnées. Dans ce cas, entourez le titre de guillemets doubles (par exemple, `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).
- **title** : ce titre s’affiche dans les résultats des moteurs de recherche. Vous pouvez également ajouter une barre verticale (|) suivie du nom du produit (par exemple, `title: Developing Libraries with Cross Platform Tools | .NET Core`). Le titre ne doit être identique au titre H1 et il doit contenir au maximum 65 caractères (dont| NOM DU PRODUIT).
- **author**, **manager**, **ms.reviewer** : le champ d’auteur doit contenir le **nom d’utilisateur GitHub** de l’auteur, et non son alias.  En revanche, les champs « manager » et « ms.reviewer » doivent contenir des alias Microsoft. ms.reviewer spécifie le nom du PM/développeur associé à l’article ou la fonctionnalité.
- **ms.devlang** définit la technologie. Certaines des valeurs prises en charge sont : dotnet, cpp, csharp, fsharp, vb et xml.
- **ms.assetid** : il s’agit du GUID de l’article utilisé à des fins de suivi interne comme Business Intelligence (BI). Quand vous créez un fichier Markdown, récupérez un GUID sur [https://www.guidgenerator.com](https://www.guidgenerator.com). 

## <a name="basic-markdown-gfm-and-special-characters"></a>Markdown de base, GFM et caractères spéciaux

Toute la syntaxe Markdown de base et GFM (GitHub Flavored Markdown) est prise en charge. Pour plus d’informations sur cette syntaxe, consultez :

- [Syntaxe Markdown de base](https://daringfireball.net/projects/markdown/syntax)
- [Documentation GFM](https://guides.github.com/features/mastering-markdown)

Markdown utilise des caractères spéciaux tels que \*, \` et \# pour la mise en forme. Si vous souhaitez inclure l’un de ces caractères dans votre contenu, vous devez effectuer l’une des deux opérations suivantes :

- Placer une barre oblique inverse devant le caractère spécial pour l’« échappement » de ce caractère (par exemple, `\*` pour un \*)
- Utiliser le [code d’entité HTML](http://www.ascii.cl/htmlcodes.htm) pour le caractère (par exemple, `&#42;` pour un &#42;).

## <a name="file-name"></a>Nom de fichier

Les noms des fichiers utilisent les règles suivantes :
* Ils contiennent uniquement des lettres minuscules, des chiffres et des traits d’union.
* Aucun espace ni caractère de ponctuation. Utilisez les traits d’union pour séparer les mots et les nombres dans le nom de fichier.
* Utilisez des verbes d’actions spécifiques, tels que développer, acheter, générer, dépanner. Pas de substantif.
* Pas de mot trop court ; évitez un, et, le, en, ou, etc.
* Le nom doit être au format Markdown et utiliser l’extension de fichier .md.
* Privilégiez des noms de fichiers courts. Ils font partie de l’URL pour vos articles.  



## <a name="headings"></a>Titres

Utilisez la mise en majuscules comme pour les phrases. Mettez toujours en majuscules :
- Le premier mot d’un titre. 
- Le mot qui suit le signe deux-points dans un titre ou un en-tête (par exemple, « Comment : Trier un tableau »). 

Les titres doivent être créés à l’aide du style atx, c’est-à-dire en utilisant 1 à 6 caractères de hachage (#) au début de la ligne pour indiquer un titre, correspondant aux niveaux de titres HTML H1 à H6. Des exemples de titres de premier et second niveau sont utilisés ci-dessus. 

Il ne **doit** exister qu’un seul titre de premier niveau (H1) dans votre rubrique, qui sera affiché comme titre sur la page.

Si votre titre se termine par un caractère `#`, vous devez ajouter un autre caractère `#` à la fin pour que le titre soit correctement rendu. Par exemple, `# Async Programming in F# #`.     

Les titres de second niveau génèrent la table des matières sur la page qui s’affiche dans la section « Dans cet article » en dessous du titre sur la page.

### <a name="third-level-heading"></a>Titre de troisième niveau
#### <a name="fourth-level-heading"></a>Titre de quatrième niveau
##### <a name="fifth-level-heading"></a>Titre de cinquième niveau
###### <a name="sixth-level-heading"></a>Titre de sixième niveau
 
## <a name="text-styling"></a>Style du texte

*Italique* À utiliser pour les fichiers, dossiers, chemins (pour les éléments longs, séparés sur leur propre ligne), les nouveaux termes, les URL (sauf quand elles sont rendues sous forme de liens, par défaut).

**Gras** À utiliser pour les éléments d’interface utilisateur.

## <a name="links"></a>liens

### <a name="internal-links"></a>Liens internes

Pour établir un lien à un en-tête dans le même fichier Markdown (également appelés liens d’ancrage), vous devrez trouver l’ID de l’en-tête en question. Pour vérifier l’ID, affichez la source de l’article rendu, recherchez l’ID de l’en-tête (par exemple, `id="blockquote"`) et établissez le lien avec # + ID (par exemple, `#blockquote`).
L’ID est généré automatiquement en fonction du texte d’en-tête. Ainsi, par exemple, étant donné une section unique nommée `## Step 2`, l’ID ressemblerait à `id="step-2"`.

- Exemple : [Chapitre 1](#chapter-1)

Pour établir un lien à un fichier Markdown dans le même dépôt, utilisez des [liens relatifs](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), dont « .md » à la fin du nom de fichier.

- Exemple : [Fichier readme](../readme.md)
- Exemple : [Bienvenue dans .NET](../docs/welcome.md)

Pour établir un lien à un en-tête d’un fichier Markdown dans le même dépôt, utilisez la liaison relative + la liaison hashtag.

- Exemple : [Communauté ASP.NET](../docs/welcome.md#community)

### <a name="external-links"></a>Liens externes

Pour établir un lien à un fichier externe, utilisez l’URL complète comme lien.

- Exemple : [GitHub](http://www.github.com)

Si une URL apparaît dans un fichier Markdown, elle est transformée en lien interactif.

- Exemple : http://www.github.com

### <a name="links-to-apis"></a>Liens vers des API

Le système de génération a certaines extensions qui permettent d’établir des liens à des API .NET Core sans avoir à utiliser de liens externes.  
Lors de la liaison à une API, vous pouvez utiliser son identificateur unique (UID) qui est généré automatiquement à partir du code source.

Vous pouvez utiliser l’une des syntaxes suivantes :
1. Lien Markdown : `[link_text](xref:UID)`
2. Lien automatique : `<xref:UID>`
3. Forme abrégée : `@UID`

- Exemple : `@System.String`
- Exemple : `[String class](xref:System.String)` 

Pour plus d’informations sur l’utilisation de cette notation, consultez [Utilisation de renvois](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).

> Pour l’instant, il n’existe aucun moyen facile de trouver les UID. La meilleure façon de trouver l’UID pour une API consiste à le rechercher dans ce dépôt : [docascode/coreapi](https://github.com/docascode/coreapi). Nous travaillons à la mise en place d’un meilleur système à l’avenir.

Quand l’UID contient les caractères spéciaux \` ou \#, la valeur de l’UID doit être encodée au format HTML (%60 et %23 respectivement), comme dans les exemples suivants :
- Exemple : @System.Threading.Tasks.Task\`1 devient `@System.Threading.Tasks.Task%601`
- Exemple : @System.Exception.\#ctor devient `@System.Exception.%23ctor`

## <a name="lists"></a>Listes

### <a name="ordered-lists"></a>Listes triées

1. This 
1. Is
1. An
1. Ordered
1. List  


#### <a name="ordered-list-with-an-embedded-list"></a>Liste triée avec une liste incorporée

1. Here
1. comes
1. an
1. embedded
    1. Miss Scarlett
    1. Professor Plum
1. ordered
1. list


### <a name="unordered-lists"></a>Listes non triées

- This
- est
- a
- bulleted
- list


##### <a name="unordered-list-with-an-embedded-list"></a>Liste non triée avec une liste incorporée

- This 
- bulleted 
- list
    - Mrs. Peacock
    - Mr. Green
- contains  
- other
    1. Colonel Mustard
    1. Mrs. White
- lists


## <a name="horizontal-rule"></a>Ligne horizontale

---

## <a name="tables"></a>Tables

| Tables        | Sont           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 est      | alignée à droite | 1 600 $ |
| col 2 est      | centrée      |   12 $ |
| col 1 est la valeur par défaut | alignée à gauche     |    1 $ |

Vous pouvez utiliser un [outil de génération de table Markdown](http://www.tablesgenerator.com/markdown_tables) pour les créer plus facilement. 

## <a name="code"></a>Code

La meilleure façon d’inclure du code consiste à ajouter des extraits à partir d’un exemple fonctionnel. Créez votre exemple en suivant les instructions du [guide de contribution](../CONTRIBUTING.md#contributing-to-samples).

Vous pouvez inclure le code à l’aide de la syntaxe Include :

```
[!code-csharp[<title>](<pathToFile>#<RegionName)]
```

L’exemple ci-dessus illustre la syntaxe C#, mais d’autres langages sont pris en charge.
Utilisez `code-fsharp` pour les exemples F# ; utilisez `code-vbnet` pour les exemples Visual Basic.
Les autres langages pris en charge sont :
* C++ : `code-cpp`
* HTML : `code-html`
* JavaScript : `code-javascript`
* Powershell : `code-ps`
* SQL : `code-sql`
* XML : `code-xml`



Le texte que vous placez pour `<title>` s’affiche en tant que substitution sur le texte. `<pathToFile>` est le chemin d’accès au fichier source. `<RegionName>` doit être une région de votre code source à inclure. Utilisez la syntaxe de préprocesseur `#region` et `#endregion` pour spécifier la région de code à inclure.

Pour les cas où les régions ne fonctionnent pas, vous pouvez spécifier le début et la fin d’un extrait à l’aide d’un nom d’élément XML dans un commentaire sur une ligne unique. Par exemple, vous pouvez écrire ceci en C# :

```csharp
// <CodeToInclude>
int j = 5;
int i ; 10;
int sum = i + j;
// </CodeToInclude>
```

Dans d’autres langages, utilisez la syntaxe de commentaire du langage concerné.
Enfin, vous pouvez utiliser des numéros de ligne : `#L1-L10` inclut les lignes 1 à 10. Nous déconseillons les numéros de ligne, car ceux-ci sont très fragiles.

L’ajout d’extraits de programmes complets garantit que tout le code s’exécute via notre système d’intégration continue. Toutefois, si vous avez besoin d’afficher un élément qui entraîne des erreurs lors de la compilation ou de l’exécution, vous pouvez utiliser des blocs de code en ligne.

### <a name="inline-code-blocks-with-language-identifier"></a>Blocs de code en ligne avec identificateur de langage

Utilisez trois accents graves (\`\`\`) + un ID de langage pour appliquer un codage en couleurs spécifique au langage à un bloc de code. Voici la liste complète des [ID de langages GFM](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs).

##### <a name="c9839"></a>C&#9839;

```c#
using System;
namespace HelloWorld
{
    class Hello 
    {
        static void Main() 
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```
#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```
#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>Bloc de code générique

Utilisez trois accents graves (&#96;&#96;&#96;) pour le codage de bloc de code générique.   

> L’approche recommandée consiste à utiliser des blocs de code avec les identificateurs de langage, comme expliqué dans la section précédente, pour garantir la coloration syntaxique appropriée sur le site de documentation. Utilisez des blocs de code générique uniquement si nécessaire.

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

### <a name="inline-code"></a>Code en ligne

Utilisez des accents graves (&#96;) pour `inline code`. Utilisez le code en ligne pour les commandes de ligne de commande, les noms de colonnes et de tables de base de données ainsi que les mots clés de langage.

## <a name="blockquotes"></a>Éléments blockquote

> La sécheresse durait maintenant depuis dix millions d’années et le règne des terribles lézards avait depuis longtemps pris fin. Ici, à l’équateur, sur le continent qui s’appellerait un jour l’Afrique, la lutte pour l’existence avait atteint un nouveau sommet dans la férocité, et le vainqueur n’était pas encore connu. Dans ce territoire aride et désolé, seul le plus petit, le plus rapide ou le plus puissant pouvait croître et espérer survivre.

## <a name="images"></a>Images

### <a name="static-image-or-animated-gif"></a>Image statique ou GIF animée

![il s’agit du texte de remplacement](../images/Logo_DotNet.png)

### <a name="linked-image"></a>Image liée

[![texte de remplacement pour l’image liée](../images/Logo_DotNet.png)](https://dot.net) 

## <a name="videos"></a>Vidéos

### <a name="channel-9"></a>Channel 9

<iframe src="https://channel9.msdn.com/Shows/On-NET/Shipping-NET-Core-RC2--Tools-Preview-1/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/g2a4W6Q7aRw" frameborder="0" allowfullscreen></iframe>

## <a name="docsmicrosoft-extensions"></a>extensions docs.microsoft

docs.microsoft fournit quelques extensions supplémentaires à GitHub Flavored Markdown. 

### <a name="alerts"></a>Alertes

Il est important d’utiliser les styles d’alerte suivants pour un rendu avec le style approprié sur le site de documentation. Toutefois, le moteur de rendu sur GitHub ne les différencie pas.     

#### <a name="note"></a>Remarque

> [!NOTE]
> Il s’agit d’une REMARQUE

#### <a name="warning"></a>Warning

> [!WARNING]
> Il s’agit d’un AVERTISSEMENT

#### <a name="tip"></a>Conseil

> [!TIP]
> Il s’agit d’un CONSEIL

#### <a name="important"></a>Important

> [!IMPORTANT]
> Cela est IMPORTANT

Et tous seront rendus comme ceci : ![Styles d’alerte](../images/alerts.png)

### <a name="buttons"></a>Boutons

> [!div class="button"]
[Liens de boutons](../docs/core/index.md)

Vous pouvez voir un exemple de boutons en action dans la [documentation Intune](https://docs.microsoft.com/en-us/intune/get-started/choose-how-to-enroll-devices). 

### <a name="selectors"></a>Sélecteurs

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Fenêtres](../docs/core/tutorials/using-on-windows.md)

Vous pouvez voir un exemple de sélecteurs en action dans la [documentation Intune](https://docs.microsoft.com/en-us/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune#how-your-end-users-get-their-apps).

### <a name="step-by-steps"></a>Procédures détaillées

>[!div class="step-by-step"]
[Précédent](../docs/csharp/expression-trees-interpreting.md)
[Suivant](../docs/csharp/expression-trees-translating.md)

Vous pouvez voir un exemple de procédures détaillées en action dans la [documentation Advanced Threat Analytics](https://docs.microsoft.com/en-us/advanced-threat-analytics/deploy-use/install-ata-step2).