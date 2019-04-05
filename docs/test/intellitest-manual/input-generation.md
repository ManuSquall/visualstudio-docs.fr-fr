---
title: Exécution symbolique dynamique | Outil de test Microsoft IntelliTest pour les développeurs
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8634f1852d10a1935b3ee55b6e80ad9503923fe9
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58323540"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Génération d’entrées à l’aide de l’exécution symbolique dynamique

IntelliTest génère des entrées pour les [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing) en analysant les conditions de branche dans le programme.
Les entrées de test sont choisies en fonction de leur capacité à déclencher de nouveaux comportements de création de branches du programme.
L’analyse est un processus incrémentiel. Elle redéfinit un prédicat **q: I -> {true, false}** sur les paramètres d’entrée de test formels **I**. **q** représente l’ensemble des comportements déjà observés par IntelliTest.
Au départ, **q : = false**, car rien n’a encore été observé.

Les étapes de la boucle sont :

1. IntelliTest détermine les entrées **i** telles que **q(i)=false** à l’aide un [solveur de contrainte](#constraint-solver).
   Par construction, l’entrée **i** prend un chemin d’exécution jamais vu avant. Cela signifie qu’au départ **i** peut être n’importe quelle entrée, car aucun chemin d’exécution n’a encore été découvert.

1. IntelliTest exécute le test avec l’entrée choisie **i** et surveille l’exécution du test et le programme testé.

1. Pendant l’exécution, le programme prend un chemin particulier qui est déterminé par toutes les branches conditionnelles du programme. L’ensemble de toutes les conditions qui déterminent l’exécution est appelé *condition de chemin*, écrite comme prédicat **p: I -> {true, false}** sur les paramètres d’entrée formels. IntelliTest calcule une représentation de ce prédicat.

1. IntelliTest définit **q := (q or p)**. En d’autres termes, il enregistre le fait qu’il a vu le chemin représenté par **p**.

1. Passez à l’étape 1.

Le [solveur de contrainte](#constraint-solver) d’IntelliTest peut gérer les valeurs de tous les types pouvant apparaître dans les programmes .NET :

* [Nombres entiers](#integers-and-floats) et [à virgule flottante](#integers-and-floats)
* [Objects](#objects)
* [Structs](#structs)
* [Tableaux](#arrays-and-strings) et [chaînes](#arrays-and-strings)

IntelliTest filtre les entrées qui ne respectent pas les hypothèses indiquées.

En plus des entrées immédiates (arguments ou [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing)), un test peut extraire d’autres valeurs d’entrée de la classe statique [PexChoose](static-helper-classes.md#pexchoose). Les choix déterminent aussi le comportement des [objets fictifs paramétrables](#parameterized-mocks).

<a name="constraint-solver"></a>
## <a name="constraint-solver"></a>Solveur de contrainte

IntelliTest utilise un solveur de contrainte pour déterminer les valeurs d’entrée appropriées d’un test et du programme testé.

IntelliTest utilise le solveur de contrainte [Z3](https://github.com/Z3Prover/z3/wiki).

<a name="dynamic-code-coverage"></a>
## <a name="dynamic-code-coverage"></a>Couverture dynamique de code

Effet collatéral de la surveillance de l’exécution, IntelliTest collecte les données de couverture dynamique de code.
La couverture est dite *dynamique* car IntelliTest connaît uniquement le code qui a été exécuté. Par conséquent, il ne peut pas donner de valeurs absolues pour la couverture comme d’autres outils de couverture peuvent généralement en donner.

Par exemple, quand IntelliTest signale la couverture dynamique de 5/10 blocs de base, cela signifie que cinq blocs sur dix ont été couverts, où le nombre total de blocs de toutes les méthodes qui ont été atteintes jusqu'à présent par l’analyse (par opposition à toutes les méthodes qui existent dans l’assembly testé) est de 10.
Plus tard au cours de l’analyse, quand d’autres méthodes accessibles sont découvertes, le numérateur (5 dans cet exemple) et le dénominateur (10) peuvent tous les deux augmenter.

<a name="integers-and-floats"></a>
## <a name="integers-and-floats"></a>Nombres entiers et à virgule flottante

Le [solveur de contrainte](#constraint-solver) d’IntelliTest détermine les valeurs d’entrée de test des types primitifs tels que **byte**, **int**, **float** et d’autres, afin de déclencher des chemins d’exécution différents pour le test et le programme testé.

<a name="objects"></a>
## <a name="objects"></a>Objets

IntelliTest peut [créer des instances de classes .NET existantes](#existing-classes) ou vous pouvez utiliser IntelliTest pour automatiquement [créer des objets fictifs](#parameterized-mocks) qui implémentent une interface spécifique et qui se comportent différemment selon leur utilisation.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Instancier les classes existantes

**Quel est le problème ?**

IntelliTest surveille les instructions exécutées quand il exécute un test et le programme testé. Il surveille en particulier tous les accès aux champs. Il utilise ensuite un [solveur de contrainte](#constraint-solver) pour déterminer les nouvelles entrées de test, notamment les objets et leurs valeurs de champ qui entraînent d’autres comportements intéressants du test et du programme testé.

Cela signifie qu’IntelliTest doit créer des objets de certains types et définir leurs valeurs de champ. Si la classe est [visible](#visibility) et a un constructeur [visible](#visibility) par défaut, IntelliTest peut créer une instance de la classe.
Si tous les champs de la classe sont [visibles](#visibility), IntelliTest peut définir les champs automatiquement.

Si le type n’est pas visible ou si les champs ne sont pas [visibles](#visibility), IntelliTest a besoin d’aide pour créer des objets et les mettre dans des états intéressants qui permettent d’obtenir une couverture maximale du code. IntelliTest peut utiliser la réflexion pour créer et initialiser des instances de manière arbitraire. Toutefois, ce n’est généralement pas souhaitable, car cela peut placer l’objet dans un état qui ne peut jamais se produire durant l’exécution normale du programme. Au lieu de cela, IntelliTest s’appuie sur des indications de l’utilisateur.

<a name="visibility"></a>
## <a name="visibility"></a>Visibilité

Le .NET Framework dispose d’un modèle de visibilité élaboré : les types, méthodes, champs et autres membres peuvent être **privés**, **publics**, **internes**et plus encore.

Quand IntelliTest génère des tests, il tente d’effectuer uniquement les actions (comme l’appel des constructeurs et des méthodes et la définition des champs) qui sont autorisées selon les règles de visibilité de .NET dans le contexte des tests générés.

Les règles sont les suivantes :

* **Visibilité des membres internes**
  * IntelliTest part du principe que les tests générés ont accès aux membres internes qui étaient visibles par la classe [PexClass](attribute-glossary.md#pexclass) englobante.
  .NET a l’attribut **InternalsVisibleToAttribute** pour étendre la visibilité des membres internes à d’autres assemblys.

* **Visibilité des membres privés et de la famille (protégés en C#) de la classe [PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest place toujours les tests générés directement dans la classe [PexClass](attribute-glossary.md#pexclass) ou dans une sous-classe. Par conséquent, IntelliTest part du principe qu’il peut utiliser tous les membres de la famille visibles (**protégés** en C#).
  * Si les tests générés sont placés directement dans la classe [PexClass](attribute-glossary.md#pexclass) (généralement en utilisant des classes partielles), IntelliTest part du principe qu’il peut également utiliser tous les membres privés de la classe [PexClass](attribute-glossary.md#pexclass).

* **Visibilité des membres publics**
  * IntelliTest part du principe qu’il peut utiliser tous les membres exportés visibles dans le contexte de la classe [PexClass](attribute-glossary.md#pexclass).

<a name="parameterized-mocks"></a>
## <a name="parameterized-mocks"></a>Objets fictifs paramétrés

Comment tester une méthode qui a un paramètre d’un type d’interface ? Ou d’une classe non-sealed ? IntelliTest ne sait pas quelles implémentations seront utilisées ultérieurement quand cette méthode est appelée. Peut-être même qu’il n’y aura aucune véritable implémentation disponible au moment du test.

La réponse classique consiste à utiliser des *objets fictifs* avec un comportement explicite.

Un objet fictif implémente une interface (ou étend une classe non-sealed). Il ne représente pas une véritable implémentation, mais juste un raccourci qui permet l’exécution des tests à l’aide de l’objet fictif. Son comportement est défini manuellement dans chaque cas de test où il est utilisé. De nombreux outils permettent de définir facilement des objets fictifs et leur comportement attendu, mais ce comportement doit toujours être défini manuellement.

À la place des valeurs codées en dur dans les objets fictifs, IntelliTest peut générer les valeurs. Tout comme il autorise les [tests unitaires paramétrables](test-generation.md#parameterized-unit-testing), IntelliTest autorise également les objets fictifs paramétrables.

Les objets fictifs paramétrables ont deux modes d’exécution différents :

* **sélection** : lors de l’exploration du code, les objets fictifs paramétrables sont une source d’entrées de test supplémentaire à partir de laquelle IntelliTest va essayer de choisir des valeurs intéressantes.
* **réexécution** : lors de l’exécution d’un test généré précédemment, les objets fictifs paramétrables se comportent comme des stubs avec un comportement (en d’autres termes, un comportement prédéfini).

Utilisez [PexChoose](static-helper-classes.md#pexchoose) pour obtenir les valeurs des objets fictifs paramétrables.

<a name="structs"></a>
## <a name="structs"></a>Structs

Le raisonnement d’IntelliTest concernant les valeurs **struct** est similaire à la façon dont il traite les [objets](#objects).

<a name="arrays-and-strings"></a>
## <a name="arrays-and-strings"></a>Tableaux et chaînes

IntelliTest surveille les instructions exécutées quand il exécute un test et le programme testé. Il est particulièrement attentif quand le programme dépend de la longueur d’une chaîne ou d’un tableau (et des limites et longueurs inférieures d’un tableau multidimensionnel).
Il observe aussi comment le programme utilise les différents éléments d’une chaîne ou d’un tableau. Il utilise ensuite un [solveur de contrainte](#constraint-solver) pour déterminer les longueurs et les valeurs d’élément pouvant entraîner des comportements intéressants du test et du programme testé.

IntelliTest tente de réduire la taille des tableaux et des chaînes nécessaires pour déclencher des comportements de programme intéressants.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Obtenir des entrées supplémentaires

La classe statique [PexChoose](static-helper-classes.md#pexchoose) peut être utilisée pour obtenir des entrées supplémentaires dans un test et pour implémenter des [objets fictifs paramétrables](#parameterized-mocks).

<a name="further-reading"></a>
## <a name="further-reading"></a>Compléments de lecture

* [How does it work?](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur la [Communauté des développeurs](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).