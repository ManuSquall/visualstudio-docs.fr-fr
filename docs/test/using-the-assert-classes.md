---
title: Utilisation des classes Assert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 01d41202f49a61a1ae2ba0f926b5c5b563ab351c
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="using-the-assert-classes"></a>Utilisation des classes Assert
Utilisez les classes Assert de l’espace de noms UnitTestingFramework pour vérifier des fonctionnalités spécifiques. Une méthode de test unitaire teste le code d’une méthode dans votre code de développement. Toutefois, elle ne signale l’exactitude du comportement du code que si vous incluez des instructions Assert.  
  
## <a name="kinds-of-asserts"></a>Genres d’assertion  
 L’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting> fournit plusieurs genres de classes Assert :  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 Dans votre méthode de test, vous pouvez appeler n’importe quel nombre de méthodes de la classe Assert, par exemple Assert.AreEqual(). La classe Assert propose de nombreuses méthodes, et la plupart d’entre elles ont plusieurs surcharges.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Utilisez la classe CollectionAssert pour comparer des collections d’objets, ainsi que pour vérifier l’état d’une ou de plusieurs collections.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Utilisez la classe StringAssert pour comparer des chaînes. Cette classe contient diverses méthodes utiles telles que StringAssert.Contains, StringAssert.Matches et StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 L’exception AssertFailedException est levée à chaque échec d’un test. Un test est considéré comme un échec s’il arrive à expiration, lève une exception inattendue ou contient une instruction Assert qui produit un résultat Failed.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 L’exception AssertInconclusiveException est levée chaque fois qu’un test produit un résultat Inconclusive. En général, vous ajoutez une instruction Assert.Inconclusive à un test sur lequel vous travaillez pour indiquer qu’il n’est pas encore prêt à être exécuté.  
  
> [!NOTE]
>  Une autre stratégie consiste à marquer un test qui n’est pas prêt à être exécuté avec l’attribut Ignore. Toutefois, cela présente un inconvénient : vous ne pouvez pas générer facilement un rapport sur le nombre de tests qu’il vous reste à implémenter.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 Si vous écrivez une nouvelle classe d’exception Assert, le fait que cette classe hérite de la classe de base UnitTestAssertException permet d’identifier plus facilement l’exception comme un échec d’assertion, et non comme une exception inattendue levée à partir de votre code de test ou de production.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Décorez une méthode de test avec l’attribut ExpectedExceptionAttribute quand vous souhaitez que la méthode de test vérifie qu’une exception censée être levée par une méthode dans votre code de développement est effectivement levée dans cette méthode.  
  
## <a name="see-also"></a>Voir aussi

<xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
[Tests unitaires sur votre code](../test/unit-test-your-code.md)
