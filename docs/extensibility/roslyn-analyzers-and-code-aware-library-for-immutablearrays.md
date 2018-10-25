---
title: Analyseurs de Roslyn et bibliothèque de Code pour ImmutableArrays | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 075f3391a155938082847c708f831d0587cf54fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907480"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analyseurs de Roslyn et bibliothèque de code pour ImmutableArrays

Le [.NET Compiler Platform](https://github.com/dotnet/roslyn) (« Roslyn ») vous permet de générer des bibliothèques de code prenant en charge.  Une bibliothèque de code fournit des fonctionnalités que vous pouvez utiliser et des outils (analyseurs de Roslyn) pour vous aider à utiliser la bibliothèque de façon optimale, ou pour éviter les erreurs.  Cette rubrique vous montre comment créer un analyseur Roslyn de monde réel pour intercepter les erreurs courantes lors de l’utilisation du [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) package NuGet.  L’exemple montre également comment fournir un correctif de code pour un problème de code identifié par l’analyseur.  Utilisateurs voient les correctifs de code dans l’ampoule Visual Studio l’interface utilisateur et peuvent appliquer un correctif pour le code automatiquement.

## <a name="get-started"></a>Prise en main

Vous avez besoin de ce qui suit pour générer cet exemple :

* Visual Studio 2015 (pas une édition Express) ou une version ultérieure.  Vous pouvez utiliser la version gratuite [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  Vous pouvez également, lors de l’installation de Visual Studio, vérifier **outils d’extensibilité Visual Studio** sous **outils courants** pour installer le Kit de développement en même temps.  Si vous avez déjà installé Visual Studio, vous pouvez également installer ce SDK en accédant au menu principal **fichier** > **New** > **projet**, en choisissant **c#** dans le volet de navigation gauche, puis en sélectionnant **extensibilité**.  Lorsque vous choisissez le «**installer les outils d’extensibilité de Visual Studio**« modèle de projet de fil d’Ariane, vous êtes invité à télécharger et installer le Kit de développement.
* [.NET compiler Platform (« Roslyn ») SDK](http://aka.ms/roslynsdktemplates).  Vous pouvez également installer ce SDK en accédant au menu principal **fichier** > **New** > **projet**, en choisissant l’option **c#** dans le volet de navigation gauche, puis en sélectionnant **extensibilité**.  Lorsque vous choisissez «**télécharger le SDK .NET Compiler Platform**« modèle de projet de fil d’Ariane, vous êtes invité à télécharger et installer le Kit de développement.  Ce SDK inclut le [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Ce permet d’outil extrêmement utile que vous savez quels types de modèle de code vous devez rechercher dans votre analyseur.  Les appels d’infrastructure analyseur dans votre code pour les types de modèle de code spécifique, afin que votre code s’exécute lorsque cela est nécessaire uniquement et pouvez vous concentrer uniquement sur l’analyse de code approprié.

## <a name="whats-the-problem"></a>Quel est le problème ?

Imaginez que vous fournissez une bibliothèque avec ImmutableArray (par exemple, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) prennent en charge.  Les développeurs c# ont beaucoup d’expérience avec les tableaux .NET.  Toutefois, en raison de la nature des techniques ImmutableArrays et l’optimisation utilisées dans l’implémentation, intuitions développeur c# entraînent les utilisateurs de votre bibliothèque d’écrire du code rompu, comme expliqué ci-dessous.  En outre, les utilisateurs ne voient pas leurs erreurs jusqu’au moment de l’exécution, ce qui n’est pas l’expérience de qualité qu’ils sont habitués dans Visual Studio avec .NET.

Les utilisateurs sont familiarisés avec l’écriture de code semblable au suivant :

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Création de tableaux vides à remplir avec les lignes de code et à l’aide de la syntaxe d’initialiseur de collection sont très familiers aux développeurs c#.  Toutefois, écrire le même code pour un ImmutableArray se bloque lors de l’exécution :

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

La première erreur est en raison de l’implémentation de ImmutableArray à l’aide un struct pour encapsuler le stockage de données sous-jacent. Les structures doivent avoir des constructeurs de sans paramètre afin que `default(T)` expressions peuvent retourner des structs avec tous les zéro ou null membres.  Lorsque le code accède à `b1.Length`, il existe un moment de l’exécution au déréférencement d’erreur, car il n’existe aucun groupe de stockage sous-jacent du struct ImmutableArray.  La méthode correcte pour créer un ImmutableArray vide est `ImmutableArray<int>.Empty`.

L’erreur avec les initialiseurs de collection se produit, car le `ImmutableArray.Add` méthode retourne les nouvelles instances chaque fois que vous l’appelez.  Étant donné que ImmutableArrays ne changent jamais, lorsque vous ajoutez un nouvel élément, vous obtenez un nouvel objet ImmutableArray (qui peut-être partager le stockage pour des raisons de performances avec un ImmutableArray existe déjà).  Étant donné que `b2` pointe vers le premier ImmutableArray avant d’appeler `Add()` cinq fois, `b2` est une valeur par défaut ImmutableArray.  L’appel longueur dessus également les incidents avec une valeur null déréférencer l’erreur.  La méthode correcte pour initialiser un ImmutableArray sans ajouter manuellement l’appel est d’utiliser `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Rechercher des types de nœud pour déclencher votre analyseur de syntaxe pertinentes

 Pour commencer à créer l’analyseur, tout d’abord déterminer quel type de SyntaxNode sont nécessaires à rechercher. Lancer le **visualiseur de syntaxe** à partir du menu **vue** > **Windows autres** > **Roslyn Syntax Visualizer**.

Placer le signe insertion de l’éditeur sur la ligne qui déclare `b1`.  Vous verrez le visualiseur de syntaxe montre que vous êtes dans un `LocalDeclarationStatement` nœud de l’arborescence de syntaxe.  Ce nœud possède un `VariableDeclaration`, qui à son tour possède un `VariableDeclarator`, qui à son tour possède un `EqualsValueClause`, enfin un `ObjectCreationExpression`.  Lorsque vous cliquez dans l’arborescence de visualiseur de syntaxe de nœuds, la syntaxe dans la fenêtre de l’éditeur met en surbrillance pour vous montrer le code représenté par ce nœud.  Les noms des types SyntaxNode sub correspondent aux noms utilisés dans la grammaire c#.

## <a name="create-the-analyzer-project"></a>Créer le projet de l’analyseur

Dans le menu principal, choisissez **fichier** > **New** > **projet**.  Dans le **nouveau projet** boîte de dialogue, sous **c#** projets dans la barre de navigation de gauche, choisissez **extensibilité**, puis dans le volet droit, choisissez le **Analyzer avec Correctif de code** modèle de projet.  Entrez un nom et confirmez la boîte de dialogue.

Le modèle s’ouvre un *DiagnosticAnalyzer.cs* fichier.  Choisissez cet éditeur onglet de la mémoire tampon.  Ce fichier contient une classe d’analyseur (formé à partir du nom que vous avez donné le projet) qui dérive de `DiagnosticAnalyzer` (un type de l’API de Roslyn).  Votre nouvelle classe a un `DiagnosticAnalyzerAttribute` déclarer votre analyseur est pertinente pour le langage c# afin que le compilateur détecte et charge votre analyseur.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Vous pouvez implémenter un analyseur à l’aide de Visual Basic qui cible le code c#, et vice versa.  Il est plus important dans le DiagnosticAnalyzerAttribute pour choisir si votre analyseur cible un langage ou les deux.  Les analyseurs plus sophistiquées qui nécessitent une modélisation détaillée du langage peuvent cibler uniquement un seul langage.  Si votre analyseur, par exemple, uniquement vérifie les noms de type ou membre public, il peut être possible d’utiliser le modèle de langage commun que roslyn offre sur Visual Basic et c#.  Par exemple, FxCop vous avertit qu’une classe implémente <xref:System.Runtime.Serialization.ISerializable>, mais la classe n’a pas la <xref:System.SerializableAttribute> attribut est indépendant du langage et fonctionne pour le code Visual Basic et c#.

## <a name="initalize-the-analyzer"></a>Initialiser l’analyseur

 Faites défiler un peu le `DiagnosticAnalyzer` classe pour voir le `Initialize` (méthode).  Le compilateur appelle cette méthode lors de l’activation d’un analyseur.  La méthode accepte un `AnalysisContext` objet qui permet à votre analyseur pour obtenir des informations de contexte et enregistrer des rappels pour les événements pour les types de code que vous souhaitez analyser.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Ouvrez une nouvelle ligne dans cette méthode et type « le contexte. » Pour afficher une liste de saisie semi-automatique IntelliSense.  Vous pouvez voir dans la liste de saisie semi-automatique, il existe de nombreux `Register...` méthodes pour gérer différents types d’événements.  Par exemple, le, `RegisterCodeBlockAction`, appelle de nouveau votre code pour un bloc, ce qui est généralement le code entre accolades.  L’inscription pour un bloc également rappelle à votre code pour l’initialiseur de champ, la valeur donnée à un attribut ou la valeur d’un paramètre facultatif.

Autre exemple, `RegisterCompilationStartAction`, appelle de nouveau votre code au début d’une compilation, ce qui est utile lorsque vous avez besoin afin de collecter les États sur nombreux emplacements.  Vous pouvez créer une structure de données, par exemple, pour collecter tous les symboles utilisés, et chaque fois que votre analyseur est rappelé une syntaxe ou un symbole, vous pouvez enregistrer des informations relatives à chaque emplacement dans votre structure de données.  Lorsque vous êtes rappelé en raison de la fin de la compilation, vous pouvez analyser tous les emplacements que vous avez enregistré, par exemple, pour signaler les symboles que le code utilise à partir de chaque `using` instruction.

À l’aide de la **visualiseur de syntaxe**, vous avez appris que vous souhaitez être appelée quand le compilateur traite une ObjectCreationExpression.  Ce code vous permet de définir le rappel :

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Vous inscrire pour un nœud de syntaxe et d’un filtre pour seulement les nœuds de syntaxe de création objet.  Par convention, les auteurs de l’analyseur utilisent une expression lambda lorsque l’enregistrement des actions, ce qui vous aide à garder les analyseurs sans état.  Vous pouvez utiliser la fonctionnalité de Visual Studio **générer à partir de l’utilisation** pour créer le `AnalyzeObjectCreation` (méthode).  Cela génère trop le type de paramètre de contexte approprié pour vous.

## <a name="set-properties-for-users-of-your-analyzer"></a>Définir les propriétés pour les utilisateurs de votre analyseur

Afin que votre analyseur s’affiche dans l’interface utilisateur de Visual Studio en conséquence, recherchez et modifiez la ligne suivante du code pour identifier votre analyseur :

```csharp
internal const string Category = "Naming";
```

Modification `"Naming"` à `"API Guidance"`.

Ensuite rechercher et ouvrir le *Resources.resx* fichier dans votre projet en utilisant le **l’Explorateur de solutions**.  Vous pouvez placer dans une description pour votre analyseur, titre, etc.  Vous pouvez modifier la valeur de tous ces `"Don't use ImmutableArray<T> constructor"` pour l’instant.  Vous pouvez placer les arguments dans votre chaîne de mise en forme de chaîne ({0}, {1}, etc.) et versions ultérieures, lorsque vous appelez `Diagnostic.Create()`, vous pouvez fournir un `params` tableau d’arguments à passer.

## <a name="analyze-an-object-creation-expression"></a>Analyser une expression de création d’objet

Le `AnalyzeObjectCreation` méthode prend un autre type de contexte fourni par l’infrastructure d’analyseur de code.  Le `Initialize` la méthode `AnalysisContext` vous permet d’enregistrer des rappels d’action pour définir votre analyseur.  Le `SyntaxNodeAnalysisContext`, par exemple, a un `CancellationToken` que vous pouvez transmettre autour.  Si un utilisateur commence à taper dans l’éditeur, Roslyn annulera les analyseurs en cours d’exécution pour enregistrer le travail et améliorer les performances.  Autre exemple, ce contexte a une propriété de nœud qui renvoie le nœud de syntaxe de la création d’objet.

Obtenir le nœud, vous pouvez supposer est le type pour lequel vous avez filtré de l’action de nœud de syntaxe :

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Lancez Visual Studio avec votre analyseur de la première fois

Lancez Visual Studio en créant et en exécutant votre analyseur (appuyez sur **F5**).  Étant donné que le démarrage du projet dans le **l’Explorateur de solutions** est le projet VSIX, vos builds de code en cours d’exécution votre code et une extension VSIX et puis lance Visual Studio avec cette extension VSIX installé.  Lorsque vous lancez Visual Studio de cette façon, il lance une ruche de Registre distinctes afin que votre utilisation principale de Visual Studio n’est pas affectée par vos instances de tests lors de la génération d’analyseurs.  La première fois que vous lancez de cette façon, Visual Studio effectue plusieurs initialisations similaires à la première fois Visual Studio après l’avoir installé.

Créez un projet console, puis entrez le code de tableau dans votre méthode principale d’applications console :

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Les lignes de code avec `ImmutableArray` ont des tildes, car vous avez besoin obtenir le package NuGet immuable et ajoutez un `using` instruction à votre code.  Appuyez sur le bouton droit du pointeur sur le nœud de projet dans le **l’Explorateur de solutions** et choisissez **gérer les Packages NuGet**.  Dans le gestionnaire NuGet, tapez « Immuable » dans la zone de recherche, choisissez l’élément **System.Collections.Immutable** (ne choisissez pas **Microsoft.Bcl.Immutable**) dans le volet gauche et appuyez sur la  **Installer** bouton dans le volet droit.  Installation du package ajoute une référence à vos références de projet.

Vous voyez toujours des soulignements ondulés rouges sous `ImmutableArray`, vous devez donc placer le signe insertion dans cet identificateur appuyez sur **Ctrl**+**.** (point) pour faire apparaître le menu de correctif suggéré et choisissez Ajouter approprié `using` instruction.

**Enregistrez et fermez** la deuxième instance de Visual Studio pour le moment pour vous placer dans un état propre pour continuer.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Terminer l’analyseur à l’aide de modifier et continuer

Dans la première instance de Visual Studio, définissez un point d’arrêt au début de votre `AnalyzeObjectCreation` méthode en appuyant sur **F9** avec le signe insertion sur la première ligne.

Lancez votre analyseur à nouveau avec **F5**et dans la deuxième instance de Visual Studio, ouvrez à nouveau votre application de console que vous avez créé la dernière fois.

Vous renvoyer à la première instance de Visual Studio sur le point d’arrêt, car le compilateur Roslyn vu une expression de création d’objet et appelée dans votre analyseur.

**Obtient le nœud de la création d’objet.** Ignorer la ligne qui définit la `objectCreation` variable en appuyant sur **F10**, puis, dans le **fenêtre exécution** évaluer l’expression `"objectCreation.ToString()"`.  Vous voyez que la variable pointe vers le nœud de syntaxe est le code `"new ImmutableArray<int>()"`, simplement ce que vous recherchez.

**Obtenir ImmutableArray < T\> objet de Type.** Vous devez vérifier si le type en cours de création est ImmutableArray.  Tout d’abord, vous obtenez l’objet qui représente ce type.  Vous vérifiez les types à l’aide du modèle sémantique pour vous assurer d’avoir exactement le type approprié, et vous ne comparez la chaîne à partir de `ToString()`.  Entrez la ligne de code à la fin de la fonction suivante :

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Vous désignez des types génériques dans les métadonnées avec backquotes (') et le nombre de paramètres génériques.  C’est pourquoi vous ne voyez pas »... ImmutableArray\<T > » dans le nom des métadonnées.

Le modèle sémantique a beaucoup de choses utiles qui vous permettent de poser des questions sur les symboles, flux de données, durée de vie des variable, etc.  Roslyn sépare les nœuds de syntaxe à partir du modèle sémantique pour diverses raisons engineering (performances, de modélisation les erreurs de code, etc.).  Vous souhaitez le modèle de compilation pour rechercher des informations contenues dans les références pour la comparaison précis.

Vous pouvez faire glisser le pointeur d’exécution jaune sur le côté gauche de la fenêtre d’éditeur.  Faites glisser jusqu'à la ligne qui définit la `objectCreation` variable et pas à pas principal de votre nouvelle ligne de code à l’aide **F10**.  Si vous placez le pointeur de la souris sur la variable `immutableArrayOfType`, vous voyez que nous avons trouvé le type exact dans le modèle sémantique.

**Obtenir le type de l’expression création d’objet.** « Type » est utilisé de plusieurs façons dans cet article, mais cela signifie que si vous avez « nouveau Foo » expression, vous devez obtenir un modèle de Foo.  Vous devez obtenir le type de l’expression de création d’objet pour voir si elle est ImmutableArray\<T > type.  Utilisez le modèle sémantique à nouveau pour obtenir des informations de symbole pour le symbole de type (ImmutableArray) dans l’expression de création d’objet.  Entrez la ligne de code à la fin de la fonction suivante :

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Étant donné que votre analyseur doit gérer code incomplète ou incorrect dans les mémoires tampons de l’éditeur (par exemple, il manque une `using` instruction), vous devez rechercher `symbolInfo` en cours `null`.  Vous devez obtenir un type nommé (INamedTypeSymbol) à partir de l’objet d’informations de symbole à la fin de l’analyse.

**Comparez les Types.** Étant donné qu’est un type générique ouvert de T qui nous intéresse, et le type dans le code est un type générique concrète, vous interroger les informations de symbole pour le type est construit à partir de (un type générique ouvert) et comparer ce résultat avec `immutableArrayOfTType`.  Entrez les informations suivantes à la fin de la méthode :

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Signaler le Diagnostic.** Le diagnostic de création de rapports est assez facile.  Vous utilisez la règle créée pour vous dans le modèle de projet, qui est défini avant la méthode Initialize.  Étant donné que cette situation dans le code est une erreur, vous pouvez modifier la ligne qui a initialisé la règle à remplacer `DiagnosticSeverity.Warning` (tilde vert) avec `DiagnosticSeverity.Error` (ligne ondulée rouge).  Le reste de la règle s’initialise à partir des ressources que vous avez modifié près du début de la procédure pas à pas.  Vous devez également signaler l’emplacement de la ligne ondulée, qui est l’emplacement de spécification du type de l’expression de création d’objet.  Entrez ce code dans le `if` bloc :

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Votre fonction doit ressembler à ceci (peut-être mis en forme différemment) :

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Supprimer le point d’arrêt afin que vous pouvez voir votre utilisation de l’analyseur (et arrêter le renvoi à la première instance de Visual Studio).  Faites glisser le pointeur d’exécution au début de votre méthode, puis appuyez sur **F5** pour continuer l’exécution.  Lorsque vous revenez à la deuxième instance de Visual Studio, le compilateur commence à examiner le code à nouveau, et elle appellera votre analyseur.  Vous pouvez voir une ligne ondulée sous `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Ajout d’un correctif de Code « » pour le problème de Code

Avant de commencer, fermez la deuxième instance de Visual Studio et arrêter le débogage dans la première instance de Visual Studio (où vous développez l’analyseur).

**Ajoutez une nouvelle classe.** Utilisez le menu contextuel (bouton droit du pointeur) sur le nœud de votre projet dans le **l’Explorateur de solutions** et choisissez Ajouter un nouvel élément.  Ajoutez une classe appelée `BuildCodeFixProvider`.  Cette classe doit dériver de `CodeFixProvider`, et vous devrez utiliser **Ctrl**+**.** (période) pour appeler la correction du code qui ajoute la bonne `using` instruction.  Cette classe doit également être annotés avec `ExportCodeFixProvider` attribut et vous devez ajouter un `using` instruction pour résoudre le `LanguageNames` enum.  Vous devez avoir un fichier de classe par le code suivant dans celui-ci :

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Épargner des membres dérivés.** À présent, placer le signe insertion de l’éditeur dans l’identificateur `CodeFixProvider` et appuyez sur **Ctrl**+**.** (point) pour remplacer l’implémentation de cette classe de base abstraite.  Cela génère une propriété et une méthode pour vous.

**Implémentez la propriété.** Renseignez le `FixableDiagnosticIds` la propriété `get` corps avec le code suivant :

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn réunit les diagnostics et les correctifs en mettant en correspondance ces identificateurs, qui sont simplement des chaînes.  Le modèle de projet généré un ID de diagnostic pour vous, et vous êtes libre de le modifier.  Le code dans la propriété retourne simplement l’ID de la classe d’analyseur.

**La méthode RegisterCodeFixAsync prend un contexte.** Le contexte est important, car un correctif de code peut s’appliquer à plusieurs tests de diagnostic, ou il peut y avoir plus d’un problème sur une ligne de code.  Si vous tapez « contexte ». dans le corps de la méthode, la liste de saisie semi-automatique IntelliSense vous affichera certains membres utiles.  Il existe un membre CancellationToken que vous pouvez vérifier pour voir si quelque chose souhaite annuler le correctif.  Il existe un membre de Document qui comporte un grand nombre de membres utiles et vous permet d’obtenir pour les objets de modèle de projet et solution.  Il existe une étendue membre qui représente le début et fin de l’emplacement du code spécifié lorsque vous avez signalé le diagnostic.

**Rendre la méthode être asynchrone.** La première chose à faire est de corriger la déclaration de méthode générée pour être un `async` (méthode).  La correction du code pour l’implémentation d’une classe abstraite d’opérations stub n’inclut pas le `async` mot clé même si la méthode retourne un `Task`.

**Obtenir la racine de l’arborescence de syntaxe.** Pour modifier le code que vous avez besoin pour produire une nouvelle arborescence de syntaxe avec les modifications de votre correctif de code rend.  Vous devez le `Document` à partir du contexte d’appeler `GetSyntaxRootAsync`.  Il s’agit d’une méthode async, car le travail inconnu pour obtenir de l’arborescence de syntaxe, en incluant éventuellement l’obtention du fichier à partir du disque, l’analyser et générer le modèle de code de Roslyn pour qu’il soit.  L’interface utilisateur de Visual Studio doit être réactif pendant ce temps, lesquelles `async` active.  Remplacez la ligne de code dans la méthode avec les éléments suivants :

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Recherchez le nœud avec le problème.** Vous passez dans l’étendue du contexte, mais le nœud que vous trouvez peut-être pas le code que vous devez modifier.  Le diagnostic signalé fourni uniquement l’étendue pour l’identificateur de type (où la ligne ondulée appartenait), mais vous devez remplacer l’expression de création d’objet dans son intégralité, y compris le `new` mot clé au début et les parenthèses à la fin.  Ajoutez le code suivant à votre méthode (et utiliser **Ctrl**+**.** Pour ajouter un `using` instruction pour `ObjectCreationExpressionSyntax`) :

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Inscrire votre correction du code pour l’ampoule l’interface utilisateur.** Lorsque vous inscrivez votre correctif de code, Roslyn se connecte automatiquement à l’ampoule Visual Studio l’interface utilisateur.  Les utilisateurs finaux s’affiche, ils peuvent utiliser **Ctrl**+**.** (période), lorsque votre analyseur tildes erronée `ImmutableArray<T>` utilisation du constructeur.  Étant donné que votre fournisseur de correctif de code s’exécute uniquement quand il existe un problème, vous pouvez supposent l’expression de création d’objet que vous recherchez.  À partir du paramètre de contexte, vous pouvez enregistrer la correction du code en ajoutant le code suivant à la fin de `RegisterCodeFixAsync` méthode :

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Vous devez placer le signe insertion de l’éditeur dans l’identificateur, `CodeAction`, puis utilisez **Ctrl**+**.** (période) pour ajouter le texte approprié `using` instruction pour ce type.

Placez ensuite le point d’insertion de l’éditeur dans le `ChangeToImmutableArrayEmpty` identificateur et l’utilisation **Ctrl**+**.** pour générer ce stub de méthode pour vous.

Cet dernière extrait de code que vous avez ajouté inscrit la correction du code en passant un `CodeAction` et l’ID de diagnostic pour le genre de problème détecté.  Dans cet exemple, il existe un seul ID de diagnostic ce code fournit des correctifs pour, donc vous pouvez simplement transmettre le premier élément du tableau d’ID diagnostic.  Lorsque vous créez le `CodeAction`, vous passez dans le texte que l’ampoule l’interface utilisateur doit utiliser en tant que description de la correction du code.  Vous également transmettez une fonction qui prend un CancellationToken et retourne un nouveau Document.  Le nouveau Document a une nouvelle arborescence de syntaxe qui inclut vos corrigée code qui appelle `ImmutableArray.Empty`.  Cet extrait de code utilise une expression lambda afin qu’il peut fermer sur le nœud objectCreation et Document du contexte.

**Construire la nouvelle arborescence de syntaxe.** Dans le `ChangeToImmutableArrayEmpty` méthode dont stub généré précédemment, entrez la ligne de code : `ImmutableArray<int>.Empty;`.  Si vous affichez le **visualiseur de syntaxe** fenêtre outil à nouveau, vous pouvez voir cette syntaxe est un nœud SimpleMemberAccessExpression.  C’est ce que cette méthode doit construire et retourner dans un nouveau Document.

La première modification à `ChangeToImmutableArrayEmpty` consiste à ajouter `async` avant `Task<Document>` le fait que les générateurs de code ne peut pas la méthode doit être asynchrone.

Renseignez le corps avec le code suivant afin que votre méthode est similaire à ce qui suit :

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

Vous devez placer le signe insertion de l’éditeur dans le `SyntaxGenerator` identificateur et l’utilisation **Ctrl**+**.** (période) pour ajouter le texte approprié `using` instruction pour ce type.

Ce code utilise `SyntaxGenerator`, qui est un type très utile pour la construction du nouveau code.  Une fois que l’obtention d’un générateur pour le document dont dispose le problème de code, `ChangeToImmutableArrayEmpty` appels `MemberAccessExpression`, en passant le type qui possède le membre que vous souhaitez accéder à et en passant le nom du membre en tant que chaîne.

Ensuite, la méthode extrait la racine du document, et étant donné que cela peut impliquer un travail arbitraire dans le cas général, le code attend cet appel et transmet le jeton d’annulation.  Modèles de code Roslyn sont immuables, comme l’utilisation d’une chaîne .NET ; Lorsque vous mettez à jour la chaîne, vous obtenez en retour un nouvel objet string.  Lorsque vous appelez `ReplaceNode`, vous obtenez en retour un nouveau nœud racine.  La majeure partie de l’arborescence de syntaxe est partagé (car il est immuable), mais la `objectCreation` nœud est remplacé par le `memberAccess` nœud, ainsi que tous les nœuds parents jusqu'à la racine d’arborescence de syntaxe.

## <a name="try-your-code-fix"></a>Essayez votre correctif de code

Vous pouvez maintenant appuyer sur **F5** pour exécuter votre analyseur dans une deuxième instance de Visual Studio.  Ouvrez le projet de console que vous avez utilisé avant.  Doit maintenant apparaître l’ampoule s’affichent dans laquelle votre nouvelle expression de création d’objet pour `ImmutableArray<int>`.  Si vous appuyez sur **Ctrl**+**.** (période), puis vous verrez votre code à résoudre, et vous verrez un aperçu de différence de code généré automatiquement dans l’ampoule l’interface utilisateur.  Roslyn cela crée pour vous.

**Conseil Pro :** si vous lancez la deuxième instance de Visual Studio et vous ne voyez pas l’ampoule avec votre correctif de code, vous devrez peut-être effacer le cache du composant de Visual Studio.  Effacement du cache de force Visual Studio pour re-examiner les composants, afin de Visual Studio doit ensuite capter de votre composant plus récente.  Tout d’abord, arrêtez la deuxième instance de Visual Studio.  Ensuite, dans **Windows Explorer**, accédez à votre répertoire utilisateur (*c:\users\\< userid\>*) et recherchez *AppData\Local\Microsoft\VisualStudio\14.0Roslyn \\*.  Dans ce répertoire, supprimez le répertoire de sub ComponentModelCache.  Les modifications « 14 » à une version avec Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Communiquer avec vidéo et terminer le projet de code

Vous pouvez voir cet exemple développé et décrits plus en détail dans [cette conférence](https://channel9.msdn.com/events/Build/2015/3-725).  La discussion montre l’Analyseur de travail et vous guide à travers la création d’elle.

Vous pouvez voir tout le code terminé [ici](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Les sous-dossiers *DoNotUseImmutableArrayCollectionInitializer* et *DoNotUseImmutableArrayCtor* chacun avoir un fichier c# pour détecter les problèmes et un fichier c# qui implémente le code corrige qui affichent dans le Ampoule Visual Studio l’interface utilisateur.  Notez le code finalisé en un peu plus d’abstraction afin d’éviter l’extraction ImmutableArray\<T > type objet maintes et maintes fois.  Il utilise des actions inscrites imbriquées pour enregistrer l’objet de type dans un contexte qui est disponible chaque fois que les actions de sub (analyser la création d’objets et d’analyser les initialisations de collection) exécuter.

## <a name="see-also"></a>Voir aussi

* [\\\Build 2015 talk](https://channel9.msdn.com/events/Build/2015/3-725)
* [Code terminé sur GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Autres documents sur le site GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Règles FxCop implémentées avec des analyseurs de Roslyn sur GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
