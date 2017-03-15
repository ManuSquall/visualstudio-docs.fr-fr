---
title: "CA1707&#160;: Les identificateurs ne doivent pas contenir de traits de soulignement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotContainUnderscores"
  - "CA1707"
helpviewer_keywords: 
  - "CA1707"
  - "IdentifiersShouldNotContainUnderscores"
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1707&#160;: Les identificateurs ne doivent pas contenir de traits de soulignement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Avec rupture \- lorsque son déclenchement s'effectue sur les assemblys<br /><br /> Sans rupture \- lorsque déclenchée sur les paramètres de type|  
  
## Cause  
 Le nom d'un identificateur contient le trait de soulignement \(\_\).  
  
## Description de la règle  
 Par convention, les noms d'identificateurs ne contiennent pas de trait de soulignement \(\_\).  La règle vérifie les espaces de noms, types, membres et paramètres.  
  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent ainsi la durée de l'apprentissage requis par les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## Comment corriger les violations  
 Supprimez tous les traits de soulignement présents dans le nom.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Règles connexes  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)