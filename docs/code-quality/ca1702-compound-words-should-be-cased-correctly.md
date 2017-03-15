---
title: "CA1702 : La casse des mots compos&#233;s doit &#234;tre correcte | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
helpviewer_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1702 : La casse des mots compos&#233;s doit &#234;tre correcte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Avec rupture \- lorsque déclenchée sur les assemblys.<br /><br /> Sans rupture \- lorsque déclenchée sur les paramètres de type.|  
  
## Cause  
 Le nom d'un identificateur contient plusieurs mots et au moins l'un des mots semble être un mot composé qui ne présente pas une casse correcte.  
  
## Description de la règle  
 Le nom de l'identificateur est fractionné en mots fondés sur la casse.  Chaque combinaison de deux mots contigus est vérifiée par la bibliothèque du vérificateur d'orthographe Microsoft.  S'il est reconnu, l'identificateur produit une violation de la règle.  "CheckSum" et "MultiPart", dont la casse doit être respectivement "Checksum" et "Multipart", sont des exemples de mots composés qui provoquent une violation.  En raison d'une utilisation commune précédente, plusieurs exceptions sont intégrées dans la règle et plusieurs mots entiers sont signalés, comme "Toolbar" et "Filename", dont la casse doit être celle de deux mots distincts ; dans le cas présent, "ToolBar" et "FileName".  
  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent ainsi la durée de l'apprentissage requis par les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## Comment corriger les violations  
 Modifiez le nom de manière à ce que sa casse soit correcte.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si les deux parties du mot composé sont reconnues par le dictionnaire orthographique et qu'on entend utiliser deux mots.  
  
## Règles connexes  
 [CA1701: La casse des mots composés de chaînes de ressources doit être correcte](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## Voir aussi  
 [Indications concernant l'attribution d'un nom](../Topic/Naming%20Guidelines.md)   
 [Conventions de mise en majuscules](../Topic/Capitalization%20Conventions.md)