---
title: "Vue d’ensemble | Outil de test Microsoft IntelliTest pour les développeurs | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Visual Studio IntelliTest developer testing tool
ms.assetid: A7B98509-7ACA-4E25-BD1B-BBC98742F028
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: a7dac076dabaf0d44a1eda9c267e5c9b2eafe5a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-microsoft-intellitest"></a>Vue d’ensemble de Microsoft IntelliTest

IntelliTest vous permet de trouver les bogues rapidement et de réduire les coûts de maintenance des tests. Grâce à une approche automatisée et transparente des tests, IntelliTest peut générer une suite de tests candidats pour votre code .NET. La génération des suites de tests peut aussi être guidée par des *propriétés de justesse* que vous spécifiez. IntelliTest fait même évoluer automatiquement la suite de tests au fil de l’évolution du code testé.

**Test de caractérisation**  
IntelliTest vous permet de déterminer le comportement du code sous la forme d’une suite de tests unitaires traditionnels. Une suite de tests de ce type peut être utilisée comme une suite de régression, qui est le point de départ permettant de s’attaquer à la complexité associée à la refactorisation d’un code hérité ou mal connu.

**Génération guidée de l’entrée des tests**  
IntelliTest utilise une approche ouverte d’analyse du code et de résolution des contraintes pour générer automatiquement des valeurs d’entrée précises pour les tests, généralement sans nécessiter l’intervention de l’utilisateur. Pour les types d’objets complexes, il génère automatiquement des fabriques. Vous pouvez guider la génération de l’entrée des tests en étendant et en configurant les fabriques selon vos besoins. Les propriétés de justesse spécifiées en tant qu’assertions dans le code seront également utilisées automatiquement pour guider la génération de l’entrée des tests.

**Intégration à l’IDE**  
IntelliTest est entièrement intégré dans l’IDE Visual Studio. Toutes les informations collectées au cours de la génération de la suite de tests (comme les entrées générées automatiquement, la sortie provenant de votre code, les cas de test générés, et leur état de réussite ou d’échec) apparaissent dans l’IDE Visual Studio. Vous pouvez facilement boucler entre la correction de votre code et la réexécution d’IntelliTest sans quitter l’IDE Visual Studio. Les tests peuvent être enregistrés dans la solution sous forme de projet de test unitaire et seront automatiquement détectés par l’Explorateur de tests Visual Studio par la suite.

**Compléter les pratiques de test existantes**  
Utilisez IntelliTest pour compléter les pratiques de test existantes que vous suivez peut-être déjà.

Si vous voulez tester :

* Des algorithmes sur des données primitives ou des tableaux de données primitives :
  * écrivez des [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing)
* Des algorithmes sur des données complexes, comme un compilateur :
  * laissez d’abord IntelliTest générer une représentation abstraite des données puis passez-la à l’algorithme
  * laissez IntelliTest générer des instances en utilisant la [création d’objets personnalisés](input-generation.md#objects) et des invariants de données, puis appelez l’algorithme
* Des conteneurs de données :
  * écrivez des [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing)
  * laissez IntelliTest générer des instances en utilisant la [création d’objets personnalisés](input-generation.md#objects) et des invariants de données, puis appelez une méthode du conteneur et revérifiez après cela les invariants
  * écrivez des [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing) qui appellent différentes méthodes de l’implémentation, en fonction des valeurs des paramètres
* Une base de code existante :
  * utilisez l’Assistant IntelliTest de Visual Studio pour commencer par générer un ensemble de [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing)

<a name="hello-world"></a>
## <a name="the-hello-world-of-intellitest"></a>Hello World dans IntelliTest

IntelliTest recherche les entrées appropriées au programme testé, ce qui signifie que vous pouvez l’utiliser pour générer la célèbre chaîne **Hello World!** . Ceci suppose que vous avez créé un projet de test C# basé sur MSTest et que vous avez ajouté une référence à **Microsoft.Pex.Framework**. Si vous utilisez un autre framework de test, créez une bibliothèque de classes C# et reportez-vous à la documentation du framework de test pour savoir comment configurer le projet.

L’exemple suivant crée deux contraintes sur le paramètre nommé **value**, pour qu’IntelliTest génère la chaîne nécessaire.

```
using System;
using Microsoft.Pex.Framework; 
using Microsoft.VisualStudio.TestTools.UnitTesting; 

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

Une fois l’exemple compilé et exécuté, IntelliTest génère un ensemble de tests comme celui-ci :

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

Accédez [ici](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest#Anchor_0) pour découvrir où les tests générés sont enregistrés.
Le code de test généré doit inclure un test comme celui-ci :

```
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

C’est aussi simple que cela !

<a name="limitations"></a>
## <a name="limitations"></a>Limitations

Cette section décrit les limitations d’IntelliTest :

* [Non déterminisme](#nondeterminism)
* [Concurrence](#concurrency)
* [Code .NET natif](#native-code)
* [Plateforme](#platform)
* [Language](#language)
* [Raisonnement symbolique](#symbolic-reasoning)
* [Traces de pile](#incorrect-stack)

<a name="nondeterminism"></a>
### <a name="nondeterminism"></a>Non déterminisme

IntelliTest suppose que le programme analysé est déterministe. Si ce n’est pas le cas, IntelliTest boucle jusqu’à atteindre une limite d’exploration.

IntelliTest considère qu’un programme est non déterministe s’il s’appuie sur des entrées qu’IntelliTest ne peut pas contrôler.

IntelliTest contrôle les entrées fournies aux [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing) et obtenues à partir de [PexChoose](static-helper-classes.md#pexchoose). En ce sens, les résultats des appels à du code non managé ou non instrumenté sont également considérés comme des « entrées » du programme instrumenté, mais IntelliTest ne peut pas les contrôler. Si le flux de contrôle du programme dépend de valeurs spécifiques provenant de ces sources externes, IntelliTest ne peut pas « diriger » le programme vers des zones précédemment non couvertes. 

En outre, le programme est considéré comme non déterministe si les valeurs provenant de sources externes changent lors de la réexécution du programme. Dans ces situations, IntelliTest perd le contrôle sur l’exécution du programme et sa recherche devient très inefficace.

Il est parfois difficile de détecter quand cela se produit. Prenons les exemples suivants :

* Le résultat de la méthode **GetHashCode()** est fourni par du code non managé et n’est pas prévisible.
* La classe **System.Random** utilise l’heure système actuelle pour fournir des valeurs véritablement aléatoires.
* La classe **System.DateTime** fournit l’heure actuelle, qui n’est évidemment pas sous le contrôle d’IntelliTest.

<a name="concurrency"></a>
### <a name="concurrency"></a>Concurrence

IntelliTest ne gère pas les programmes multithreads.

<a name="native-code"></a>
### <a name="native-code-net-code-that-is-not-instrumented"></a>Code natif, du code .NET qui n’est pas instrumenté

IntelliTest ne comprend pas le code natif, comme les instructions x86 appelées via **P/Invoke**. Il ne sait pas comment traduire ces appels en contraintes qui peuvent être passées au [solveur de contrainte](input-generation.md#constraint-solver). Même pour le code .NET, il peut analyser seulement le code qu’il instrumente. IntelliTest ne peut pas instrumenter certaines parties de **mscorlib**, notamment la bibliothèque de réflexion. **DynamicMethod** ne peut pas être instrumenté. 

La solution de contournement suggérée est d’avoir un mode de test où de telles méthodes se trouvent dans des types dans un assembly dynamique. Cependant, même si certaines méthodes sont non instrumentées, IntelliTest tente de couvrir autant de code instrumenté que possible.

<a name="platform"></a>
### <a name="platform"></a>Plateforme

IntelliTest est pris en charge seulement sur .NET Framework X86 32 bits.

<a name="language"></a>
### <a name="language"></a>Langue

En principe, IntelliTest peut analyser les programmes .NET arbitraires, écrits dans n’importe quel langage .NET. Cependant, dans Visual Studio, il prend en charge seulement C#.

<a name="symbolic-reasoning"></a>
### <a name="symbolic-reasoning"></a>Raisonnement symbolique

IntelliTest utilise un [solveur de contrainte](input-generation.md#constraint-solver) automatique pour déterminer les valeurs d’entrée appropriées pour le test et pour le programme testé. Les capacités du solveur de contrainte sont et seront toujours néanmoins limitées.

<a name="incorrect-stack"></a>
### <a name="slightly-incorrect-stack-traces"></a>Traces de pile (légèrement) incorrectes

Comme IntelliTest intercepte et « lève à nouveau » les exceptions dans chaque méthode instrumentée, les numéros de ligne dans les traces de pile ne seront pas correctes. Il s’agit d’une limitation liée à la conception de l’instruction « rethrow ».

<a name="further-reading"></a>
## <a name="further-reading"></a>Informations supplémentaires

* [Billet de blog d’introduction](https://blogs.msdn.microsoft.com/visualstudioalm/2014/11/19/introducing-smart-unit-tests/) sur MSDN.
* [Générer des tests unitaires pour votre code avec IntelliTest](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest)

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
