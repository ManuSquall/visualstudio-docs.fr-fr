---
title: "Utilisation des classes Assert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert, classes"
  - "Assert, instructions"
  - "tests unitaires, instructions Assert"
  - "tests unitaires, classes Assert"
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 27
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 27
---
# Utilisation des classes Assert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez les classes Assert de l'espace de noms UnitTestingFramework pour vérifier des fonctionnalités spécifiques.  Une méthode de test unitaire exerce le code d'une méthode dans votre code de développement, mais elle fournit des rapports sur la validité du comportement du code uniquement si vous incluez des instructions Assert.  
  
## Types d'Asserts  
 L'espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting> fournit plusieurs types de classes Assert :  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 Dans votre méthode de test, vous pouvez appeler un nombre quelconque de méthodes de la classe Assert, telle que Assert.AreEqual\(\).  La classe Assert offre de nombreuses méthodes et une grande partie d'entre elles a plusieurs surcharges.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Utilisez la classe CollectionAssert pour comparer des collections d'objets et pour vérifier l'état d'une ou plusieurs collections.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Utilisez la classe StringAssert pour comparer des chaînes.  Cette classe contient diverses méthodes utiles telles que StringAssert.Contains, StringAssert.Matches et StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 L'exception AssertFailedException est levée à chaque fois qu'un test échoue.  Un test échoue s'il atteint son délai d'expiration, s'il lève une exception inattendue ou s'il contient une instruction Assert qui produit un résultat Échec.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 L'exception AssertInconclusiveException est levée à chaque fois qu'un test produit un résultat Non concluant.  En général, vous ajoutez une instruction Assert.Inconclusive à un test sur lequel vous travaillez encore, afin d'indiquer qu'il n'est pas encore prêt à être exécuté.  
  
> [!NOTE]
>  Une autre stratégie consiste à marquer un test qui n'est pas prêt à être exécuté avec l'attribut Ignore.  Toutefois, l'inconvénient est qu'il est difficile de générer un rapport sur le nombre de tests qu'il reste à implémenter.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 Si vous écrivez une nouvelle classe d'exceptions Assert, faites en sorte que cette classe hérite de la classe de base UnitTestAssertException afin de simplifier l'identification de l'exception comme échec d'assertion plutôt qu'exception inattendue levée à partir de votre test ou code de production.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Décorez une méthode de test avec l'attribut ExpectedExceptionAttribute lorsque vous souhaitez qu'elle vérifie qu'une exception qui doit être levée par une méthode dans votre code de développement est en effet levée dans cette méthode.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/fr-fr/e8370b93-085b-41c9-8dec-655bd886f173)