---
title: Manuel de référence IntelliTest | Outils de test Microsoft pour les développeurs
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 97b28c2810b59465c6d5ac682e95e25b324a95a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653199"
---
# <a name="intellitest-reference-manual"></a>Manuel de référence IntelliTest

## <a name="contents"></a>Sommaire

* **[Vue d’ensemble d’IntelliTest](introduction.md)**
  - [Hello World dans IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Limitations](introduction.md#limitations)
    * [Non-déterminisme](introduction.md#nondeterminism)
    * [Concurrence](introduction.md#concurrency)
    * [Code natif](introduction.md#native-code)
    * [Plateforme](introduction.md#platform)
    * [Language](introduction.md#language)
    * [Raisonnement symbolique](introduction.md#symbolic-reasoning)
    * [Traces de pile incorrectes](introduction.md#incorrect-stack-traces)
  - [Compléments de lecture](introduction.md#further-reading)

* **[Bien démarrer avec IntelliTest](getting-started.md)**
  - [Attributs importants](getting-started.md#important-attributes)
  - [Classes d’assistance statiques importantes](getting-started.md#helper-classes)

* **[Génération de tests](test-generation.md)**
  - [Générateurs de tests](test-generation.md#test-generators)
  - [Tests unitaires paramétrés](test-generation.md#parameterized-unit-testing)
  - [Tests unitaires paramétrés génériques](test-generation.md#generic-parameterized)
  - [Autorisation d’exceptions](test-generation.md#allowing-exceptions)
  - [Test de types internes](test-generation.md#internal-types)
  - [Hypothèses et assertions](test-generation.md#assumptions-and-assertions)
  - [Précondition](test-generation.md#precondition)
  - [Postcondition](test-generation.md#postcondition)
  - [Échecs de test](test-generation.md#test-failures)
  - [Installation et suppression](test-generation.md#setup-teardown)
  - [Compléments de lecture](test-generation.md#further-reading)

* **[Génération d’entrée](input-generation.md)**
  - [Solveur de contraintes](input-generation.md#constraint-solver)
  - [Couverture du code dynamique](input-generation.md#dynamic-code-coverage)
  - [Nombres entiers et à virgule flottante](input-generation.md#integers-and-floats)
  - [Objets](input-generation.md#objects)
  - [Instanciation de classes existantes](input-generation.md#existing-classes)
  - [Visibilité](input-generation.md#visibility)
  - [Objets fictifs paramétrés](input-generation.md#parameterized-mocks)
  - [Structs](input-generation.md#structs)
  - [Tableaux et chaînes](input-generation.md#arrays-and-strings)
  - [Obtention d’entrées supplémentaires](input-generation.md#additional-inputs)
  - [Compléments de lecture](input-generation.md#further-reading)

* **[Limites de l’exploration](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)

* **[Glossaire des attributs](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)

* **[Cascade des paramètres](settings-waterfall.md)**

* **[Classes d’assistance statiques](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Avertissements et erreurs](warnings-and-errors.md)**
  - [MaxBranches dépassé](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime dépassé](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions dépassé](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls dépassé](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack dépassé](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns dépassé](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests dépassé](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Impossible de concrétiser la solution](warnings-and-errors.md#cannot-concretize-solution)
  - [Besoin d’aide pour construire l’objet](warnings-and-errors.md#help-construct)
  - [Besoin d’aide pour rechercher des types](warnings-and-errors.md#help-types)
  - [Type utilisable deviné](warnings-and-errors.md#usable-type-guessed)
  - [Erreur inattendue pendant l’exploration](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Méthode non instrumentée appelée](warnings-and-errors.md#uninstrumented-method-called)
  - [Méthode externe appelée](warnings-and-errors.md#external-method-called)
  - [Méthode non instrumentable appelée](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problème de testabilité](warnings-and-errors.md#testability-issue)
  - [Limitation](warnings-and-errors.md#limitation)
  - [Confusion observée au niveau des appels](warnings-and-errors.md#observed-call-mismatch)
  - [Valeur stockée dans un champ statique](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur la [Communauté des développeurs](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).