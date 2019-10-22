---
title: Limites de l’exploration | Outil de test Microsoft IntelliTest pour les développeurs
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: f6b29b8bc2a9755f5f2e2ced237a5a1ce6acfd6e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653222"
---
# <a name="exploration-bounds"></a>Limites de l’exploration

**PexSettingsAttributeBase** est la classe de base abstraite pour définir les limites des paramètres en tant qu’attributs. Consultez [Cascade des paramètres](settings-waterfall.md) pour obtenir une vue d’ensemble des paramètres dans IntelliTest.

Vous pouvez modifier les paramètres à l’aide des propriétés nommées de cet attribut et de ses attributs dérivés :

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Limites de la résolution des contraintes**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) : nombre de secondes pendant lesquelles le [solveur de contrainte](input-generation.md#constraint-solver) doit découvrir les entrées qui incitent à suivre un chemin d’exécution nouveau et différent.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) : taille en mégaoctets que le [solveur de contrainte](input-generation.md#constraint-solver) peut utiliser pour découvrir des entrées.
* **Limites du chemin d’exploration**
  * [MaxBranches](#maxbranches) : nombre maximal de branches qui peuvent être suivies sur un chemin d’exécution.
  * [MaxCalls](#maxcalls) : nombre maximal d’appels qui peuvent être passés pendant le parcours d’un chemin d’exécution.
  * [MaxStack](#maxstack) : taille maximale de la pile pendant le parcours d’un chemin d’exécution, mesurée en nombre de frames d’appels actifs.
  * [MaxConditions](#maxconditions) : nombre maximal de conditions sur les entrées qui peuvent être vérifiées pendant le parcours d’un chemin d’exécution.
* **Limites de l’exploration**
  * [MaxRuns](#maxruns) : nombre maximal d’exécutions qui seront tentées au cours d’une exploration.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) : nombre maximal d’exécutions consécutives sans émettre un nouveau test.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) : nombre maximal d’exécutions avec des chemins d’exécution uniques qui seront tentées au cours d’une exploration.
  * [MaxExceptions](#maxexceptions) : nombre maximal d’exceptions qui peuvent être trouvées en combinant tous les chemins d’exécution découverts.
* **Paramètres de génération de code de suite de tests**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) : quand la valeur est true, les chemins d’exécution qui dépassent l’une des limites de chemin ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)) sont ignorés.
  * [TestEmissionFilter](#testemissionfilter) : indique dans quelles circonstances IntelliTest doit émettre des tests.
  * [TestEmissionBranchHits](#testemissionbranchhits) : contrôle le nombre de tests émis par IntelliTest.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Nombre de secondes pendant lesquelles le [solveur de contrainte](input-generation.md#constraint-solver) doit calculer les entrées qui vont inciter à suivre un chemin d’exécution nouveau et différent. Il s’agit d’une option de **PexSettingsAttributeBase** et ses types dérivés.

Plus IntelliTest explore les chemins d’exécution d’un programme, plus les systèmes de contraintes créés par IntelliTest à partir du flux de contrôle et du flux de données du programme deviennent complexes. Selon le temps dont vous disposez, vous pouvez définir cette valeur pour permettre à IntelliTest de prendre plus ou moins de temps pour découvrir de nouveaux chemins d’exécution.

En règle générale, un délai d’expiration est établi parce qu’IntelliTest essaie de trouver une solution pour un système de contraintes qui n’en a pas, mais il ne le sait pas. Comme il s’agit du cas le plus courant pour un délai d’expiration, il n’est peut-être pas judicieux d’augmenter la limite.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Nombre de mégaoctets que le [solveur de contrainte](input-generation.md#constraint-solver) peut utiliser pour calculer les entrées qui vont inciter à suivre un chemin d’exécution nouveau et différent. Il s’agit d’une option de *PexSettingsAttributeBase** et ses types dérivés.

Plus IntelliTest explore les chemins d’exécution d’un programme, plus les systèmes de contraintes créés par IntelliTest à partir du flux de contrôle et du flux de données du programme deviennent complexes. En fonction de la mémoire disponible sur votre ordinateur, vous pouvez définir cette valeur pour permettre à IntelliTest de s’attaquer à des systèmes de contraintes plus complexes.

En règle générale, un délai d’expiration est établi parce qu’IntelliTest essaie de trouver une solution pour un système de contraintes qui n’en a pas, mais il ne le sait pas. Comme il s’agit de la cause la plus courante d’une situation de mémoire insuffisante, il n’est peut-être pas judicieux d’augmenter la limite.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Nombre maximal de branches qui peuvent être suivies dans un chemin d’exécution.

La motivation derrière cette limite de l’exploration est de restreindre la longueur des chemins d’exécution qu’IntelliTest explore pendant la [génération d’entrées](input-generation.md). Cette limite évite en particulier à IntelliTest de ne plus répondre si le programme entre dans une boucle infinie.

Chaque branche conditionnelle et inconditionnelle du code exécuté et surveillé est comptabilisée pour cette limite, dont les branches qui ne dépendent pas des entrées du test paramétrable.

Par exemple, le code suivant consomme des branches dans la limite de 100 :

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Nombre maximal d’appels qui peuvent être passés pendant le parcours d’un chemin d’exécution.

La motivation derrière cette limite de l’exploration est de restreindre la longueur des chemins d’exécution qu’IntelliTest explore pendant la [génération d’entrées](input-generation.md). Cette limite évite en particulier à IntelliTest de ne plus répondre si le programme appelle une méthode de manière récursive un nombre infini de fois, ce qui provoquerait un dépassement de capacité de la pile irréversible pour IntelliTest.

Chaque appel (direct, indirect, virtuel, de saut) du code exécuté et surveillé est comptabilisé pour respecter cette limite.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Taille maximale de la pile pendant le parcours d’un chemin d’exécution, mesurée en nombre de frames d’appels actifs.

La motivation derrière cette limite de l’exploration est de restreindre la taille de la pile des chemins d’exécution qu’IntelliTest explore pendant la [génération d’entrées](input-generation.md). Cette limite évite en particulier à IntelliTest d’utiliser tout l’espace de pile disponible, ce qui provoquerait un dépassement de capacité de la pile irréversible pour IntelliTest.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Nombre maximal de conditions sur les entrées qui peuvent être vérifiées pendant le parcours d’un chemin d’exécution.

La motivation derrière cette limite de l’exploration est de restreindre la complexité des chemins d’exécution qu’IntelliTest explore pendant la [génération d’entrées](input-generation.md). Chaque branche conditionnelle qui dépend des entrées du test paramétrable est comptabilisée pour respecter cette limite.

Par exemple, chaque chemin dans le code suivant consomme n+1 conditions :

```csharp
[PexMethod]
void ParameterizedTest(int n)
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

Nombre maximal d’exécutions qu’IntelliTest va tenter au cours de l’exploration d’un test.

La motivation derrière cette limite de l’exploration est que tout code qui contient des boucles ou une récursivité peut avoir un nombre infini de chemins d’exécution et IntelliTest doit donc être limité pendant la [génération d’entrées](input-generation.md).

Les deux paramètres **MaxRuns** et **MaxRunsWithUniquePaths** sont liés de la manière suivante :

* IntelliTest appelle une méthode de test paramétrable jusqu’à **MaxRuns** fois avec des entrées de test différentes.
* Si le code exécuté est déterministe, IntelliTest prend chaque fois un chemin d’exécution différent. Toutefois, sous certaines conditions, le code exécuté peut suivre un chemin d’exécution qu’il a déjà pris auparavant, avec des entrées différentes.
* IntelliTest compte le nombre de chemins d’exécution uniques qu’il trouve ; ce nombre est limité par l’option **MaxRunsWithUniquePaths**.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Nombre maximal d’exécutions consécutives sans émettre un nouveau test.

Même si IntelliTest peut souvent trouver de nombreuses entrées de test intéressantes dans un court délai, il n’en trouve plus de nouvelles après un certain temps et n’émet plus de tests unitaires. Cette option de configuration place une limite sur le nombre de tentatives consécutives qu’IntelliTest peut effectuer sans émettre un nouveau test. Une fois atteinte, l’exploration s’arrête.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Nombre maximal de chemins uniques qu’IntelliTest prend en compte au cours d’une exploration.

La motivation derrière cette limite de l’exploration est que tout code contenant des boucles ou une récursivité peut avoir un nombre infini de chemins d’exécution et IntelliTest doit donc être limité pendant la [génération d’entrées](input-generation.md).

Les deux paramètres **MaxRuns** et **MaxRunsWithUniquePaths** sont liés de la manière suivante :

* IntelliTest appelle une méthode de test paramétrable jusqu’à **MaxRuns** fois avec des entrées de test différentes.
* Si le code exécuté est déterministe, IntelliTest prend chaque fois un chemin d’exécution différent. Toutefois, sous certaines conditions, le code exécuté peut suivre un chemin d’exécution qu’il a déjà pris auparavant, avec des entrées différentes.
* IntelliTest compte le nombre de chemins d’exécution uniques qu’il trouve ; ce nombre est limité par l’option **MaxRunsWithUniquePaths**.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Nombre maximal d’exceptions qui peuvent être rencontrées avant d’arrêter l’exploration.

La motivation derrière cette limite de l’exploration est d’arrêter l’exploration de code qui contient de nombreux bogues. Si IntelliTest détecte trop d’erreurs dans le code, l’exploration est arrêtée.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Les chemins d’exécution qui dépassent les limites de chemin configurées [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) et [MaxConditions](#maxconditions) sont ignorés.

La motivation derrière cette limite de l’exploration est de traiter (très probablement) les tests sans fin d’exécution. Quand IntelliTest atteint une limite de l’exploration comme [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) ou [MaxConditions](#maxconditions), il suppose que le test ne sera pas un processus sans fin d’exécution et n’entraînera pas de dépassement de capacité de la pile ultérieurement. De tels cas de test peuvent poser des problèmes à d’autres frameworks de tests et cet attribut fournit un moyen d’empêcher IntelliTest d’émettre des cas de test pour des processus potentiellement sans fin d’exécution ou qui risquent de provoquer un dépassement de capacité de la pile.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Indique les types de tests qu’IntelliTest doit émettre. Les valeurs possibles sont :

* **All** : émet des tests pour tout, dont les violations d’hypothèses.
* **FailuresAndIncreasedBranchHits** (valeur par défaut) : émet des tests pour tous les échecs uniques et chaque fois qu’un cas de test augmente la couverture sous le contrôle de [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths** : émet des tests pour tous les échecs détectés par IntelliTest et aussi pour chaque entrée de test qui entraîne un chemin d’exécution unique.
* **Failures** : émet des tests pour les échecs uniquement.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

Selon le paramètre [TestEmissionFilter](#testemissionfilter) actuel, IntelliTest émet de nouveaux cas de test quand ils couvrent une branche du programme qui ne l’a pas déjà été.

Le paramètre **TestEmissionBranchHits** détermine si IntelliTest doit juste prendre en compte si une branche a été couverte (**TestEmissionBranchHits=1**), si un test l’a couverte une ou deux fois (**TestEmissionBranchHits=2**), et ainsi de suite.

**TestEmissionBranchHits=1** produit une très petite suite de tests qui couvre toutes les branches qu’IntelliTest peut atteindre. En particulier, cette suite de tests couvre également l’ensemble des instructions et blocs de base atteints.

La valeur par défaut de cette option est **TestEmissionBranchHits=2**, qui génère une suite de tests plus expressive et également mieux adaptée pour détecter de futures erreurs de régression.

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur la [Communauté des développeurs](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
