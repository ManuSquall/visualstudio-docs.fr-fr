---
title: "Manuel de référence IntelliTest | Outils de test Microsoft pour les développeurs | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 30c23fc51f136d7fc3dcfeca191f5c469fb1e331
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="intellitest-reference-manual"></a>Manuel de référence IntelliTest

## <a name="contents"></a>Sommaire

* **[Vue d’ensemble d’IntelliTest](introduction.md)**
  - [Hello World dans IntelliTest](introduction.md#hello-world)
  - [Limitations](introduction.md#limitations)
    * [Non-déterminisme](introduction.md#nondeterminism)
    * [Concurrence](introduction.md#concurrency)
    * [Code natif](introduction.md#native-code)
    * [Plateforme](introduction.md#platform)
    * [Language](introduction.md#language)
    * [Raisonnement symbolique](introduction.md#symbolic-reasoning)
    * [Traces de pile incorrectes](introduction.md#incorrect-stack)
  - [Compléments de lecture](introduction.md#further-reading)<p>&nbsp;</p>

* **[Bien démarrer avec IntelliTest](getting-started.md)**
  - [Attributs importants](getting-started.md#important-attributes)
  - [Classes d’assistance statiques importantes](getting-started.md#helper-classes)<p>&nbsp;</p>
 
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
  - [Compléments de lecture](test-generation.md#further-reading)<p>&nbsp;</p>

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
  - [Compléments de lecture](input-generation.md#further-reading)<p>&nbsp;</p>

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
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)<p>&nbsp;</p>

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
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)<p>&nbsp;</p>

* **[Cascade des paramètres](settings-waterfall.md)**

* **[Classes d’assistance statiques](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)<p>&nbsp;</p>

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
  - [Valeur stockée dans un champ statique](warnings-and-errors.md#value-static-field)<p>&nbsp;</p>

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
