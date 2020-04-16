---
title: Roslyn Analyzers et Bibliothèque de code-aware pour ImmutableArrays (fr) Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65849a3d9ad1cdd073551f96e61997fe5f91118a
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444893"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analyseurs Roslyn et bibliothèque de code pour ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La [plate-forme de compilateur .NET](https://github.com/dotnet/roslyn) ("Roslyn") vous aide à construire des bibliothèques de code. Une bibliothèque consciente du code fournit des fonctionnalités que vous pouvez utiliser et l’outillage (analyseurs Roslyn) pour vous aider à utiliser la bibliothèque de la meilleure façon ou pour éviter les erreurs. Ce sujet vous montre comment construire un analyseur Roslyn du monde réel pour attraper les erreurs courantes lors de l’utilisation de la [NIB: Immutable Collections](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet paquet. L’exemple montre également comment fournir un correctif de code pour un problème de code trouvé par l’analyseur. Les utilisateurs voient des correctifs de code dans l’interface utilisateur de l’ampoule Visual Studio et peuvent appliquer automatiquement un correctif pour le code.

## <a name="getting-started"></a>Mise en route
Vous avez besoin de ce qui suit pour construire cet exemple:

- Visual Studio 2015 (pas une édition Express) ou une version ultérieure. Vous pouvez utiliser la [gratuité Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Studio visuel SDK](../extensibility/visual-studio-sdk.md). Vous pouvez également, lors de l’installation de Visual Studio, vérifier Visual Studio Extensibility Tools sous Common Tools pour installer le SDK en même temps. Si vous avez déjà installé Visual Studio, vous pouvez également installer ce SDK en allant au menu principal **File &#124; New &#124;Project ...**, en choisissant C dans la vitre de navigation gauche, puis en choisissant Extensibility. Lorsque vous choisissez le modèle de projet de chapelure **« Installez les outils d’extéabilité visual studio**», il vous invite à télécharger et installer le SDK.

- [.NET Compiler Platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Vous pouvez également installer ce SDK en allant au menu principal **Fichier &#124; Nouveau projet &#124; ...**, en choisissant C **dans** le volet de navigation gauche, puis en choisissant **Extensibility**. Lorsque vous choisissez " Télécharger le modèle de projet de chapelure **.NET Compiler Platform SDK**", il vous invite à télécharger et installer le SDK. Ce SDK comprend le [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Cet outil extrêmement utile vous aide à déterminer quels types de modèles de code vous devriez rechercher dans votre analyseur. L’infrastructure d’analyseur appelle dans votre code pour des types spécifiques de modèle de code, de sorte que votre code ne s’exécute que si nécessaire et ne peut se concentrer que sur l’analyse du code pertinent.

## <a name="whats-the-problem"></a>Quel est le problème?
Imaginez que vous fournissez une bibliothèque avec <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>ImmutableArray (par exemple, ) de soutien. Les développeurs de CMD ont beaucoup d’expérience avec les tableaux .NET. Cependant, en raison de la nature d’ImmutableArrays et des techniques d’optimisation utilisées dans la mise en œuvre, les intuitions des développeurs CMD font que les utilisateurs de votre bibliothèque écrivent du code cassé, comme expliqué ci-dessous. En outre, les utilisateurs ne voient pas leurs erreurs jusqu’à l’heure d’exécution, qui n’est pas l’expérience de qualité qu’ils sont habitués à Visual Studio avec .NET.

Les utilisateurs sont familiers avec l’écriture de code comme ce qui suit:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

La création de tableaux vides pour remplir les lignes de code ultérieures et l’utilisation de la syntaxe initiale de collecte sont très familières aux développeurs C. Cependant, écrire le même code pour un ImmutableArray se bloque à l’exécution:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

La première erreur est due à l’implémentation d’ImmutableArray à l’aide d’une struct pour envelopper le stockage de données sous-jacent. Les structs doivent avoir des `default(T)` constructeurs sans paramètres afin que les expressions puissent retourner des structs avec tous les membres nuls ou nuls. Lorsque le code `b1.Length`accède, il y a une erreur de déreférence nulle de temps d’exécution parce qu’il n’y a pas de tableau de stockage sous-jacent dans la struct d’ImmutableArray. La bonne façon de créer un ImmutableArray vide est `ImmutableArray<int>.Empty`.

 L’erreur avec les initialisateurs de collecte se produit parce que la méthode ImmutableArray.Add renvoie de nouvelles instances chaque fois que vous l’appelez. Parce qu’ImmutableArrays ne change jamais, lorsque vous ajoutez un nouvel élément, vous revenez un nouvel objet ImmutableArray (qui peut partager le stockage pour des raisons de performance avec un ImmutableArray existant précédemment). Parce `b2` que les points à la `Add()` première ImmutableArray avant d’appeler cinq fois, `b2` est un immutableArray par défaut. Calling Length sur elle se bloque également avec une erreur de déreférence nulle. La bonne façon d’initialiser un ImmutableArray sans `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`appeler manuellement Ajouter est d’utiliser .

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Trouver des types pertinents de nœuds syntaxiques pour déclencher votre analyseur
Pour commencer à construire l’analyseur, d’abord comprendre quel type de SyntaxNode vous devez chercher.   Lancez le Visualiseur Syntax à partir du menu **View &#124; Autres Windows &#124; Roslyn Syntax Visualizer**.

Placez la caret de l’éditeur `b1`sur la ligne qui déclare . Vous verrez le Visualizer Syntax montre `LocalDeclarationStatement` que vous êtes dans un nœud de l’arbre syntaxe. Ce nœud `VariableDeclaration`a un , `VariableDeclarator`qui à son `EqualsValueClause`tour a un `ObjectCreationExpression`, qui à son tour a un , et enfin il ya un . Lorsque vous cliquez sur l’arbre Syntax Visualizer des nœuds, la syntaxe dans la fenêtre de l’éditeur met en évidence pour vous montrer le code représenté par ce nœud. Les noms des sous-types SyntaxNode correspondent aux noms utilisés dans la grammaire C.

## <a name="creating-the-analyzer-project"></a>Création du projet Analyzer
Parmi le menu principal choisir **File &#124; New &#124; Project ...**. Dans le **dialogue du nouveau projet,** dans le cadre des projets **C dans** la barre de navigation gauche, choisissez Extensibility, et dans le volet droit, choisissez **l’Analyseur avec** le modèle de projet Code Fix. Entrez un nom et confirmez le dialogue.

Le modèle ouvre un fichier DiagnosticAnalyzer.cs. Choisissez cet onglet tampon d’éditeur. Ce fichier a une classe d’analyseur (formé à partir `DiagnosticAnalyzer` du nom que vous avez donné le projet) qui dérive de (un type Roslyn API). Votre nouvelle classe `DiagnosticAnalyzerAttribute` a un déclarant que votre analyseur est pertinent pour la langue C de sorte que le compilateur découvre et charge votre analyseur.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Vous pouvez implémenter un analyseur à l’aide de Visual Basic qui cible le code C, et vice versa. Il est plus important dans le DiagnosticAnalyzerAttribute de choisir si votre analyseur cible une langue ou les deux. Les analyseurs plus sophistiqués qui nécessitent une modélisation détaillée de la langue ne peuvent cibler qu’une seule langue. Si votre analyseur, par exemple, ne vérifie que les noms de type ou les noms des membres du public, il peut être possible d’utiliser le modèle de langage commun que Roslyn offre sur Visual Basic et CM. Par exemple, FxCop avertit <xref:System.Runtime.Serialization.ISerializable>qu’une classe implémente, mais la classe n’a pas l’attribut est indépendant de la langue et fonctionne à la <xref:System.SerializableAttribute> fois pour Visual Basic et code C.

## <a name="initalizing-the-analyzer"></a>Initaliser l’analyseur
Faites défiler un `DiagnosticAnalyzer` peu dans `Initialize` la classe pour voir la méthode. Le compilateur appelle cette méthode lors de l’activation d’un analyseur. La méthode `AnalysisContext` prend un objet qui permet à votre analyseur d’obtenir des informations contextuelles et d’enregistrer des rappels pour les événements pour les types de code que vous souhaitez analyser.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Ouvrez une nouvelle ligne dans cette méthode et tapez le « contexte ». pour voir une liste d’achèvement Intellisense. Vous pouvez voir dans la `Register…` liste d’achèvement il existe de nombreuses méthodes pour gérer divers types d’événements. Par exemple, le `RegisterCodeBlockAction`premier, , rappelle à votre code pour un bloc, qui est généralement code entre les accolades bouclées. L’inscription à un bloc rappelle également à votre code pour le initialisateur d’un champ, la valeur donnée à un attribut, ou la valeur d’un paramètre optionnel.

Comme un `RegisterCompilationStartAction`autre exemple, , rappelle à votre code au début d’une compilation, ce qui est utile lorsque vous avez besoin de recueillir l’état sur de nombreux endroits. Vous pouvez créer une structure de données, par exemple, pour collecter tous les symboles utilisés, et chaque fois que votre analyseur est rappelé pour une syntaxe ou un symbole, vous pouvez enregistrer des informations sur chaque emplacement de votre structure de données. Lorsque vous êtes rappelé en raison de la fin de la compilation, vous pouvez analyser tous `using` les emplacements que vous avez enregistrés, par exemple, pour signaler les symboles que le code utilise à partir de chaque instruction.

En utilisant le **Visualizer Syntax**, vous avez appris que vous voulez être appelé lorsque le compilateur traite une objectCreationExpression. Vous utilisez ce code pour configurer le rappel :

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Vous vous inscrivez pour un nœud syntaxe et filtrer uniquement pour les nœuds syntaxes de création d’objets. Par convention, les auteurs d’analyseurs utilisent un lambda lors de l’enregistrement des actions, ce qui aide à garder les analyseurs apatrides. Vous pouvez utiliser la fonction Visual Studio `AnalyzeObjectCreation` Generate From **Use** pour créer la méthode. Cela génère le bon type de paramètre de contexte pour vous aussi.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Définir des propriétés pour les utilisateurs de votre analyseur
Afin que votre analyseur apparaît dans Visual Studio interface utilisateur de manière appropriée, recherchez et modifiez la ligne de code suivante pour identifier votre analyseur :

```csharp
internal const string Category = "Naming";
```

Remplacez `"Naming"` par `"API Guidance"`.

Trouvez et ouvrez ensuite le fichier Resources.resx dans votre projet à l’aide de la **Solution Explorer**. Vous pouvez mettre dans une description pour votre Analyseur, titre, etc. Vous pouvez changer la valeur `“Don’t use ImmutableArray<T> constructor”` pour tous ces pour l’instant. Vous pouvez mettre des arguments de{0} {1}formatage de chaîne dans `Diagnostic.Create()`votre chaîne ( , , etc.), et plus tard quand vous appelez, vous pouvez fournir un tableau de params d’arguments à passer.

## <a name="analyzing-an-object-creation-expression"></a>Analyse d’une expression de création d’objets
La `AnalyzeObjectCreation` méthode prend un autre type de contexte fourni par le cadre d’analyseur de code. La méthode Initialize `AnalysisContext` vous permet d’enregistrer des rappels d’action pour configurer votre analyseur. Le `SyntaxNodeAnalysisContext`, par exemple, a un `CancellationToken` que vous pouvez passer autour. Si un utilisateur commence à taper dans l’éditeur, Roslyn annulera les analyseurs en cours d’exécution pour enregistrer le travail et améliorer les performances. À titre d’exemple, ce contexte a une propriété de nœud qui renvoie le nœud syntaxe de création d’objets.

Obtenez le nœud, que vous pouvez supposer est le type pour lequel vous avez filtré l’action de nœud syntaxe:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Lancement de Visual Studio avec votre analyseur la première fois
Lancez Visual Studio en construisant et exécutant votre analyseur (appuyez sur **F5**). Parce que le projet de démarrage dans le **Solution Explorer** est le projet VSIX, l’exécution de votre code construit votre code et un VSIX, puis lance Visual Studio avec celui VSIX installé. Lorsque vous lancez Visual Studio de cette façon, il se lance avec une ruche de registre distincte de sorte que votre utilisation principale de Visual Studio ne sera pas affectée par vos instances de test tout en construisant des analyseurs. La première fois que vous lancez de cette façon, Visual Studio fait plusieurs initialisations similaires à la première fois que vous avez lancé Visual Studio après l’avoir installé.

 Créez un projet de console, puis entrez le code de tableau dans votre méthode Principale d’applications de console :

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Les lignes de `ImmutableArray` code avec ont des gribouillis parce que vous `using` avez besoin d’obtenir le paquet Immuable NuGet et ajouter une déclaration à votre code. Appuyez sur le bouton pointeur droit sur le nœud de projet dans la **solution Explorer** et choisissez **Manage NuGet Packages ...**. Dans le gestionnaire NuGet, tapez "Immutable" dans la boîte de recherche, et choisissez l’élément "System.Collections.Immutable" (ne choisissez pas "Microsoft.Bcl.Immutable") dans la vitre gauche et appuyez sur le bouton Installer dans la vitre droite. L’installation du paquet ajoute une référence à vos références de projet.

Vous voyez encore des gribouillis rouges sous `ImmutableArray`, alors placez le caret dans cet identifiant et appuyez sur **CTRL.** (période) pour mettre en place le menu `using` de correction suggéré et choisir d’ajouter l’instruction appropriée.

**Enregistrer tous et fermer** la deuxième instance de Visual Studio pour l’instant pour vous mettre dans un état propre pour continuer.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Terminer l’analyseur à l’aide d’Edit et Continuer
Dans le premier cas de Visual Studio, définissez `AnalyzeObjectCreation` un point d’arrêt au début de votre méthode en appuyant sur **F9** avec la caret sur la première ligne.

Lancez à nouveau votre analyseur avec **F5**, et dans le second cas de Visual Studio, ouvrez à nouveau votre application de console que vous avez créée la dernière fois.

Vous revenez à la première instance de Visual Studio au point d’arrêt parce que le compilateur Roslyn a vu une expression de création d’objet et a appelé dans votre analyseur.

**Obtenez le nœud de création d’objet.** Franchir la ligne `objectCreation` qui définit la variable en appuyant sur **F10**, et dans la **fenêtre immédiate** évaluer l’expression `“objectCreation.ToString()”`. Vous voyez que le nœud syntaxe `"new ImmutableArray<int>()"`les points variables à est le code , juste ce que vous recherchez.

**Obtenez ImmutableArray\<T> Type objet.** Vous devez vérifier si le type en cours de création est ImmutableArray. Tout d’abord, vous obtenez l’objet qui représente ce type. Vous vérifiez les types en utilisant le modèle sémantique pour vous assurer que vous avez exactement le bon type, et vous ne comparez pas la chaîne de ToString (). Entrez la ligne de code suivante à la fin de la fonction :

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Vous désignez les types génériques dans les métadonnées avec les backquotes (') et le nombre de paramètres génériques. C’est pourquoi vous ne voyez pas "... ImmutableArray\<T>" au nom des métadonnées.

Le modèle sémantique a beaucoup de choses utiles sur elle qui vous permettent de poser des questions sur les symboles, le flux de données, la durée de vie variable, etc. Roslyn sépare les nœuds syntaxiques du modèle sémantique pour diverses raisons d’ingénierie (performance, modélisation du code erroné, etc.). Vous souhaitez que le modèle de compilation recherche des informations contenues dans les références pour une comparaison précise.

Vous pouvez faire glisser le pointeur d’exécution jaune sur le côté gauche de la fenêtre de l’éditeur. Faites glisser jusqu’à la `objectCreation` ligne qui définit la variable et étape sur votre nouvelle ligne de code à l’aide de **F10**. Si vous planez le `immutableArrayOfType`pointeur de la souris sur la variable, vous voyez que nous avons trouvé le type exact dans le modèle sémantique.

**Obtenez le type d’expression de création d’objet.** "Type" est utilisé de plusieurs façons dans cet article, mais cela signifie que si vous avez "nouveau Foo" expression, vous devez obtenir un modèle de Foo. Vous devez obtenir le type de l’expression de création d’objet pour voir si c’est le type ImmutableArray\<T>. Utilisez à nouveau le modèle sémantique pour obtenir des informations de symbole pour le symbole de type (ImmutableArray) dans l’expression de création d’objet. Entrez la ligne de code suivante à la fin de la fonction :

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Parce que votre analyseur a besoin de gérer le code incomplet ou incorrect dans les tampons de l’éditeur (par exemple, il ya une déclaration manquante), `using` vous devriez vérifier pour `symbolInfo` être `null`. Vous devez obtenir un type nommé (INamedTypeSymbol) à partir de l’objet d’information du symbole pour terminer l’analyse.

**Comparez les types.** Parce qu’il ya un type générique ouvert de T que nous recherchons, et le type dans le code est un type générique concret, `immutableArrayOfTType`vous interrogez les informations de symbole pour ce que le type est construit à partir (un type générique ouvert) et de comparer ce résultat avec . Entrez ce qui suit à la fin de la méthode :

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Signalez le diagnostic.** Signaler le diagnostic est assez facile. Vous utilisez la règle créée pour vous dans le modèle de projet, qui est défini avant la méthode Initialize. Parce que cette situation dans le code est une erreur, `DiagnosticSeverity.Warning` vous pouvez changer la `DiagnosticSeverity.Error` ligne qui a para initialisé La règle pour remplacer (squiggle vert) par (squiggle rouge). Le reste de la Règle est parasité à partir des ressources que vous avez modifiées vers le début de la procédure pas à pas. Vous devez également signaler l’emplacement de l’échiquage, qui est l’emplacement de la spécification de type de la création d’objet. Entrez ce `if` code dans le bloc :

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Votre fonction devrait ressembler à ceci (peut-être formaté différemment):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

Enlevez le point d’arrêt afin que vous puissiez voir votre analyseur travailler (et arrêter de retourner à la première instance de Visual Studio). Faites glisser le pointeur d’exécution au début de votre méthode, et appuyez sur **F5** pour continuer l’exécution. Lorsque vous revenez à la deuxième instance de Visual Studio, le compilateur va commencer à examiner le code à nouveau, et il appellera dans votre analyseur. Vous pouvez voir un `ImmutableType<int>`squiggle sous .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Ajout d’un « correctif de code » pour la question du code
Avant de commencer, fermez la deuxième instance de Visual Studio et arrêtez de débogage dans le premier cas de Visual Studio (où vous développez l’analyseur).

**Ajoutez une nouvelle classe.** Utilisez le menu raccourci (bouton pointeur droit) sur votre nœud de projet dans la Solution Explorer et choisissez d’ajouter un nouvel article. Ajouter une `BuildCodeFixProvider`classe appelée . Cette classe doit `CodeFixProvider`dériver de , et vous aurez besoin d’utiliser **CTRL.** (période) pour invoquer le `using` correctif de code qui ajoute la bonne instruction. Cette classe doit également être `ExportCodeFixProvider` annotée avec attribut, `using` et vous `LanguageNames` devrez ajouter une déclaration pour résoudre l’enum. Vous devez avoir un fichier de classe avec le code suivant en elle:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Stub membres dérivés.** Maintenant, placez la caret de `CodeFixProvider` l’éditeur dans l’identifiant et appuyez sur **CTRL.** (période) pour talonner la mise en œuvre de cette classe de base abstraite. Cela génère une propriété et une méthode pour vous.

**Implémenter la propriété.** Remplissez `FixableDiagnosticIds` le corps `get` de la propriété avec le code suivant :

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn rassemble des diagnostics et des correctifs en faisant correspondre ces identificateurs, qui ne sont que des cordes. Le modèle de projet a généré un ID de diagnostic pour vous, et vous êtes libre de le modifier. Le code dans la propriété renvoie juste l’ID de la classe d’analyseur.

**La méthode RegisterCodeFixAsync prend un contexte.** Le contexte est important parce qu’un correctif de code peut s’appliquer à plusieurs diagnostics, ou il pourrait y avoir plus d’un problème sur une ligne de code. Si vous tapez "contexte". dans le corps de la méthode, la liste d’achèvement Intellisense vous montrera quelques membres utiles. Il ya un membre CancellationToken que vous pouvez vérifier pour voir si quelque chose veut annuler le correctif. Il y a un membre de Document qui a beaucoup de membres utiles et vous permet d’arriver au projet et aux objets de modèle de solution. Il ya un membre Span qui est le début et la fin de l’emplacement du code spécifié lorsque vous avez signalé le diagnostic.

**Faites de la méthode être async.** La première chose que vous devez faire est `async` de fixer la déclaration de méthode générée pour être une méthode. Le correctif de code pour stubbing la mise en `async` œuvre d’une classe abstraite n’inclut pas le mot clé, même si la méthode retourne un `Task`.

**Obtenez la racine de l’arbre syntaxe.** Pour modifier le code, vous devez produire un nouvel arbre syntaxe avec les modifications apportées par votre correctif de code. Vous avez `Document` besoin de `GetSyntaxRootAsync`la du contexte pour appeler . Il s’agit d’une méthode async parce qu’il ya un travail inconnu pour obtenir l’arbre de syntaxe, peut-être y compris l’obtention du fichier à partir du disque, l’analyser, et la construction du modèle de code Roslyn pour elle. L’interface utilisateur Visual Studio doit être `async` réactive pendant cette période, ce qui permet d’utiliser. Remplacer la ligne de code dans la méthode par les éléments suivants :

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Trouvez le nœud avec le problème.** Vous passez dans la durée du contexte, mais le nœud que vous trouvez peut ne pas être le code que vous devez changer. Le diagnostic rapporté ne fournissait que la portée pour l’identifiant de type (où le `new` squiggle appartenait), mais vous devez remplacer l’expression entière de création d’objet, y compris le keywoard au début et les parenthèses à la fin. Ajoutez le code suivant à votre méthode (et utilisez **CTRLMD.** pour ajouter `using` une `ObjectCreationExpressionSyntax`déclaration pour ):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Enregistrez votre correctif de code pour l’interface utilisateur de l’ampoule.** Lorsque vous enregistrez votre correctif de code, Roslyn se branche automatiquement sur l’interface utilisateur de l’ampoule Visual Studio. Les utilisateurs finaux verront qu’ils peuvent utiliser **CTRL.** (période) lorsque votre analyseur gicle `ImmutableArray<T>` une mauvaise utilisation de constructeur. Parce que votre fournisseur de correctifs de code ne s’exécute que lorsqu’il y a un problème, vous pouvez supposer que vous avez l’expression de création d’objet que vous recherchiez. À partir du paramètre contextuelle, vous pouvez enregistrer le `RegisterCodeFixAsync` nouveau correctif de code en ajoutant le code suivant à la fin de la méthode :

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Vous devez placer la caret de l’éditeur dans l’identifiant, `CodeAction`puis utiliser **CTRL.** (période) pour ajouter `using` l’instruction appropriée pour ce type.

Placez ensuite la prise en `ChangeToImmutableArrayEmpty` charge de l’éditeur dans l’identifiant et utilisez **CTRLMD.** nouveau pour générer ce talon de méthode pour vous.

Ce dernier extrait de code que vous avez ajouté `CodeAction` enregistre le correctif de code en passant un et l’ID de diagnostic pour le type de problème trouvé. Dans cet exemple, il n’y a qu’un seul ID diagnostique pour lequel ce code fournit des correctifs, de sorte que vous pouvez simplement passer le premier élément du tableau des pièces d’identité diagnostiques. Lorsque vous `CodeAction`créez le , vous passez dans le texte que l’interface utilisateur d’ampoule doit utiliser comme une description du correctif de code. Vous passez également dans une fonction qui prend un AnnulationToken et retourne un nouveau document. Le nouveau document a un nouvel arbre syntaxe `ImmutableArray.Empty`qui comprend votre code patché qui appelle . Cet extrait de code utilise un lambda afin qu’il puisse se fermer sur le nœud d’objet et le document du contexte.

**Construire le nouvel arbre syntaxe.** Dans `ChangeToImmutableArrayEmpty` la méthode dont le talon que vous `ImmutableArray<int>.Empty;`avez généré plus tôt, entrez la ligne de code: . Si vous consultez à nouveau la fenêtre de l’outil Syntax Visualizer, vous pouvez voir que cette syntaxe est un nœud SimpleMemberAccessExpression. C’est ce que cette méthode doit construire et retourner dans un nouveau document.

La première `ChangeToImmutableArrayEmpty` modification est `async` `Task<Document>` d’ajouter avant parce que les générateurs de code ne peut pas supposer que la méthode doit être async.

Remplissez le corps avec le code suivant de sorte que votre méthode ressemble à ce qui suit:

```csharp

private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Vous devrez mettre la caret de `SyntaxGenerator` l’éditeur dans l’identifiant et utiliser **CTRL.** (période) pour ajouter `using` l’instruction appropriée pour ce type.

Ce code `SyntaxGenerator`utilise , qui est un type très utile pour la construction de nouveau code. Après avoir obtenu un générateur pour le `ChangeToImmutableArrayEmpty` `MemberAccessExpression`document qui a le problème de code, appelle, en passant le type qui a le membre que nous voulons accéder et en passant le nom du membre comme une chaîne.

Ensuite, la méthode va chercher la racine du document, et parce que cela peut impliquer un travail arbitraire dans le cas général, le code attend cet appel et passe le jeton d’annulation. Les modèles de code Roslyn sont immuables, comme travailler avec une chaîne .NET; lorsque vous mettez à jour la chaîne, vous obtenez un nouvel objet de chaîne en retour. Lorsque vous `ReplaceNode`appelez, vous obtenez en arrière un nouveau nœud racine. La plupart de l’arbre syntaxe est partagée `objectCreation` (parce qu’il `memberAccess` est immuable), mais le nœud est remplacé par le nœud, ainsi que tous les nœuds parent jusqu’à la racine de l’arbre syntaxe.

## <a name="trying-your-code-fix"></a>Essayer votre correctif de code
Vous pouvez maintenant appuyer sur **F5** pour exécuter votre analyseur dans un deuxième cas de Visual Studio. Ouvrez le projet de console que vous avez utilisé avant. Maintenant, vous devriez voir l’ampoule apparaissent où votre nouvelle expression de création d’objet est pour `ImmutableArray<int>`. Si vous appuyez sur **CTRL.** (période), alors vous verrez votre correctif de code, et vous verrez un aperçu de différence de code généré automatiquement dans l’interface utilisateur d’ampoule. Roslyn crée ça pour toi.

Astuce Pro: Si vous lancez la deuxième instance de Visual Studio, et que vous ne voyez pas l’ampoule avec votre correctif de code, alors vous devrez peut-être effacer le cache de composant Visual Studio. Effacer le cache oblige Visual Studio à réexaminer les composants, de sorte que Visual Studio devrait alors ramasser votre dernier composant. Tout d’abord, arrêtez la deuxième instance de Visual Studio. Ensuite, dans Windows Explorer, allez à votre\\ répertoire utilisateur (c:'users<userid\>) et trouver AppData-Local-Microsoft-VisualStudio -14.0Roslyn\\. Dans ce répertoire, supprimez le sous-répertoire ComponentModelCache. Le "14" change de version en version avec Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Talk Video et Finish Code Project
Vous pouvez voir cet exemple développé et discuté plus loin dans [ce discours](https://channel9.msdn.com/events/Build/2015/3-725). La conférence démontre l’analyseur de travail et vous guide à travers la construction.

Vous pouvez voir tout le code fini [ici](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Les sous-dossiers DoNotUseImmutableArrayCollectionInitializer et DoNotUseImmutableArrayCtor ont chacun un fichier C pour trouver des problèmes et un fichier C qui implémente les correctifs de code qui apparaissent dans l’interface utilisateur de l’ampoule Visual Studio. Notez que le code fini a un peu plus d’abstraction pour éviter d’aller chercher l’objet immutableArray\<T> type encore et encore. Il utilise des actions enregistrées imbriquées pour enregistrer l’objet de type dans un contexte qui est disponible chaque fois que les sous-actions (analyser la création d’objets et analyser les initialisations de collecte) s’exécutent.

## <a name="see-also"></a>Voir aussi
[\\-Construire 2015 parler](https://channel9.msdn.com/events/Build/2015/3-725)
[Code terminé sur GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md) 
Autres documents sur le site 
[GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)[FxCop règles mises en œuvre avec des analyseurs Roslyn sur GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
