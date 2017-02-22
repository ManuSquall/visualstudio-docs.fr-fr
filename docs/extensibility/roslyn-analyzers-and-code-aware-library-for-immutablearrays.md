---
title: "Analyseurs de Roslyn et de la biblioth&#232;que de Code prenant en charge pour ImmutableArrays | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Analyseurs de Roslyn et de la biblioth&#232;que de Code prenant en charge pour ImmutableArrays
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le [.NET Compiler Platform](https://github.com/dotnet/roslyn) \(« Roslyn »\) vous permet de créer des bibliothèques de code prenant en charge.  Une bibliothèque de code prenant en charge fournit des fonctionnalités que vous pouvez utiliser et des outils \(analyseurs Roslyn\) pour vous aider à utiliser la bibliothèque de façon optimale, ou pour éviter des erreurs.  Cette rubrique vous montre comment créer un analyseur de Roslyn réel pour intercepter les erreurs courantes lors de l'utilisation du [Collections immuables](../Topic/NIB:%20Immutable%20Collections.md) package NuGet.  L'exemple montre également comment fournir un correctif pour un problème de code identifié par l'analyseur.  Les utilisateurs voient les correctifs de code dans l'ampoule Visual Studio l'interface utilisateur et peuvent appliquer un correctif pour le code automatiquement.  
  
## Dans cette rubrique  
 Cette rubrique compose les sections suivantes :  
  
-   Prise en main  
  
-   Quel est le problème ?  
  
-   Recherche de Types de modèle de Code approprié pour déclencher votre analyseur  
  
-   Création du projet Analyzer  
  
-   Initialisation de l'analyseur  
  
-   Définition des propriétés pour les utilisateurs de votre analyseur  
  
-   Analyse d'une Expression de création d'objet  
  
-   Lancement de Visual Studio avec votre analyseur de la première fois  
  
-   Fin de l'analyseur à l'aide de modifier & Continuer  
  
-   Ajout d'un « correctif » pour le problème de Code  
  
-   Tentative de correction du Code  
  
-   Communiquer avec le projet de Code terminé et vidéo  
  
## Prise en main  
 Vous devez disposer pour générer cet exemple :  
  
-   Visual Studio 2015 \(pas une édition Express\) ou une version ultérieure.  Vous pouvez utiliser le libre [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)  
  
-   [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  Vous pouvez également, lors de l'installation de Visual Studio, vérifier outils d'extensibilité de Visual Studio sous outils communs pour installer le Kit de développement logiciel en même temps.  Si vous avez déjà installé Visual Studio, vous pouvez également installer ce SDK à partir du menu principal **fichier &#124; Nouveau &#124; Projet...**, en choisissant c\# dans le volet de navigation gauche, puis en choisissant d'extensibilité.  Lorsque vous choisissez la «**installer les outils d'extensibilité de Visual Studio**« modèle de projet du plan du site, il vous invite à télécharger et installer le Kit de développement logiciel.  
  
-   [.NET compiler Platform \(« Roslyn »\) SDK](http://aka.ms/roslynsdktemplates).  Vous pouvez également installer le Kit de développement logiciel en ouvrant le menu principal **fichier &#124; Nouveau &#124; Projet...**, en choisissant **c\#** dans le volet de navigation gauche, puis en sélectionnant **extensibilité**.  Lorsque vous choisissez «**Télécharger le SDK de plateforme du compilateur .NET**« modèle de projet du plan du site, il vous invite à télécharger et installer le Kit de développement logiciel.  Ce SDK inclut les [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Cela permet d'outil extrêmement utile que vous savez quels types de modèle de code recherchez dans votre analyseur.  Les appels d'infrastructure analyzer dans votre code pour les types de modèle de code spécifique, afin que votre code s'exécute lorsque cela est nécessaire uniquement et permettre se concentrer uniquement sur l'analyse de code approprié.  
  
## Quel est le problème ?  
 Imaginez que vous fournissez une bibliothèque avec ImmutableArray \(par exemple, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>\) prend en charge.  Les développeurs c\# ont beaucoup d'expérience dans les tableaux .NET.  Toutefois, en raison de la nature de ImmutableArrays et optimisation des techniques utilisées dans l'implémentation, intuitions développeur c\# entraînent les utilisateurs de votre bibliothèque d'écrire du code rompu, comme expliqué ci\-dessous.  En outre, les utilisateurs ne voient pas leurs erreurs jusqu'au moment de l'exécution, ce qui n'est pas la qualité qu'ils servent à dans Visual Studio avec .NET.  
  
 Les utilisateurs sont familiers avec l'écriture de code comme suit :  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Création de tableaux vides à remplir avec les lignes de code et à l'aide de la syntaxe d'initialiseur de collection sont très familiers aux développeurs c\#.  Toutefois, écrire le même code pour un ImmutableArray se bloque lors de l'exécution :  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 La première erreur est en raison de l'implémentation de ImmutableArray utilisant une structure pour encapsuler le stockage de données sous\-jacent.  Les structures doivent avoir des constructeurs sans paramètre afin que `default(T)` structs avec toutes les expressions peuvent retourner zéro ou null membres.  Lorsque le code accède à `b1.Length`, il existe une exécution déréférencement d'erreur étant donné qu'aucun groupe de stockage sous\-jacent du struct ImmutableArray.  La méthode correcte pour créer un ImmutableArray vide est `ImmutableArray<int>.Empty`.  
  
 L'erreur avec des initialiseurs de collection se produit parce que la méthode ImmutableArray.Add retourne des instances de chaque fois que vous l'appelez.  Étant donné que ImmutableArrays ne changent jamais, lorsque vous ajoutez un nouvel élément, vous obtenez en retour un nouvel objet ImmutableArray \(qui peut\-être partager un stockage pour des raisons de performances avec un ImmutableArray existant\).  Étant donné que `b2` pointe vers le premier ImmutableArray avant d'appeler `Add()` cinq fois, `b2` est une valeur par défaut ImmutableArray.  Appel longueur dessus également se bloque avec une valeur null déréférencer l'erreur.  La méthode correcte pour initialiser un ImmutableArray sans ajouter manuellement l'appel est d'utiliser `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.  
  
## Recherche de Types de nœud syntaxe appropriées pour déclencher votre analyseur  
 Pour commencer à créer l'analyseur, tout d'abord déterminer le type de SyntaxNode que vous souhaitez rechercher.    Lance le visualiseur de syntaxe dans le menu **affichage &#124; Autres fenêtres &#124; Roslyn Syntax Visualizer**.  
  
 Placer le signe insertion de l'éditeur sur la ligne qui déclare `b1`.  Vous verrez le visualiseur de syntaxe montre que vous êtes dans un `LocalDeclarationStatement` nœud de l'arborescence de syntaxe.  Ce nœud possède un `VariableDeclaration`, qui à son tour possède un `VariableDeclarator`, qui à son tour a une `EqualsValueClause`, et enfin un `ObjectCreationExpression`.  Lorsque vous cliquez dans l'arborescence de syntaxe visualiseur de nœuds, la syntaxe dans la fenêtre de l'éditeur met en surbrillance pour vous montrer le code représenté par ce nœud.  Les noms des types SyntaxNode sub mettre en correspondance les noms utilisés dans la syntaxe du langage c\#.  
  
## Création du projet Analyzer  
 Dans le menu principal, choisissez **fichier &#124; Nouveau &#124; Projet...**.  Dans le **Nouveau projet** boîte de dialogue, sous **c\#** projets dans la barre de navigation de gauche, sélectionnez extensibilité, puis dans le volet droit du **Analyzer avec Code corriger** modèle de projet.  Entrez un nom et confirmez la boîte de dialogue.  
  
 Le modèle s'ouvre un fichier DiagnosticAnalyzer.cs.  Choisissez éditeur onglet de la mémoire tampon.  Ce fichier contient une classe d'analyseur \(formé à partir du nom, vous avez donné au projet\) qui dérive de `DiagnosticAnalyzer` \(un type de l'API de Roslyn\).  Votre nouvelle classe a un `DiagnosticAnalyzerAttribute` déclarer votre analyseur concerne le langage c\# afin que le compilateur détecte et charge votre analyseur.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Vous pouvez implémenter un analyseur à l'aide de Visual Basic qui cible le code c\#, et vice versa.  Il est plus important dans le DiagnosticAnalyzerAttribute pour choisir si votre analyseur cible une langue ou à la fois.  Analyseurs plus complexes qui requièrent une modélisation détaillée de la langue peuvent uniquement cibler une seule langue.  Si votre analyseur, contrôles, par exemple uniquement des noms de type ou membre public, il peut être possible d'utiliser le modèle de langage commun que roslyn offre entre Visual Basic et c\#.  Par exemple, FxCop vous avertit qu'une classe implémente <xref:System.Runtime.Serialization.ISerializable>, mais la classe n'a pas la <xref:System.SerializableAttribute> attribut est indépendant du langage et fonctionne pour le code Visual Basic et c\#.  
  
## Initialisation de l'analyseur  
 Faites défiler un peu le `DiagnosticAnalyzer` pour déterminer le `Initialize` \(méthode\).  Le compilateur appelle cette méthode lors de l'activation d'un analyseur.  La méthode prend un `AnalysisContext` objet qui permet à votre analyseur pour obtenir des informations de contexte et à enregistrer des rappels pour les événements pour les types de code que vous souhaitez analyser.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Ouvrez une nouvelle ligne dans cette méthode et type « contexte ». » Pour afficher une liste de saisie semi\-automatique Intellisense.  Vous pouvez voir dans la liste de saisie semi\-automatique, il existe de nombreux `Register…` méthodes pour gérer les différents types d'événements.  Par exemple, le premier abonnement `RegisterCodeBlockAction`, les appels à votre code pour un bloc, ce qui est généralement de code entre accolades.  S'inscrire pour un bloc également rappelle votre code pour l'initialiseur d'un champ, la valeur donnée à un attribut ou la valeur d'un paramètre facultatif.  
  
 Autre exemple, `RegisterCompilationStartAction`, appelle de nouveau votre code au début d'une compilation, ce qui est utile lorsque vous avez besoin collecter l'état sur plusieurs emplacements.  Vous pouvez créer une structure de données, par exemple, pour collecter tous les symboles utilisés, et chaque fois que votre analyseur est rappelé pour certains syntaxe ou un symbole, vous pouvez enregistrer des informations sur chaque emplacement dans votre structure de données.  Lorsque vous êtes rappelé en raison de la fin de la compilation, vous pouvez analyser tous les emplacements que vous avez enregistré, par exemple, pour signaler les symboles, le code utilise à partir de chaque `using` instruction.  
  
 À l'aide de la **syntaxe visualiseur**, vous avez appris que vous souhaitez appeler lorsque le compilateur traite une ObjectCreationExpression.  Ce code vous permet de définir le rappel :  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 Vous inscrire pour un nœud de la syntaxe et les filtrer uniquement les nœuds de syntaxe de création objet.  Par convention, les auteurs de l'analyseur utilisent une expression lambda lors de l'enregistrement des actions, qui permet de garder les analyseurs sans état.  Vous pouvez utiliser la fonctionnalité de Visual Studio **Générer à partir de l'utilisation** pour créer le `AnalyzeObjectCreation` \(méthode\).  Cela génère le type de paramètre de contexte approprié trop.  
  
## Définition des propriétés pour les utilisateurs de votre analyseur  
 Afin que votre analyseur s'affiche dans l'interface utilisateur de Visual Studio appropriée, recherchez et modifiez la ligne suivante du code pour identifier votre analyseur :  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Modification `"Naming"` à `"API Guidance"`.  
  
 Ensuite rechercher et ouvrir le fichier Resources.resx dans votre projet en utilisant le **l'Explorateur de solutions**.  Vous pouvez placer une description pour votre analyseur, titre, etc..  Vous pouvez modifier la valeur de tous ces `“Don’t use ImmutableArray<T> constructor”` pour l'instant.  Vous pouvez placer des arguments dans votre chaîne de formatage de chaîne \({0}, \\{1\\}, etc.\) et par la suite lorsque vous appelez `Diagnostic.Create()`, vous pouvez fournir des arguments à passer un tableau de paramètres.  
  
## Analyse d'une Expression de création d'objet  
 Le `AnalyzeObjectCreation` méthode prend un type différent de contexte fourni par l'infrastructure d'analyseur de code.  La méthode Initialize `AnalysisContext` permet d'enregistrer des rappels d'action pour configurer votre analyseur.  Le `SyntaxNodeAnalysisContext`, par exemple, a un `CancellationToken` que vous pouvez transmettre autour.  Si un utilisateur commence à taper dans l'éditeur, Roslyn annulera analyseurs en cours d'exécution pour enregistrer le travail et améliorer les performances.  Autre exemple, ce contexte a une propriété de nœud qui renvoie le nœud de syntaxe de création d'objet.  
  
 Obtenir le nœud, vous pouvez supposer est le type pour lequel vous avez filtré l'action de nœud de syntaxe :  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
### Lancement de Visual Studio avec votre analyseur de la première fois  
 Lancez Visual Studio en créant et en exécutant votre analyseur \(appuyez sur **F5**\).  Étant donné que le démarrage du projet dans le **l'Explorateur de solutions** est le projet VSIX, exécute vos builds de code de votre code et un projet VSIX et puis lance Visual Studio avec cette extension VSIX installé.  Lorsque vous lancez Visual Studio de cette manière, il lance une ruche de registre distinct afin que votre utilisation principale de Visual Studio n'est pas affectée par les instances de tests lors de la génération d'analyseurs.  Le premier lancement de cette façon, Visual Studio exécute plusieurs initialisations similaires à lorsque vous avez lancé Visual Studio après son installation.  
  
 Créez un projet console, puis entrez le code du tableau dans la méthode Main les applications console :  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 Les lignes de code avec `ImmutableArray` ont tildes, car vous devrez obtenir le package NuGet immuable et ajouter un `using` instruction à votre code.  Appuyez sur le bouton droit du pointeur sur le nœud du projet dans le **l'Explorateur de solutions** et choisissez **Gérer les Packages NuGet...**.  Dans le Gestionnaire de NuGet, tapez « Immuable » dans la zone de recherche, choisissez l'élément « System.Collections.Immutable » \(ne sélectionnez pas « Microsoft.Bcl.Immutable »\) dans le volet gauche et appuyez sur le bouton Installer dans le volet droit.  Installation du package ajoute une référence à vos références de projet.  
  
 Vous rencontrez encore des soulignements ondulés rouges sous `ImmutableArray`, placez le point d'insertion dans cet identificateur appuyez sur **CTRL \+.** \(point\) pour faire apparaître le menu correctif suggéré et sélectionnez Ajouter approprié `using` instruction.  
  
 **Enregistrez et fermez** la deuxième instance de Visual Studio pour le moment pour vous placer dans un état valide pour continuer.  
  
## Fin de l'analyseur à l'aide de modifier & Continuer  
 Dans la première instance de Visual Studio, définissez un point d'arrêt au début de votre `AnalyzeObjectCreation` méthode en appuyant sur **F9** avec le signe insertion sur la première ligne.  
  
 Lancez votre analyseur avec **F5**, dans la deuxième instance de Visual Studio, ouvrez à nouveau votre application de console que vous avez créé la dernière fois.  
  
 Vous renvoyer à la première instance de Visual Studio sur le point d'arrêt, car le compilateur Roslyn vu une expression de création d'objet et appelé dans votre analyseur.  
  
 **Obtient le nœud de la création d'objet.** Ignorer la ligne qui définit la `objectCreation` variable en appuyant sur **F10**, et dans le **fenêtre exécution** évaluer l'expression `“objectCreation.ToString()”`.  Vous constatez que le nœud de syntaxe que la variable pointe vers le code `"new ImmutableArray<int>()"`, simplement ce que vous recherchez.  
  
 **Obtenir un objet de Type de ImmutableArray \< T \>.** Vous devez vérifier si le type en cours de création est ImmutableArray.  Tout d'abord, vous obtenez l'objet qui représente ce type.  Vous vérifiez les types à l'aide du modèle sémantique pour vous assurer d'avoir exactement le type approprié, et vous ne comparez pas la chaîne de ToString\(\).  Entrez la ligne de code à la fin de la fonction suivante :  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Vous désignez des types génériques dans les métadonnées avec backquotes \('\) et le nombre de paramètres génériques.  C'est pourquoi vous ne voyez pas »... ImmutableArray \< T \> » dans le nom des métadonnées.  
  
 Le modèle sémantique a plusieurs choses utiles qui vous permettent de poser des questions sur les symboles, les flux de données, durée de vie des variables, etc..  Roslyn sépare les nœuds de la syntaxe du modèle sémantique pour diverses raisons engineering \(performances, modélisation des erreurs de code, etc.\).  Vous souhaitez que le modèle de compilation pour rechercher des informations contenues dans les références de comparaison précis.  
  
 Vous pouvez faire glisser le pointeur d'exécution jaune sur le côté gauche de la fenêtre de l'éditeur.  Faites glisser jusqu'à la ligne qui définit la `objectCreation` variable et pas à pas principal de votre nouvelle ligne de code à l'aide **F10**.  Si vous placez le pointeur de la souris sur la variable `immutableArrayOfType`, vous voyez que nous avons trouvé le type exact du modèle sémantique.  
  
 **Obtenir le type de l'expression création d'objet.** « Type » est utilisé de plusieurs façons dans cet article, mais cela signifie que si vous avez « nouveau Foo » expression, vous devez obtenir un modèle de Foo.  Vous devez obtenir le type de l'expression de création d'objet pour voir s'il s'agit du type ImmutableArray \< T \>.  Utilisez de nouveau le modèle sémantique pour obtenir des informations sur les symboles pour le symbole de type \(ImmutableArray\) dans l'expression de création d'objet.  Entrez la ligne de code à la fin de la fonction suivante :  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Étant donné que votre analyseur doit gérer le code incomplète ou incorrect dans les mémoires tampons de l'éditeur \(par exemple, il manque une `using` instruction\), vous devez rechercher les `symbolInfo` est `null`.  Vous devez obtenir un type nommé \(INamedTypeSymbol\) à partir de l'objet d'informations de symbole pour terminer l'analyse.  
  
 **Comparez les Types.** Est un type générique ouvert de T qui nous intéresse, et le type dans le code est un type générique concrète, vous interroger les informations de symbole pour le type est construit à partir de \(un type générique ouvert\) et comparez le résultat avec `immutableArrayOfTType`.  Entrez ce qui suit à la fin de la méthode :  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 **Rapport de Diagnostic.** Le diagnostic de création de rapports est assez facile.  Vous utilisez la règle créée pour vous dans le modèle de projet, qui est défini avant la méthode Initialize.  Étant donné que cette situation dans le code est une erreur, vous pouvez modifier la ligne qui a initialisé la règle à remplacer `DiagnosticSeverity.Warning` \(soulignement ondulé vert\) avec `DiagnosticSeverity.Error` \(ligne ondulée rouge\).  Le reste de la règle s'initialise à partir des ressources que vous avez modifié au début de la procédure pas à pas.  Vous devez également signaler l'emplacement de la ligne ondulée, qui est l'emplacement de la spécification du type de l'objet création HYDROGENOSULFITE.  Entrez ce code dans la `if` bloc :  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 Votre fonction doit ressembler à ceci \(peut\-être mis en forme différemment\) :  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 Supprimez le point d'arrêt afin que vous pouvez voir votre utilisation de l'analyseur \(et arrêter le renvoi à la première instance de Visual Studio\).  Faites glisser le pointeur d'exécution au début de votre méthode, puis appuyez sur **F5** pour continuer l'exécution.  Lorsque vous revenez à la deuxième instance de Visual Studio, le compilateur va commencer à examiner le code à nouveau, et elle appellera votre analyseur.  Vous pouvez voir une ligne ondulée sous `ImmutableType<int>`.  
  
## Ajout d'un « correctif » pour le problème de Code  
 Avant de commencer, fermez la deuxième instance de Visual Studio et arrêter le débogage dans la première instance de Visual Studio \(dans lequel vous développez l'analyseur\).  
  
 **Ajoutez une nouvelle classe.** Utilisez le menu contextuel \(bouton droit du pointeur\) sur le nœud de votre projet dans l'Explorateur de solutions et sélectionnez Ajouter un nouvel élément.  Ajoutez une classe appelée `BuildCodeFixProvider`.  Cette classe doit dériver de `CodeFixProvider`, et vous devrez utiliser **CTRL \+.** \(point\) pour appeler la correction du code qui ajoute le bon `using` instruction.  Cette classe doit également être annotée avec `ExportCodeFixProvider` attribut et vous devez ajouter un `using` instruction pour résoudre les `LanguageNames` enum.  Vous devez disposer d'un fichier de classe par le code suivant dans celui\-ci :  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 **Stub des membres dérivés.** À présent, placer le signe insertion de l'éditeur dans l'identificateur `CodeFixProvider` et appuyez sur **CTRL \+.** \(point\) pour l'implémentation de cette classe de base abstraite de stub.  Cela génère une propriété et une méthode pour vous.  
  
 **Implémentez la propriété.** Renseignez les `FixableDiagnosticIds` la propriété `get` corps avec le code suivant :  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
 Roslyn réunit les diagnostics et les correctifs en faisant correspondre ces identificateurs, qui sont simplement des chaînes.  Le modèle de projet généré un ID de diagnostic pour vous, et vous êtes libre de le modifier.  Le code de la propriété retourne simplement l'ID de la classe d'analyseur.  
  
 **La méthode RegisterCodeFixAsync prend un contexte.** Le contexte est important, car un correctif de code peut s'appliquer à plusieurs tests de diagnostic, ou il peut y avoir plusieurs problèmes sur une ligne de code.  Si vous tapez « contexte ». dans le corps de la méthode, la liste de saisie semi\-automatique Intellisense vous montrera certains membres utiles.  Il existe un membre CancellationToken que vous pouvez consulter pour voir si quelque chose souhaite annuler la correction.  Il existe un membre de Document qui possède un grand nombre de membres utiles et vous permet d'obtenir pour les objets de modèle de projet et solution.  Il existe un membre Span qui représente le début et fin de l'emplacement du code spécifié lorsque vous avez signalé le diagnostic.  
  
 **Faites de la méthode est asynchrone.** La première chose à faire est de corriger la déclaration de méthode généré un `async` \(méthode\).  Le correctif de code pour requise l'implémentation d'une classe abstraite n'inclut pas le `async` \(mot clé\) même si la méthode retourne un `Task`.  
  
 **Obtenir la racine de l'arborescence de syntaxe.** Pour modifier le code, de que vous devez générer une nouvelle arborescence de syntaxe avec les modifications votre correctif de code rend.  Vous devez le `Document` à partir du contexte d'appeler `GetSyntaxRootAsync`.  Il s'agit d'une méthode asynchrone, car le travail inconnue pour obtenir de l'arborescence de syntaxe, notamment l'obtention du fichier à partir du disque, l'analyser et créer le modèle de code Roslyn pour qu'il soit.  L'interface utilisateur de Visual Studio doit être réactif pendant ce temps, lesquels `async` active.  Remplacez la ligne de code dans la méthode par le code suivant :  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
 **Rechercher le nœud avec le problème.** Vous passez dans l'étendue du contexte, mais le nœud que vous trouvez peut\-être pas le code, que vous devez modifier.  Le diagnostic signalé fournie uniquement l'étendue pour l'identificateur de type \(laquelle appartenait le trait de soulignement ondulé\), mais vous devez remplacer l'expression de création de l'objet complet, y compris le `new` keywoard au début et les parenthèses à la fin.  Ajoutez le code suivant à votre méthode \(et utilisez **CTRL \+.** pour ajouter un `using` instruction pour `ObjectCreationExpressionSyntax`\) :  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
 **Inscrire votre correction du code pour l'ampoule l'interface utilisateur.** Lorsque vous inscrivez votre correction du code, Roslyn se connecte automatiquement à l'ampoule Visual Studio l'interface utilisateur.  Les utilisateurs voient ces derniers peuvent utiliser **CTRL \+.** \(point\) lorsque votre analyseur tildes erronée `ImmutableArray<T>` utilisation du constructeur.  Étant donné que votre fournisseur de correctif de code s'exécute uniquement lorsqu'il y a un problème, vous pouvez supposer que vous disposez de l'expression de création d'objet que vous recherchez.  À partir du paramètre de contexte, vous pouvez enregistrer la correction du code en ajoutant le code suivant à la fin de `RegisterCodeFixAsync` méthode :  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
 Vous devez placer le signe insertion de l'éditeur dans l'identificateur, `CodeAction`, puis utilisez **CTRL \+.** \(point\) pour ajouter la `using` instruction pour ce type.  
  
 Puis placez le point d'insertion de l'éditeur dans le `ChangeToImmutableArrayEmpty` identificateur et l'utilisation **CTRL \+.** pour générer ce stub de méthode pour vous.  
  
 Ce dernier extrait de code que vous avez ajouté enregistre la correction du code en passant un `CodeAction` et l'ID de diagnostic pour le type de problème détecté.  Dans cet exemple, il n'est qu'un ID de diagnostic qui fournit ce code résout, donc vous pouvez simplement transmettre le premier élément du tableau d'ID diagnostic.  Lorsque vous créez le `CodeAction`, vous passez dans le texte que l'ampoule l'interface utilisateur doit utiliser en tant que description de la correction du code.  Vous passez également une fonction qui prend un CancellationToken et retourne un nouveau Document.  Le nouveau Document a une nouvelle arborescence de syntaxe qui contient votre code corrigé qui appelle `ImmutableArray.Empty`.  Cet extrait de code utilise une expression lambda afin qu'il peut fermer sur le nœud objectCreation et Document du contexte.  
  
 **Construire la nouvelle arborescence de syntaxe.** Dans la `ChangeToImmutableArrayEmpty` méthode dont stub que vous avez générée précédemment, entrez la ligne de code : `ImmutableArray<int>.Empty;`.  Si vous affichez à nouveau la fenêtre visualiseur de syntaxe, vous pouvez voir que cette syntaxe est un nœud SimpleMemberAccessExpression.  C'est ce que cette méthode doit construire et retourner dans un nouveau Document.  
  
 La première modification à `ChangeToImmutableArrayEmpty` consiste à ajouter `async` avant `Task<Document>` car les générateurs de code ne peut pas prendre la méthode doit être asynchrone.  
  
 Remplissez le corps avec le code suivant afin que votre méthode ressemble à ce qui suit :  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
 Vous devez placer le signe insertion de l'éditeur dans le `SyntaxGenerator` identificateur et l'utilisation **CTRL \+.** \(point\) pour ajouter la `using` instruction pour ce type.  
  
 Ce code utilise `SyntaxGenerator`, qui est un type très utile pour la construction du nouveau code.  Après l'obtention d'un générateur de document dont le numéro de code, `ChangeToImmutableArrayEmpty` appelle `MemberAccessExpression`, en passant le type qui comporte le membre que nous souhaitons accéder et en transmettant le nom du membre en tant que chaîne.  
  
 Ensuite, la méthode extrait la racine du document, et parce que cela peut impliquer le travail arbitraire de manière générale, le code attend de cet appel et transmet le jeton d'annulation.  Modèles de code Roslyn sont immuables, de même qu'avec une chaîne .NET ; Lorsque vous mettez à jour la chaîne, vous obtenez en retour un nouvel objet string.  Lorsque vous appelez la méthode `ReplaceNode`, vous obtenez en retour un nœud racine.  La plupart de l'arborescence de syntaxe est partagé \(car il est immuable\), mais la `objectCreation` nœud est remplacé par le `memberAccess` nœud, ainsi que tous les nœuds parents jusqu'à la racine d'arborescence de syntaxe.  
  
## Tentative de correction du Code  
 Vous pouvez maintenant appuyer sur **F5** pour exécuter votre analyseur dans une deuxième instance de Visual Studio.  Ouvrez le projet de console que celle utilisée précédemment.  Maintenant l'ampoule doit s'afficher dans lequel votre nouvelle expression de création d'objet est de `ImmutableArray<int>`.  Si vous appuyez sur **CTRL \+.** \(point\), puis vous verrez votre code à corriger et un aperçu de différence de code généré automatiquement dans l'ampoule l'interface utilisateur s'affiche.  Roslyn cela crée pour vous.  
  
 Conseil Pro : Si vous lancez la deuxième instance de Visual Studio et que vous ne voyez pas l'ampoule de correction de votre code, puis vous devrez effacer le cache du composant de Visual Studio.  Effacement du cache force Visual Studio de réexaminer les composants, afin de Visual Studio doit ensuite capter de votre composant plus récente.  Tout d'abord, arrêtez la deuxième instance de Visual Studio.  Dans l'Explorateur Windows, accédez à votre répertoire utilisateur \(c:\\users\\ \< userid \>\), puis recherchez AppData\\Local\\Microsoft\\VisualStudio\\14.0Roslyn\\.  Dans ce répertoire, supprimez le sous\-répertoire ComponentModelCache.  Les modifications de « 14 » à une version avec Visual Studio.  
  
## Vidéo de présentation et de projet de Code de fin  
 Vous pouvez voir cet exemple développé et abordé ultérieurement dans [cette discussion](http://channel9.msdn.com/events/Build/2015/3-725).  La discussion montre comment l'Analyseur de travail et vous guide à travers le créer.  
  
 Vous pouvez voir tout le code terminé [ici](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Les sous\-dossiers DoNotUseImmutableArrayCollectionInitializer et DoNotUseImmutableArrayCtor ont un fichier c\# pour rechercher un fichier c\# qui implémente les correctifs de code qui s'affichent dans l'ampoule Visual Studio l'interface utilisateur et des problèmes.  Notez le code terminé est un peu plus d'abstraction afin d'éviter l'extraction de l'objet de type ImmutableArray \< T \> maintes et maintes fois.  Il utilise des actions inscrites imbriquées pour enregistrer l'objet de type dans un contexte qui est disponible chaque fois que les actions sub \(analyse de la création d'objets et analyser les initialisations de collection\) s'exécutent.  
  
## Voir aussi  
 [Présentation de \\\\Build 2015](http://channel9.msdn.com/events/Build/2015/3-725)   
 [Code terminé sur github](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)   
 [Plusieurs exemples sur github, regroupées en trois types d'analyseurs](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)   
 [Autres documents sur le site github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)   
 [Règles de FxCop implémentés avec les analyseurs de Roslyn sur github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)