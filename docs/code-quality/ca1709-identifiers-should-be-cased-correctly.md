---
title: "CA1709&#160;: La casse des identificateurs doit &#234;tre correcte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldBeCasedCorrectly"
  - "CA1709"
helpviewer_keywords: 
  - "CA1709"
  - "IdentifiersShouldBeCasedCorrectly"
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 29
---
# CA1709&#160;: La casse des identificateurs doit &#234;tre correcte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Avec rupture \- lorsque déclenchée sur des assemblys, des espaces de noms, des types, des membres et des paramètres.<br /><br /> Sans rupture \- lorsque déclenchée sur des paramètres de type générique.|  
  
## Cause  
 Le nom d'un identificateur ne présente pas une casse correcte.  
  
 \- ou \-  
  
 Le nom d'un identificateur contient un acronyme de deux lettres dont la seconde est en minuscule.  
  
 \- ou \-  
  
 Le nom d'un identificateur contient un acronyme de trois lettres majuscules ou plus.  
  
## Description de la règle  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent ainsi la durée de l'apprentissage requis par les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
 Par convention, les noms de paramètres utilisent la casse mixte ; les noms d'espaces de noms, de types et de membres utilisent la convention de casse Pascal.  Dans un nom qui utilise la casse mixte, la première lettre est une minuscule, et la première lettre de tout mot restant dans le nom est en majuscule.  "packetSniffer", "ioFile" et "fatalErrorCode" sont autant d'exemples de noms qui utilisent la casse mixte.  Dans un nom qui utilise la casse Pascal, la première lettre est une majuscule, et la première lettre de tout mot restant dans le nom est en majuscule.  "PacketSniffer", "IOFile" et "FatalErrorCode" sont autant d'exemples de noms qui utilisent la casse Pascal.  
  
 Cette règle fractionne le nom en mots fondés sur la casse et vérifie tous les mots de deux lettres en fonction d'une liste de mots à deux lettres communs, tel que « In » ou « My ».  Si aucune correspondance n'est trouvée, le mot est considéré comme un acronyme.  De plus, cette règle part du principe qu'elle identifie un acronyme lorsque le nom rencontré contient quatre lettres majuscules de suite ou trois lettres majuscules de suite à la fin du nom.  
  
 Par convention, les acronymes de deux lettres sont tout en lettres majuscules, et les acronymes de trois caractères ou plus utilisent la convention de casse Pascal.  Les exemples suivants utilisent cette convention d'affectation de noms : 'DB', 'CR', 'Cpa' et 'Ecma'.  Les exemples suivants enfreignent la convention : 'Io', 'XML' et 'DoD', et pour les noms qui ne constituent pas des paramètres, 'xp' et 'cpl'.  
  
 « ID » fait l'objet d'une casse particulière pour provoquer une violation de cette règle. 'Id' n'est pas un acronyme, mais une abréviation correspondant à 'identification'.  
  
## Comment corriger les violations  
 Modifiez le nom de manière à ce que sa casse soit correcte.  
  
## Quand supprimer les avertissements  
 Vous pouvez supprimer sans risque un avertissement si vous avez vos propres conventions d'affectation de noms ou si l'identification correspond à un nom propre, comme le nom d'une société ou d'une technologie.  
  
 Vous pouvez également ajouter des termes, des abréviations et des acronymes spécifiques à un dictionnaire personnalisé d'analyse du code.  Les termes spécifiés dans le dictionnaire personnalisé ne provoqueront pas des violations de cette règle.  Pour plus d’informations, consultez [Comment : personnaliser le dictionnaire d’analyse du code](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
  
## Règles connexes  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)