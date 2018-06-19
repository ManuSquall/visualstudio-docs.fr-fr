---
title: Analyseurs de Roslyn et de la bibliothèque de Code prenant en charge pour ImmutableArrays | Documents Microsoft
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
ms.openlocfilehash: 6ebafdd09e6fca0e1266c4eb03c4f6cb66554d06
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148517"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analyseurs de Roslyn et de la bibliothèque de Code prenant en charge pour ImmutableArrays

Le [plateforme des compilateurs .NET](https://github.com/dotnet/roslyn) (« Roslyn ») vous permet de générer des bibliothèques de code prenant en charge.  Une bibliothèque de code prenant en charge fournit les fonctionnalités que vous pouvez utiliser et les outils (analyseurs Roslyn) pour vous aider à utiliser la bibliothèque de façon optimale, ou pour éviter les erreurs.  Cette rubrique vous montre comment créer un analyseur de Roslyn réel pour intercepter les erreurs courantes lors de l’utilisation du [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) package NuGet.  L’exemple montre également comment fournir un correctif pour un problème de code identifié par l’analyseur.  Les utilisateurs voient les corrections du code dans l’ampoule Visual Studio UI et peuvent appliquer un correctif pour le code automatiquement.

## <a name="getting-started"></a>Prise en main

Vous devez les éléments suivants pour générer cet exemple :

* Visual Studio 2015 (pas une édition Express) ou une version ultérieure.  Vous pouvez utiliser gratuitement le [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  Vous pouvez également, lors de l’installation de Visual Studio, vérifier outils d’extensibilité de Visual Studio sous outils courants pour installer le Kit de développement en même temps.  Si vous avez déjà installé Visual Studio, vous pouvez également installer ce SDK en accédant au menu principal **fichier &#124; nouveau &#124;projet...** , en choisissant c# dans le volet de navigation gauche, puis en choisissant d’extensibilité.  Lorsque vous choisissez la «**installer les outils d’extensibilité de Visual Studio**« modèle de projet de barre de navigation, il vous invite à télécharger et installer le Kit de développement.
* [Plateforme de compilateurs .NET (« Roslyn ») SDK](http://aka.ms/roslynsdktemplates).  Vous pouvez également installer ce SDK en accédant au menu principal **fichier &#124; nouveau &#124; projet...** , en choisissant l’option **c#** dans le volet de navigation gauche, puis en choisissant **extensibilité**.  Lorsque vous choisissez «**télécharger le SDK de plateforme du compilateur .NET**« modèle de projet de barre de navigation, il vous invite à télécharger et installer le Kit de développement.  Ce SDK comprend le [Roslyn syntaxe visualiseur](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Cette extrêmement utiles outil vous permet de vous identifier quels types de modèle de code vous recherchez dans l’Analyseur de votre.  Les appels d’infrastructure analyseur dans votre code pour les types de modèles de code spécifiques, afin que votre code s’exécute lorsque cela est nécessaire uniquement et peut se concentrer uniquement sur l’analyse de code approprié.

## <a name="whats-the-problem"></a>Quel est le problème ?

Imaginez que vous fournissez une bibliothèque avec ImmutableArray (par exemple, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) prend en charge.  Les développeurs c# ont beaucoup d’expérience avec les tableaux de .NET.  Toutefois, en raison de la nature des techniques ImmutableArrays et d’optimisation utilisée dans l’implémentation, intuitions de développeurs c# entraînent les utilisateurs de votre bibliothèque écrire du code rompu, comme expliqué ci-dessous.  En outre, les utilisateurs ne voient pas les erreurs jusqu’au moment de l’exécution, ce qui n’est pas l’expérience de qualité qu’ils servent à dans Visual Studio avec .NET.

Les utilisateurs sont familiarisés avec l’écriture de code comme suit :

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Création de tableaux vides à remplir avec les lignes de code et à l’aide de la syntaxe d’initialiseur de collection sont très familiers aux développeurs c#.  Toutefois, l’écriture de la même code pour un ImmutableArray se bloque lors de l’exécution :

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

La première erreur est en raison de l’implémentation de ImmutableArray utilisant une structure pour encapsuler le stockage de données sous-jacent. Les structures doivent avoir des constructeurs de sans paramètre afin que `default(T)` structs avec toutes les expressions peuvent retourner zéro ou null membres.  Lorsque le code accède à `b1.Length`, il existe une exécution déréférencement d’erreur étant donné qu’aucun groupe de stockage sous-jacent du struct ImmutableArray.  La méthode correcte pour créer un ImmutableArray vide est `ImmutableArray<int>.Empty`.

L’erreur avec des initialiseurs de collection se produit, car la méthode ImmutableArray.Add retourne de nouvelles instances chaque fois que vous l’appelez.  Étant donné que ImmutableArrays ne changent jamais, lorsque vous ajoutez un nouvel élément, vous revenir un nouvel objet ImmutableArray (qui peut partager du stockage pour des raisons de performances avec un ImmutableArray existant).  Étant donné que `b2` pointe vers le premier ImmutableArray avant d’appeler `Add()` cinq fois, `b2` est une valeur par défaut ImmutableArray.  L’appel de longueur sur elle aussi se bloque avec une valeur null déréférencer l’erreur.  La méthode correcte pour initialiser un ImmutableArray sans ajouter manuellement l’appel est d’utiliser `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Recherche de Types de nœud de syntaxe appropriées pour déclencher l’Analyseur de votre

 Pour commencer à générer l’analyseur, tout d’abord déterminer le type de SyntaxNode que vous deviez rechercher. Lance le visualiseur de syntaxe dans le menu **vue &#124; autres fenêtres &#124; Roslyn syntaxe visualiseur**.

Placer le signe insertion de l’éditeur sur la ligne qui déclare `b1`.  Vous verrez le visualiseur de syntaxe montre que vous êtes dans un `LocalDeclarationStatement` nœud de l’arborescence de syntaxe.  Ce nœud possède un `VariableDeclaration`, qui à son tour possède un `VariableDeclarator`, qui à son tour possède un `EqualsValueClause`et enfin une `ObjectCreationExpression`.  Lorsque vous cliquez dans l’arborescence de syntaxe visualiseur de nœuds, la syntaxe dans la fenêtre de l’éditeur met en surbrillance pour vous montrer le code représenté par ce nœud.  Les noms des types de sub SyntaxNode correspondent aux noms utilisés dans la grammaire c#.

## <a name="creating-the-analyzer-project"></a>Création du projet de l’analyseur

Dans le menu principal, choisissez **fichier &#124; nouveau &#124; projet...** .  Dans le **nouveau projet** boîte de dialogue, sous **c#** projets dans la barre de navigation de gauche, choisissez l’extensibilité et dans le volet droit, choisissez le **analyseur avec correction du Code** projet modèle.  Entrez un nom et la boîte de dialogue Confirmer.

Le modèle s’ouvre un fichier DiagnosticAnalyzer.cs.  Choisissez éditeur onglet de la mémoire tampon.  Ce fichier comporte une classe de l’analyseur (formé à partir du nom, vous avez donné au projet) qui dérive de `DiagnosticAnalyzer` (un type de l’API de Roslyn).  Votre nouvelle classe a un `DiagnosticAnalyzerAttribute` déclarer votre analyseur ne s’applique au langage c# afin que le compilateur détecte et charge votre analyseur.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Vous pouvez implémenter un analyseur à l’aide de Visual Basic qui cible le code c#, et vice versa.  Il est plus important dans le DiagnosticAnalyzerAttribute pour choisir si votre analyseur cible un langage ou les deux.  Les analyseurs plus sophistiquées qui nécessitent une modélisation détaillée de la langue peuvent uniquement cibler une seule langue.  Si votre analyzer, par exemple, seulement vérifie les noms de type ou membre public, il peut être possible d’utiliser le modèle de langage commun que roslyn offre sur Visual Basic et c#.  Par exemple, FxCop vous avertit qu’une classe implémente <xref:System.Runtime.Serialization.ISerializable>, mais la classe n’a pas la <xref:System.SerializableAttribute> attribut est indépendant du langage et fonctionne pour le code Visual Basic et c#.

## <a name="initalizing-the-analyzer"></a>Initialisation de l’analyseur

 Faites défiler un peu la `DiagnosticAnalyzer` classe pour voir le `Initialize` (méthode).  Le compilateur appelle cette méthode lors de l’activation d’un analyseur.  La méthode prend un `AnalysisContext` objet qui permet à votre analyseur pour obtenir des informations de contexte et enregistrer des rappels pour les événements pour les types de code que vous souhaitez analyser.

```csharp
public override void Initialize(AnalysisContext context) {}

```

Ouvrez une nouvelle ligne dans cette méthode et type « le contexte. » Pour afficher une liste de saisie semi-automatique IntelliSense.  Vous pouvez voir dans la liste de saisie semi-automatique, il existe de nombreux `Register...` méthodes pour gérer les différents types d’événements.  Par exemple, le premier d'entre eux `RegisterCodeBlockAction`, appelle de nouveau votre code pour un bloc, ce qui est généralement le code entre accolades.  L’inscription d’un bloc également rappelle à votre code pour l’initialiseur d’un champ, la valeur donnée à un attribut ou la valeur d’un paramètre facultatif.

Autre exemple, `RegisterCompilationStartAction`, appelle de nouveau votre code au début d’une compilation, ce qui est utile lorsque vous devez collecter l’état sur plusieurs emplacements.  Vous pouvez créer une structure de données, par exemple, pour collecter tous les symboles utilisés, et chaque fois que votre analyseur est rappelé pour certains syntaxe ou d’un symbole, vous pouvez enregistrer des informations relatives à chaque emplacement de votre structure de données.  Lorsque vous êtes rappelé en raison de la fin de la compilation, vous pouvez analyser tous les emplacements que vous avez enregistré, par exemple, pour signaler les symboles, le code utilise à partir de chaque `using` instruction.

À l’aide de la **syntaxe visualiseur**, vous avez appris que vous souhaitez être appelé lorsque le compilateur traite une ObjectCreationExpression.  Ce code vous permet de définir le rappel :

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Vous inscrire pour un nœud de syntaxe et d’un filtre pour seulement les nœuds de syntaxe de création objet.  Par convention, les auteurs de l’analyseur utiliser une expression lambda lors de l’enregistrement des actions, qui permet de conserver les analyseurs sans état.  Vous pouvez utiliser la fonctionnalité de Visual Studio **générer à partir de l’utilisation** pour créer le `AnalyzeObjectCreation` (méthode).  Cela génère le bon type de paramètre de contexte trop.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Définition des propriétés pour les utilisateurs de votre analyseur

Afin que votre analyseur s’affiche dans l’interface utilisateur de Visual Studio appropriée, recherchez et remplacez la ligne suivante de code pour identifier votre analyseur :

```csharp
internal const string Category = "Naming";
```

Modification `"Naming"` à `"API Guidance"`.

Ensuite rechercher et ouvrir le `Resources.resx` fichier dans votre projet en utilisant le **l’Explorateur de solutions**.  Vous pouvez placer dans une description pour votre analyseur, un titre, un périphérique.  Vous pouvez modifier la valeur pour tous ces `"Don't use ImmutableArray<T> constructor"` pour l’instant.  Vous pouvez placer la chaîne mise en forme d’arguments dans votre chaîne de ({0}, {{1}, etc.) et versions ultérieures, lorsque vous appelez `Diagnostic.Create()`, vous pouvez fournir un `params` tableau d’arguments à passer.

## <a name="analyzing-an-object-creation-expression"></a>Analyse une Expression de création d’objet

Le `AnalyzeObjectCreation` méthode prend un autre type de contexte fourni par l’infrastructure d’analyseur de code.  La méthode Initialize `AnalysisContext` permet d’enregistrer des rappels d’action pour configurer votre analyseur.  Le `SyntaxNodeAnalysisContext`, par exemple, a un `CancellationToken` que vous pouvez passer autour.  Si un utilisateur commence à taper dans l’éditeur, Roslyn annulera analyseurs en cours d’exécution pour enregistrer le travail et améliorer les performances.  Autre exemple, ce contexte a une propriété de nœud qui renvoie le nœud de syntaxe de la création de l’objet.

Obtenir le nœud, vous pouvez supposer qu’est le type pour lequel vous avez filtré l’action de nœud de syntaxe :

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Lancement de Visual Studio avec votre analyseur de la première fois

Lancez Visual Studio en créant et en exécutant votre analyseur (appuyez sur **F5**).  Étant donné que le démarrage du projet dans le **l’Explorateur de solutions** le projet VSIX, vos builds de code en cours d’exécution votre code et une extension VSIX et lance ensuite Visual Studio avec cette extension VSIX installé.  Lorsque vous lancez Visual Studio de cette façon, il lance une ruche de registre distinct afin que votre utilisation principale de Visual Studio n’est pas affectée par vos instances de tests lors de la génération d’analyseurs.  La première fois que vous lancez cette façon, Visual Studio exécute plusieurs initialisations similaires à la première fois Visual Studio après l’avoir installé.

Créer un projet de console, puis entrez le code de tableau dans votre méthode principale d’applications console :

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Les lignes de code avec `ImmutableArray` ont les tildes, car vous devez obtenir le package NuGet immuable et ajoutez un `using` instruction à votre code.  Appuyez sur le bouton droit du pointeur sur le nœud de projet dans le **l’Explorateur de solutions** et choisissez **gérer les Packages NuGet...** .  Dans le gestionnaire NuGet, tapez « Immuable » dans la zone de recherche, choisissez l’élément « System.Collections.Immutable » (ne sélectionnez pas « Microsoft.Bcl.Immutable ») dans le volet gauche et appuyez sur le bouton Installer dans le volet droit.  Installation du package ajoute une référence à vos références de projet.

Vous rencontrez encore des soulignements ondulés rouges sous `ImmutableArray`, placez le point d’insertion dans un identificateur et appuyez sur **CTRL +.** (point) pour afficher le menu de suggestion de correction et de choisir d’ajouter les `using` instruction.

**Enregistrez et fermez** la deuxième instance de Visual Studio pour l’instant pour vous placer dans un état propre pour continuer.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Fin de l’analyseur à l’aide de modifier & Continuer

Dans la première instance de Visual Studio, définissez un point d’arrêt au début de votre `AnalyzeObjectCreation` méthode en appuyant sur **F9** avec le signe insertion sur la première ligne.

Démarrer l’Analyseur de votre nouveau avec **F5**et dans la deuxième instance de Visual Studio, ouvrez à nouveau votre application console que vous avez créé la dernière fois.

Vous renvoyer à la première instance de Visual Studio sur le point d’arrêt, car le compilateur Roslyn vu d’une expression de création d’objet et appelé dans l’Analyseur de votre.

**Obtenir le nœud de la création d’objet.** Étape sur la ligne qui définit la `objectCreation` variable en appuyant sur **F10**et dans le **fenêtre exécution** évaluer l’expression `"objectCreation.ToString()"`.  Vous voyez que la variable pointe vers le nœud de syntaxe est le code `"new ImmutableArray<int>()"`, simplement ce que vous recherchez.

**Obtenir ImmutableArray < T\> objet de Type.** Vous devez vérifier si le type en cours de création est ImmutableArray.  Tout d’abord, vous obtenez l’objet qui représente ce type.  Vous vérifiez les types à l’aide du modèle sémantique pour vous assurer d’avoir exactement le type approprié, et vous ne comparer la chaîne de ToString().  Entrez la ligne de code à la fin de la fonction suivante :

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Vous désignez des types génériques dans les métadonnées avec backquotes (') et le nombre de paramètres génériques.  C’est pourquoi vous ne voyez pas «... » ImmutableArray\<T > » dans le nom des métadonnées.

Le modèle sémantique a beaucoup de choses utiles qui vous permettent de poser des questions sur les symboles, flux de données, durée de vie des variable, etc.  Roslyn sépare les nœuds de la syntaxe du modèle sémantique pour diverses raisons engineering (performances, la modélisation de code erronée, etc.).  Vous souhaitez que le modèle de compilation pour rechercher des informations contenues dans les références pour la comparaison précis.

Vous pouvez faire glisser le pointeur d’exécution jaune sur le côté gauche de la fenêtre d’éditeur.  Faites-le glisser jusqu'à la ligne qui définit la `objectCreation` variable et pas à pas principal de votre nouvelle ligne de code à l’aide **F10**.  Si vous placez le pointeur de la souris au-dessus de la variable `immutableArrayOfType`, vous voyez que nous avons trouvé le type exact dans le modèle sémantique.

**Obtenir le type de l’expression création d’objet.** « Type » est utilisé de plusieurs façons dans cet article, mais cela signifie que si vous avez « nouveau Foo » expression, vous devez obtenir un modèle de Foo.  Vous devez obtenir le type de l’expression de création d’objet pour voir si elle est ImmutableArray\<T > type.  Utilisez de nouveau le modèle sémantique pour obtenir des informations sur les symboles pour le symbole de type (ImmutableArray) dans l’expression de création d’objet.  Entrez la ligne de code à la fin de la fonction suivante :

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Étant donné que votre analyseur doit gérer le code incomplète ou incorrect dans les mémoires tampon de l’éditeur (par exemple, il manque `using` instruction), vous devez rechercher `symbolInfo` en cours `null`.  Vous devez obtenir un type nommé (INamedTypeSymbol) à partir de l’objet d’informations de symbole à la fin de l’analyse.

**Comparer les Types.** Car il existe un type générique ouvert de T que nous recherchons et le type dans le code est un type générique concrète, vous interroger les informations de symbole pour le type est construit à partir de (un type générique ouvert) et comparer le résultat avec `immutableArrayOfTType`.  Entrez ce qui suit à la fin de la méthode :

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Rapport de Diagnostic.** Le diagnostic de création de rapports est assez simple.  Vous utilisez la règle créée pour vous dans le modèle de projet, qui est défini avant la méthode Initialize.  Étant donné que cette situation dans le code est une erreur, vous pouvez modifier la ligne qui a initialisé la règle à remplacer `DiagnosticSeverity.Warning` (tilde vert) avec `DiagnosticSeverity.Error` (ligne ondulée rouge).  Le reste de la règle s’initialise à partir des ressources que vous avez modifié vers le début de la procédure pas à pas.  Vous devez également l’emplacement pour le tilde, qui est l’emplacement de spécification de type de l’expression objet la création de rapports.  Entrez ce code dans le `if` bloc :

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

Supprimer le point d’arrêt afin que vous pouvez voir votre utilisation de l’analyseur (et arrêter le renvoi à la première instance de Visual Studio).  Faites glisser le pointeur d’exécution au début de votre méthode, puis appuyez sur **F5** pour poursuivre l’exécution.  Lorsque vous revenez à la deuxième instance de Visual Studio, le compilateur va commencer à examiner le code à nouveau, et il appelle votre analyseur.  Vous pouvez voir une ligne ondulée sous `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Ajout d’un correctif « Code » pour le problème de Code

Avant de commencer, fermez la deuxième instance de Visual Studio et arrêter le débogage dans la première instance de Visual Studio (sur lequel vous développez l’analyseur).

**Ajoutez une nouvelle classe.** Utilisez le menu contextuel (bouton droit du pointeur) sur le nœud de votre projet dans l’Explorateur de solutions et choisissez d’ajouter un nouvel élément.  Ajoutez une classe appelée `BuildCodeFixProvider`.  Cette classe doit dériver de `CodeFixProvider`, et vous devrez utiliser **CTRL +.** (point) pour appeler la correction du code qui ajoute la bonne `using` instruction.  Cette classe doit également être annotée avec `ExportCodeFixProvider` attribut et vous devez ajouter un `using` instruction pour résoudre le `LanguageNames` enum.  Vous devez avoir un fichier de classe par le code suivant dans celui-ci :

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Stub des membres dérivés.** À présent, placer le signe insertion de l’éditeur dans l’identificateur `CodeFixProvider` et appuyez sur **CTRL +.** (point) pour la mise en œuvre pour cette classe de base abstraite de stub.  Cela génère une propriété et une méthode pour vous.

**Implémentez la propriété.** Renseignez le `FixableDiagnosticIds` la propriété `get` corps avec le code suivant :

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn réunit les diagnostics et les correctifs en mettant en correspondance ces identificateurs, qui sont simplement des chaînes.  Le modèle de projet généré un ID de diagnostic, et vous êtes libre de le modifier.  Le code dans la propriété retourne simplement l’ID de la classe de l’analyseur.

**La méthode RegisterCodeFixAsync prend un contexte.** Le contexte est important, car un correctif de code peut s’appliquer à plusieurs tests de diagnostic, ou il peut y avoir plusieurs problèmes sur une ligne de code.  Si vous tapez « contexte ». dans le corps de la méthode, la liste de saisie semi-automatique IntelliSense vous montrera certains membres utiles.  Il existe un membre de CancellationToken que vous pouvez vérifier si un élément souhaite annuler la correction.  Il est un membre de Document qui possède un grand nombre de membres utiles et vous permet d’obtenir pour les objets de modèle de projet et de solution.  Il existe un membre Span qui représente le début et fin de l’emplacement du code spécifié lorsque vous avez signalé le diagnostic.

**Rendre la méthode à être asynchrone.** La première chose à faire est de corriger la déclaration de méthode générée pour être un `async` (méthode).  La correction du code pour la mise en œuvre d’une classe abstraite d’opérations stub n’inclut pas le `async` (mot clé) même si la méthode retourne un `Task`.

**Obtenir la racine de l’arborescence de syntaxe.** Pour modifier le code, de que vous devez générer une nouvelle arborescence de syntaxe avec les modifications votre correctif de code rend.  Vous devez le `Document` à partir du contexte d’appeler `GetSyntaxRootAsync`.  Il s’agit d’une méthode async, car le travail inconnu pour obtenir de l’arborescence de syntaxe, notamment l’obtention du fichier à partir du disque, l’analyser et créer le modèle de code de Roslyn pour qu’il soit.  L’interface utilisateur de Visual Studio doit être réactif pendant ce temps, lesquels `async` active.  Remplacez la ligne de code dans la méthode avec les éléments suivants :

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Recherchez le nœud avec le problème.** Vous passez dans l’étendue du contexte, mais le nœud que vous trouvez peut-être pas le code que vous avez à modifier.  Le diagnostic signalé présenté l’étendue pour l’identificateur de type (où le tilde appartenait), mais vous devez remplacer l’expression de création de l’objet complet, y compris le `new` (mot clé) au début et les parenthèses à la fin.  Ajoutez le code suivant à votre méthode (et utiliser **CTRL +.** Pour ajouter un `using` instruction pour `ObjectCreationExpressionSyntax`) :

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Inscrire votre correction du code pour l’ampoule l’interface utilisateur.** Lorsque vous inscrivez votre correction du code, Roslyn se connecte automatiquement à l’ampoule Visual Studio UI.  Les utilisateurs finaux verront qu’ils peuvent utiliser **CTRL +.** (point) lorsque votre analyseur tildes un mauvais `ImmutableArray<T>` utilisation du constructeur.  Étant donné que votre fournisseur de correctif de code s’exécute uniquement lorsqu’il existe un problème, vous pouvez supposer qu'ont de l’expression de création d’objet que vous recherchez.  À partir du paramètre de contexte, vous pouvez enregistrer la correction du code en ajoutant le code suivant à la fin de `RegisterCodeFixAsync` méthode :

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Vous devez placer le signe insertion de l’éditeur dans l’identificateur, `CodeAction`, puis utilisez **CTRL +.** (point) pour ajouter les `using` instruction pour ce type.

Puis placez le point d’insertion de l’éditeur dans le `ChangeToImmutableArrayEmpty` identificateur et l’utilisation **CTRL +.** pour générer un stub de cette méthode pour vous.

Cet dernière extrait de code que vous avez ajouté enregistre la correction du code en passant un `CodeAction` et l’ID de diagnostic pour le type de problème trouvé.  Dans cet exemple, n'est qu’un seul ID de diagnostic ce code fournit des correctifs pour, donc vous pouvez passer uniquement le premier élément du tableau d’ID diagnostic.  Lorsque vous créez le `CodeAction`, vous passez dans le texte que l’ampoule l’interface utilisateur doit utiliser en tant que description de la correction du code.  Vous passez également une fonction qui accepte un CancellationToken et retourne un nouveau Document.  Le nouveau Document a une nouvelle arborescence de syntaxe qui contient votre code corrigé qui appelle `ImmutableArray.Empty`.  Cet extrait de code utilise une expression lambda afin qu’il peut fermer sur le nœud objectCreation et Document du contexte.

**Construire la nouvelle arborescence de syntaxe.** Dans le `ChangeToImmutableArrayEmpty` méthode dont stub que vous avez généré précédemment, entrez la ligne de code : `ImmutableArray<int>.Empty;`.  Si vous affichez à nouveau la fenêtre d’outil visualiseur de syntaxe, vous pouvez voir que cette syntaxe est un nœud SimpleMemberAccessExpression.  C’est ce que cette méthode doit construire et retourner dans un nouveau Document.

La première modification à `ChangeToImmutableArrayEmpty` consiste à ajouter `async` avant `Task<Document>` car les générateurs de code ne peut pas prendre la méthode doit être asynchrone.

Renseignez le corps avec le code suivant afin que votre méthode ressemble à ce qui suit :

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

Vous devez placer le signe insertion de l’éditeur dans le `SyntaxGenerator` identificateur et l’utilisation **CTRL +.** (point) pour ajouter les `using` instruction pour ce type.

Ce code utilise `SyntaxGenerator`, qui est un type très utile pour la construction du nouveau code.  Après l’obtention d’un générateur pour le document dont le numéro de code, `ChangeToImmutableArrayEmpty` appelle `MemberAccessExpression`, en passant le type qui possède le membre que vous souhaitez accéder et en passant le nom du membre en tant que chaîne.

Ensuite, la méthode extrait la racine du document, et parce que cela peut impliquer un travail arbitraire de manière générale, le code attend cet appel et transmet le jeton d’annulation.  Modèles de code Roslyn sont immuables, de même qu’avec une chaîne .NET ; Lorsque vous mettez à jour la chaîne, vous obtenez en retour un nouvel objet string.  Lorsque vous appelez `ReplaceNode`, vous obtenez en retour un nœud racine.  La majeure partie de l’arborescence de syntaxe est partagé (car il est immuable), mais la `objectCreation` nœud est remplacé par le `memberAccess` nœud, ainsi que tous les nœuds parents jusqu'à la racine d’arborescence de syntaxe.

## <a name="trying-your-code-fix"></a>La tentative de correction du Code

Vous pouvez désormais appuyer sur **F5** pour exécuter votre analyseur dans une deuxième instance de Visual Studio.  Ouvrez le projet de console que celle utilisée précédemment.  Maintenant vous devriez voir l’ampoule où votre nouvelle expression de création d’objet est pour `ImmutableArray<int>`.  Si vous appuyez sur **CTRL +.** (point), puis vous voyez votre code à corriger, et vous verrez un aperçu de différence de code généré automatiquement dans l’ampoule l’interface utilisateur.  Roslyn cela crée pour vous.

**Conseils Pro :** si vous lancez la deuxième instance de Visual Studio, vous ne voyez pas l’ampoule avec votre correction du code, puis vous devrez peut-être effacer le cache du composant de Visual Studio.  Effacement du cache de force réexaminer les composants, afin de Visual Studio doit sélectionne votre composant plus récente de Visual Studio.  Tout d’abord, arrêtez la deuxième instance de Visual Studio.  Puis, dans l’Explorateur Windows, accédez à votre répertoire utilisateur (c:\users\\< userid\>) et recherchez AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\.  Dans ce répertoire, supprimez le répertoire de sub ComponentModelCache.  Les modifications « 14 » vers une version avec Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Vidéo de la conversation et le projet de Code de fin

Vous pouvez voir cet exemple développés et présentés plus en détail dans [cette discussion](http://channel9.msdn.com/events/Build/2015/3-725).  La discussion montre l’Analyseur de travail et vous guide à travers la créer.

Vous pouvez voir tout le code terminé [ici](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Les sous-dossiers DoNotUseImmutableArrayCollectionInitializer et DoNotUseImmutableArrayCtor ont un fichier c# pour la recherche de problèmes et un fichier c# qui implémente les correctifs de code qui s’affichent dans l’ampoule Visual Studio UI.  Notez que le code de fin a un peu plus d’abstraction afin d’éviter l’extraction ImmutableArray\<T > type objet indéfiniment.  Il utilise des actions inscrites imbriquées pour enregistrer l’objet de type dans un contexte qui est disponible chaque fois que les actions de sub (analyser la création d’objet et analyser des initialisations de collection) s’exécutent.

## <a name="see-also"></a>Voir aussi

* [\\\Build 2015 talk](http://channel9.msdn.com/events/Build/2015/3-725)
* [Code terminé sur GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Autres documents sur le site GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Règles FxCop implémentés avec des analyseurs de Roslyn sur GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
