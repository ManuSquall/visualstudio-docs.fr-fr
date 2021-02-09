---
title: Analyseurs Roslyn et bibliothèques de code pour ImmutableArrays
description: Découvrez comment créer un analyseur Roslyn réel pour intercepter les erreurs courantes lors de l’utilisation du package NuGet System. Collections. immuable.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c41b70cf9a4e4e5ae4b1d1ddd2d2a6f6876b9a96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875521"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analyseurs Roslyn et bibliothèque prenant en charge le code pour ImmutableArrays

Le [.NET Compiler Platform](https://github.com/dotnet/roslyn) (« Roslyn ») vous aide à générer des bibliothèques prenant en charge le code. Une bibliothèque de prise en charge du code fournit des fonctionnalités que vous pouvez utiliser et outils (analyseurs Roslyn) pour vous aider à utiliser la bibliothèque de la manière la plus appropriée ou pour éviter les erreurs. Cette rubrique vous montre comment créer un analyseur Roslyn réel pour intercepter les erreurs courantes lors de l’utilisation du package NuGet [System. Collections. immuable](https://www.nuget.org/packages/System.Collections.Immutable) . L’exemple montre également comment fournir un correctif de code pour un problème de code trouvé par l’analyseur. Les utilisateurs voient les corrections de code dans l’interface utilisateur de l’ampoule Visual Studio et peuvent appliquer automatiquement un correctif pour le code.

## <a name="get-started"></a>Bien démarrer

Pour générer cet exemple, vous avez besoin des éléments suivants :

* Visual Studio 2015 (pas une édition Express) ou une version ultérieure. Vous pouvez utiliser l' [édition Visual Studio Community](https://visualstudio.microsoft.com/vs/community/) gratuite
* [SDK Visual Studio](../extensibility/visual-studio-sdk.md). Vous pouvez également, lors de l’installation de Visual Studio, cocher **outils d’extensibilité de Visual Studio** sous **outils courants** pour installer le kit de développement logiciel (SDK) en même temps. Si vous avez déjà installé Visual Studio, vous pouvez également installer ce kit de développement logiciel (SDK) en accédant au menu principal **fichier**  >  **nouveau**  >  **projet**, en choisissant **C#** dans le volet de navigation de gauche, puis en choisissant **extensibilité**. Quand vous choisissez le modèle de projet «**installer le outils d’extensibilité de Visual Studio**», vous êtes invité à télécharger et à installer le kit de développement logiciel (SDK).
* [Kit de développement logiciel (SDK) .NET Compiler Platform (« Roslyn »)](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Vous pouvez également installer ce kit de développement logiciel (SDK) en accédant au menu principal **fichier**  >  **nouveau**  >  **projet**, en choisissant **C#** dans le volet de navigation gauche, puis en choisissant **extensibilité**. Lorsque vous choisissez le modèle de projet «**Télécharger le kit de développement logiciel (SDK) .NET Compiler Platform**», vous êtes invité à télécharger et à installer le kit de développement logiciel (SDK). Ce kit de développement logiciel (SDK) comprend le [Syntax Visualizer Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Syntax-Visualizer.md). Cet outil utile vous aide à déterminer les types de modèles de code que vous devez rechercher dans votre analyseur. L’infrastructure de l’analyseur appelle dans votre code pour des types de modèle de code spécifiques, de sorte que votre code s’exécute uniquement lorsque cela est nécessaire et peut se concentrer uniquement sur l’analyse du code pertinent.

## <a name="whats-the-problem"></a>Quel est le problème?

Imaginez que vous fournissez une bibliothèque avec la prise en charge de ImmutableArray (par exemple, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> ). Les développeurs C# bénéficient d’une grande expérience avec les tableaux .NET. Toutefois, en raison de la nature des techniques de ImmutableArrays et d’optimisation utilisées dans l’implémentation, les intuitions des développeurs C# entraînent l’écriture de code endommagé pour les utilisateurs de votre bibliothèque, comme expliqué ci-dessous. En outre, les utilisateurs ne voient pas leurs erreurs jusqu’au moment de l’exécution, ce qui n’est pas l’expérience de qualité dans lequel ils sont utilisés dans Visual Studio avec .NET.

Les utilisateurs sont familiarisés avec l’écriture de code comme suit :

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

La création de tableaux vides à remplir avec les lignes de code suivantes et l’utilisation de la syntaxe d’initialiseur de collection sont familières aux développeurs C#. Toutefois, l’écriture du même code pour un ImmutableArray se bloque au moment de l’exécution :

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

La première erreur est due au fait que l’implémentation de ImmutableArray utilise un struct pour encapsuler le stockage de données sous-jacent. Les structs doivent avoir des constructeurs sans paramètre afin que `default(T)` les expressions puissent retourner des structs avec tous les membres zéro ou null. Quand le code accède à `b1.Length` , il y a une erreur de déréférencement null au moment de l’exécution, car il n’existe aucun tableau de stockage sous-jacent dans le struct ImmutableArray. La méthode correcte pour créer un ImmutableArray vide est `ImmutableArray<int>.Empty` .

L’erreur avec les initialiseurs de collection se produit parce que la `ImmutableArray.Add` méthode retourne de nouvelles instances chaque fois que vous l’appelez. Comme ImmutableArrays ne change jamais, lorsque vous ajoutez un nouvel élément, vous récupérez un nouvel objet ImmutableArray (qui peut partager du stockage pour des raisons de performances avec un ImmutableArray existant précédemment). Étant donné que `b2` pointe vers le premier ImmutableArray avant d’appeler `Add()` cinq fois, `b2` est un ImmutableArray par défaut. L’appel de length sur ce service se bloque également avec une erreur de déréférencement null. La méthode correcte pour initialiser un ImmutableArray sans appeler manuellement Add consiste à utiliser `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` .

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Rechercher les types de nœuds de syntaxe appropriés pour déclencher votre analyseur

 Pour commencer à créer l’analyseur, commencez par déterminer le type de SyntaxNode que vous devez rechercher. Lancez l' **Syntax Visualizer** à partir de la **vue** de menu  >  **autres**  >  **Syntax Visualizer Roslyn** Windows.

Placez le signe insertion de l’éditeur sur la ligne qui déclare `b1` . Vous verrez que le Syntax Visualizer vous indique que vous êtes dans un `LocalDeclarationStatement` nœud de l’arborescence de syntaxe. Ce nœud a un, `VariableDeclaration` qui a à son tour un `VariableDeclarator` , qui a à son tour un `EqualsValueClause` , et enfin, il y a un `ObjectCreationExpression` . Lorsque vous cliquez dans l’arborescence Syntax Visualizer de nœuds, la syntaxe de la fenêtre de l’éditeur est mise en surbrillance pour vous montrer le code représenté par ce nœud. Les noms des sous-types SyntaxNode correspondent aux noms utilisés dans la grammaire C#.

## <a name="create-the-analyzer-project"></a>Créer le projet de l’analyseur

Dans le menu principal, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans la boîte de dialogue **nouveau projet** , sous projets **C#** dans la barre de navigation de gauche, choisissez **extensibilité**, puis dans le volet droit, choisissez le modèle **de projet analyseur avec correction de code** . Entrez un nom et confirmez la boîte de dialogue.

Le modèle ouvre un fichier *DiagnosticAnalyzer.cs* . Choisissez cet onglet de mémoire tampon de l’éditeur. Ce fichier contient une classe d’analyseur (formée du nom que vous avez donné au projet) qui dérive de `DiagnosticAnalyzer` (un type d’API Roslyn). Votre nouvelle classe a une `DiagnosticAnalyzerAttribute` déclaration que votre analyseur est en rapport avec le langage C# afin que le compilateur Découvre et charge votre analyseur.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Vous pouvez implémenter un analyseur à l’aide de Visual Basic qui ciblent le code C#, et vice versa. Il est plus important dans le DiagnosticAnalyzerAttribute de choisir si votre analyseur cible une langue ou les deux. Des analyseurs plus sophistiqués nécessitant une modélisation détaillée de la langue ne peuvent cibler qu’une seule langue. Par exemple, si votre analyseur vérifie uniquement les noms de type ou les noms de membres publics, il peut être possible d’utiliser le modèle de langage commun Roslyn offre dans Visual Basic et C#. Par exemple, FxCop avertit qu’une classe implémente <xref:System.Runtime.Serialization.ISerializable> , mais la classe n’a pas l' <xref:System.SerializableAttribute> attribut est indépendant du langage et fonctionne pour le code Visual Basic et C#.

## <a name="initialize-the-analyzer"></a>Initialiser l’analyseur

 Faites défiler un peu la `DiagnosticAnalyzer` classe pour voir la `Initialize` méthode. Le compilateur appelle cette méthode lors de l’activation d’un analyseur. La méthode prend un `AnalysisContext` objet qui permet à votre analyseur d’obtenir des informations de contexte et d’enregistrer des rappels pour les événements pour les genres de code que vous souhaitez analyser.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Ouvrez une nouvelle ligne dans cette méthode et tapez « Context ». pour afficher une liste de saisie semi-automatique IntelliSense. Vous pouvez voir dans la liste de saisie semi-automatique qu’il existe de nombreuses `Register...` méthodes pour gérer différents types d’événements. Par exemple, le premier, `RegisterCodeBlockAction` , rappelle votre code pour un bloc, qui est généralement du code entre accolades. L’inscription pour un bloc rappelle également votre code pour l’initialiseur d’un champ, la valeur donnée à un attribut ou la valeur d’un paramètre facultatif.

Autre exemple : `RegisterCompilationStartAction` , rappelle votre code au début d’une compilation, ce qui est utile lorsque vous devez collecter l’État sur de nombreux emplacements. Vous pouvez créer une structure de données, par exemple pour collecter tous les symboles utilisés, et chaque fois que votre analyseur est rappelé pour une syntaxe ou un symbole, vous pouvez enregistrer des informations sur chaque emplacement dans votre structure de données. Lorsque vous êtes rappelé en raison de la fin de la compilation, vous pouvez analyser tous les emplacements que vous avez enregistrés, par exemple pour signaler les symboles utilisés par le code à partir de chaque `using` instruction.

À l’aide de la **Syntax Visualizer**, vous avez appris que vous souhaitez être appelé lorsque le compilateur traite un ObjectCreationExpression. Vous utilisez ce code pour configurer le rappel :

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Vous vous inscrivez à un nœud de syntaxe et filtrez uniquement pour les nœuds de syntaxe de création d’objet. Par Convention, les auteurs de l’analyseur utilisent une expression lambda lors de l’inscription des actions, ce qui permet de conserver les analyseurs sans État. Vous pouvez utiliser la fonctionnalité générer à **partir de l’utilisation** de Visual Studio pour créer la `AnalyzeObjectCreation` méthode. Cela génère également le type de paramètre de contexte correct pour vous.

## <a name="set-properties-for-users-of-your-analyzer"></a>Définir les propriétés des utilisateurs de votre analyseur

Pour que votre analyseur s’affiche dans l’interface utilisateur de Visual Studio de manière appropriée, recherchez et modifiez la ligne de code suivante pour identifier votre analyseur :

```csharp
internal const string Category = "Naming";
```

Remplacez `"Naming"` par `"API Guidance"`.

Ensuite, recherchez et ouvrez le fichier *Resources. resx* dans votre projet à l’aide de l' **Explorateur de solutions**. Vous pouvez insérer une description pour votre analyseur, son titre, etc. Vous pouvez modifier la valeur de tous les à `"Don't use ImmutableArray<T> constructor"` pour le moment. Vous pouvez placer des arguments de mise en forme de chaîne dans votre chaîne ( {0} , {1} , etc.), et ultérieurement lorsque vous appelez `Diagnostic.Create()` , vous pouvez fournir un `params` tableau d’arguments à passer.

## <a name="analyze-an-object-creation-expression"></a>Analyser une expression de création d’objet

La `AnalyzeObjectCreation` méthode prend un type différent de contexte fourni par l’infrastructure de l’analyseur de code. La `Initialize` méthode `AnalysisContext` vous permet d’inscrire des rappels d’action pour configurer votre analyseur. `SyntaxNodeAnalysisContext`, Par exemple, a un `CancellationToken` que vous pouvez passer. Si un utilisateur commence à taper dans l’éditeur, Roslyn annule les analyseurs en cours d’exécution pour enregistrer le travail et améliorer les performances. Autre exemple : ce contexte a une propriété Node qui retourne le nœud de la syntaxe de création de l’objet.

Obtenir le nœud, que vous pouvez supposer, est le type pour lequel vous avez filtré l’action de nœud de syntaxe :

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Lancer Visual Studio avec votre analyseur la première fois

Lancez Visual Studio en générant et en exécutant votre analyseur (appuyez sur **F5**). Étant donné que le projet de démarrage dans le **Explorateur de solutions** est le projet VSIX, l’exécution de votre code génère votre code et une extension VSIX, puis lance Visual Studio avec le VSIX installé. Quand vous lancez Visual Studio de cette manière, il démarre avec une ruche de Registre distincte, de sorte que votre utilisation principale de Visual Studio n’est pas affectée par vos instances de test lors de la création d’analyseurs. La première fois que vous lancez cette méthode, Visual Studio effectue plusieurs initialisations similaires à quand vous avez lancé Visual Studio pour la première fois après l’avoir installé.

Créez un projet console, puis entrez le code du tableau dans la méthode main de votre application console :

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Les lignes de code avec `ImmutableArray` ont des tildes, car vous devez obtenir le package NuGet immuable et ajouter une `using` instruction à votre code. Appuyez sur le bouton de pointeur droit sur le nœud du projet dans la **Explorateur de solutions** et choisissez **gérer les packages NuGet**. Dans le gestionnaire NuGet, tapez « immuable » dans la zone de recherche, puis choisissez l’élément **System. Collections. immuable** (ne choisissez pas **Microsoft. BCL. immuable**) dans le volet gauche et cliquez sur le bouton **installer** dans le volet droit. L’installation du package ajoute une référence à vos références de projet.

Vous voyez toujours des tildes rouges sous. `ImmutableArray` Placez le signe insertion dans cet identificateur et appuyez sur **CTRL** + **.** (point) pour afficher le menu de correction suggéré et choisir d’ajouter l' `using` instruction appropriée.

**Enregistrez tout et fermez** la deuxième instance de Visual Studio pour le moment afin de continuer.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Terminer l’analyseur à l’aide de modifier & continuer

Dans la première instance de Visual Studio, définissez un point d’arrêt au début de votre `AnalyzeObjectCreation` méthode en appuyant sur **F9** avec le signe insertion sur la première ligne.

Lancez à nouveau votre analyseur à l’aide de la touche **F5** et, dans la deuxième instance de Visual Studio, rouvrez l’application console que vous avez créée pour la dernière fois.

Vous revenez à la première instance de Visual Studio au point d’arrêt, car le compilateur Roslyn a vu une expression de création d’objet et a été appelée dans votre analyseur.

**Obtient le nœud de création de l’objet.** Effectuer un pas à pas principal sur la ligne qui définit la `objectCreation` variable en appuyant sur **F10**, puis, dans la **fenêtre exécution** , évaluer l’expression `"objectCreation.ToString()"` . Vous voyez que le nœud de syntaxe vers lequel pointe la variable est le code `"new ImmutableArray<int>()"` , exactement ce que vous recherchez.

**Obtient l’objet de type ImmutableArray<T \> .** Vous devez vérifier si le type en cours de création est ImmutableArray. Tout d’abord, vous récupérez l’objet qui représente ce type. Vous vérifiez les types à l’aide du modèle sémantique pour vous assurer que vous avez exactement le type correct et que vous ne comparez pas la chaîne à partir de `ToString()` . Entrez la ligne de code suivante à la fin de la fonction :

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Vous désignez des types génériques dans les métadonnées avec des battements (') et le nombre de paramètres génériques. C’est la raison pour laquelle vous ne voyez pas «... ImmutableArray \<T> » dans le nom des métadonnées.

Le modèle sémantique comporte de nombreux éléments utiles qui vous permettent de poser des questions sur les symboles, le workflow de données, la durée de vie variable, etc. Roslyn sépare les nœuds de syntaxe du modèle sémantique pour différentes raisons d’ingénierie (performances, modélisation de code erroné, etc.). Vous souhaitez que le modèle de compilation recherche des informations contenues dans des références pour une comparaison précise.

Vous pouvez faire glisser le pointeur d’exécution jaune sur le côté gauche de la fenêtre de l’éditeur. Faites-le glisser jusqu’à la ligne qui définit la `objectCreation` variable et parcourez votre nouvelle ligne de code en utilisant **F10**. Si vous placez le pointeur de la souris sur la variable `immutableArrayOfType` , vous voyez que nous avons trouvé le type exact dans le modèle sémantique.

**Obtient le type de l’expression de création de l’objet.** « Type » est utilisé de plusieurs façons dans cet article, mais cela signifie que si vous avez une expression « New foo », vous devez obtenir un modèle de foo. Vous devez obtenir le type de l’expression de création d’objet pour voir s’il s’agit du \<T> type ImmutableArray. Utilisez de nouveau le modèle sémantique pour obtenir les informations de symbole pour le symbole de type (ImmutableArray) dans l’expression de création d’objet. Entrez la ligne de code suivante à la fin de la fonction :

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Étant donné que votre analyseur doit gérer du code incomplet ou incorrect dans les mémoires tampons de l’éditeur (par exemple, il existe une instruction manquante `using` ), vous devez vérifier qu’il s’agit de `symbolInfo` `null` . Vous devez obtenir un type nommé (INamedTypeSymbol) à partir de l’objet d’informations de symbole pour terminer l’analyse.

**Comparez les types.** Étant donné qu’il existe un type générique ouvert de T que nous recherchons et que le type dans le code est un type générique concret, vous interrogez les informations de symbole pour ce que le type est construit (un type générique ouvert) et comparez ce résultat à `immutableArrayOfTType` . Entrez le code suivant à la fin de la méthode :

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Signaler le diagnostic.** Il est assez facile de signaler le diagnostic. Vous utilisez la règle créée pour vous dans le modèle de projet, qui est défini avant la méthode Initialize. Dans la mesure où cette situation dans le code est une erreur, vous pouvez modifier la ligne qui a initialisé la règle à remplacer `DiagnosticSeverity.Warning` (tilde vert) par `DiagnosticSeverity.Error` (tilde rouge). Le reste de la règle Initialise à partir des ressources que vous avez modifiées vers le début de la procédure pas à pas. Vous devez également signaler l’emplacement du tilde, qui est l’emplacement de la spécification de type de l’expression de création d’objet. Entrez ce code dans le `if` bloc :

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Votre fonction doit ressembler à ceci (peut-être formaté différemment) :

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

Supprimez le point d’arrêt afin que vous puissiez voir le fonctionnement de votre analyseur (et arrêter le retour à la première instance de Visual Studio). Faites glisser le pointeur d’exécution jusqu’au début de votre méthode, puis appuyez sur **F5** pour poursuivre l’exécution. Lorsque vous revenez à la deuxième instance de Visual Studio, le compilateur commence à examiner à nouveau le code, et il appelle dans votre analyseur. Vous pouvez voir un tilde sous `ImmutableType<int>` .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Ajout d’un « correctif de code » pour le problème de code

Avant de commencer, fermez la deuxième instance de Visual Studio et arrêtez le débogage dans la première instance de Visual Studio (où vous développez l’analyseur).

**Ajoutez une nouvelle classe.** Utilisez le menu contextuel (bouton de pointeur droit) sur le nœud de votre projet dans la **Explorateur de solutions** et choisissez d’ajouter un nouvel élément. Ajoutez une classe appelée `BuildCodeFixProvider` . Cette classe doit dériver de `CodeFixProvider` , et vous devrez utiliser **CTRL** + **.** (point) pour appeler le correctif de code qui ajoute l' `using` instruction correcte. Cette classe doit également être annotée avec `ExportCodeFixProvider` l’attribut, et vous devrez ajouter une `using` instruction pour résoudre l' `LanguageNames` énumération. Vous devez disposer d’un fichier de classe contenant le code suivant :

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Stub des membres dérivés.** Maintenant, placez le signe insertion de l’éditeur dans l’identificateur `CodeFixProvider` et appuyez sur **CTRL** + **.** (point) pour remplacer l’implémentation de cette classe de base abstraite. Cela génère une propriété et une méthode pour vous.

**Implémentez la propriété.** Renseignez le `FixableDiagnosticIds` corps de la propriété `get` avec le code suivant :

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn réunit les diagnostics et les correctifs en faisant correspondre ces identificateurs, qui sont simplement des chaînes. Le modèle de projet a généré un ID de diagnostic pour vous, et vous êtes libre de le modifier. Le code dans la propriété retourne simplement l’ID de la classe d’analyseur.

**La méthode RegisterCodeFixAsync prend un contexte.** Le contexte est important, car un correctif de code peut s’appliquer à plusieurs Diagnostics, ou il peut y avoir plusieurs problèmes sur une ligne de code. Si vous tapez « Context ». dans le corps de la méthode, la liste de saisie semi-automatique IntelliSense vous indique certains membres utiles. Il y a un membre CancellationToken que vous pouvez vérifier pour voir si un élément veut annuler le correctif. Il existe un membre de document qui possède un grand nombre de membres utiles et vous permet d’accéder aux objets du modèle de projet et de solution. Il existe un membre span qui correspond au début et à la fin de l’emplacement du code spécifié lorsque vous avez signalé le diagnostic.

**Rendez la méthode asynchrone.** La première chose à faire est de corriger la déclaration de méthode générée pour qu’elle soit une `async` méthode. Le correctif de code pour l’ajout de l’implémentation d’une classe abstraite n’inclut pas le `async` mot clé, même si la méthode retourne un `Task` .

**Obtient la racine de l’arborescence de syntaxe.** Pour modifier le code, vous devez générer une nouvelle arborescence de syntaxe avec les modifications apportées par votre correction de code. Vous avez besoin du `Document` contexte à appeler `GetSyntaxRootAsync` . Il s’agit d’une méthode Async, car il existe un travail inconnu pour obtenir l’arborescence de syntaxe, en incluant éventuellement l’obtention du fichier sur le disque, son analyse et la génération du modèle de code Roslyn pour celui-ci. L’interface utilisateur de Visual Studio doit être réactive pendant cette période, ce qui utilise `async` active. Remplacez la ligne de code de la méthode par ce qui suit :

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Recherchez le nœud présentant le problème.** Vous passez dans l’étendue du contexte, mais le nœud que vous trouvez n’est peut-être pas le code que vous devez modifier. Le diagnostic signalé n’a fourni que l’étendue de l’identificateur de type (où le tilde appartenait), mais vous devez remplacer l’intégralité de l’expression de création d’objet, y compris le `new` mot clé au début et les parenthèses à la fin. Ajoutez le code suivant à votre méthode (et utilisez **CTRL** + **.** pour ajouter une `using` instruction pour `ObjectCreationExpressionSyntax` ) :

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Inscrivez votre correctif de code pour l’interface utilisateur de l’ampoule.** Lorsque vous inscrivez votre correctif de code, Roslyn se connecte automatiquement à l’interface utilisateur de l’ampoule Visual Studio. Les utilisateurs finaux verront qu’ils peuvent utiliser la **touche Ctrl** + **.** (point) quand votre analyseur grossit une utilisation de constructeur incorrecte `ImmutableArray<T>` . Étant donné que votre fournisseur de correctif de code s’exécute uniquement en cas de problème, vous pouvez supposer que vous avez l’expression de création d’objet que vous recherchez. À partir du paramètre context, vous pouvez inscrire le nouveau correctif de code en ajoutant le code suivant à la fin de la `RegisterCodeFixAsync` méthode :

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Vous devez placer le signe insertion de l’éditeur dans l’identificateur, `CodeAction` , puis utiliser **CTRL** + **.** (point) pour ajouter l' `using` instruction appropriée pour ce type.

Placez ensuite le signe insertion de l’éditeur dans l' `ChangeToImmutableArrayEmpty` identificateur et utilisez **CTRL** + **.** à nouveau pour générer ce stub de méthode pour vous.

Ce dernier extrait de code que vous avez ajouté inscrit le correctif de code en passant un `CodeAction` et l’ID de diagnostic pour le type de problème trouvé. Dans cet exemple, il n’existe qu’un seul ID de diagnostic pour lequel ce code fournit des correctifs. vous pouvez donc simplement passer le premier élément du tableau d’ID de diagnostic. Lorsque vous créez le `CodeAction` , vous transmettez le texte que l’interface utilisateur de l’ampoule doit utiliser comme description du correctif de code. Vous transmettez également une fonction qui prend un CancellationToken et retourne un nouveau document. Le nouveau document a une nouvelle arborescence de syntaxe qui inclut le code corrigé qui appelle `ImmutableArray.Empty` . Cet extrait de code utilise une expression lambda pour pouvoir se fermer sur le nœud objectCreation et le document du contexte.

**Construisez la nouvelle arborescence de syntaxe.** Dans la `ChangeToImmutableArrayEmpty` méthode dont le stub a été généré précédemment, entrez la ligne de code : `ImmutableArray<int>.Empty;` . Si vous affichez à nouveau la fenêtre outil **Syntax Visualizer** , vous pouvez voir que cette syntaxe est un nœud SimpleMemberAccessExpression. C’est ce que cette méthode doit construire et retourner dans un nouveau document.

La première modification apportée à `ChangeToImmutableArrayEmpty` est l’ajout de `async` avant `Task<Document>` , car les générateurs de code ne peuvent pas supposer que la méthode doit être asynchrone.

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

Vous devrez placer le signe insertion de l’éditeur dans l' `SyntaxGenerator` identificateur et utiliser **CTRL** + **.** (point) pour ajouter l' `using` instruction appropriée pour ce type.

Ce code utilise `SyntaxGenerator` , qui est un type utile pour la construction d’un nouveau code. Après avoir obtenu un générateur pour le document qui a le problème de code, `ChangeToImmutableArrayEmpty` appelle `MemberAccessExpression` , en passant le type qui a le membre auquel nous souhaitons accéder et en passant le nom du membre en tant que chaîne.

Ensuite, la méthode extrait la racine du document et, comme cela peut impliquer un travail arbitraire dans le cas général, le code attend cet appel et passe le jeton d’annulation. Les modèles de code Roslyn sont immuables, comme l’utilisation d’une chaîne .NET. Lorsque vous mettez à jour la chaîne, vous recevez un nouvel objet String en retour. Lorsque vous appelez `ReplaceNode` , vous récupérez un nouveau nœud racine. La plupart de l’arborescence de syntaxe est Shared (car elle est immuable), mais le `objectCreation` nœud est remplacé par le `memberAccess` nœud, ainsi que tous les nœuds parents jusqu’à la racine de l’arborescence de syntaxe.

## <a name="try-your-code-fix"></a>Essayez votre correctif de code

Vous pouvez maintenant appuyer sur **F5** pour exécuter votre analyseur dans une seconde instance de Visual Studio. Ouvrez le projet de console que vous avez utilisé auparavant. Vous devriez maintenant voir que l’ampoule s’affiche à l’emplacement de votre nouvelle expression de création d’objet `ImmutableArray<int>` . Si vous appuyez sur **CTRL** + **.** (point), vous verrez votre correctif de code, et vous verrez un aperçu de la différence de code généré automatiquement dans l’interface utilisateur de l’ampoule. Roslyn le crée pour vous.

**Conseil Pro :** Si vous lancez la deuxième instance de Visual Studio et que vous ne voyez pas l’ampoule avec votre correctif de code, vous devrez peut-être effacer le cache des composants Visual Studio. L’effacement du cache force Visual Studio à réexaminer les composants, de sorte que Visual Studio doit ensuite récupérer votre composant le plus récent. Tout d’abord, arrêtez la deuxième instance de Visual Studio. Ensuite, dans l' **Explorateur Windows**, accédez *à \\ %LocalAppData%\Microsoft\VisualStudio\16.0Roslyn*. (Le « 16,0 » passe de la version à la version avec Visual Studio.) Supprimez le sous-répertoire *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Projet de code vidéo et de fin

Vous pouvez voir que cet exemple a été développé et abordé plus en détail dans [ce débat](https://channel9.msdn.com/events/Build/2015/3-725). La communication montre l’analyseur de travail et vous guide tout au long de sa création.

Vous pouvez voir tout le code terminé [ici](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Les sous-dossiers *DoNotUseImmutableArrayCollectionInitializer* et *DoNotUseImmutableArrayCtor* ont chacun un fichier c# pour rechercher les problèmes et un fichier c# qui implémente les correctifs de code qui s’affichent dans l’interface utilisateur de l’ampoule Visual Studio. Notez que le code terminé a un peu plus d’abstraction pour éviter la récupération de l' \<T> objet de type ImmutableArray. Il utilise des actions inscrites imbriquées pour enregistrer l’objet de type dans un contexte disponible à chaque exécution des sous-actions (analyse de la création d’objets et analyse des initialisations de collection).

## <a name="see-also"></a>Voir aussi

* [\\\Build 2015 parler](https://channel9.msdn.com/events/Build/2015/3-725)
* [Code terminé sur GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Plusieurs exemples sur GitHub, regroupés en trois types d’analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Autres documents sur le site OSS GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Règles FxCop implémentées avec des analyseurs Roslyn sur GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
