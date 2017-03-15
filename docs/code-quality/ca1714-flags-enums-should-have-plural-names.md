---
title: "CA1714 : Les &#233;num&#233;rations d&#39;indicateurs doivent avoir des noms au pluriel | Microsoft Docs"
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
  - "FlagsEnumsShouldHavePluralNames"
  - "CA1714"
helpviewer_keywords: 
  - "CA1714"
  - "FlagsEnumsShouldHavePluralNames"
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1714 : Les &#233;num&#233;rations d&#39;indicateurs doivent avoir des noms au pluriel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une énumération publique a le <xref:System.FlagsAttribute?displayProperty=fullName> et son nom ne termine pas par "s".  
  
## Description de la règle  
 Les types marqués avec <xref:System.FlagsAttribute> ont des noms au pluriel car l'attribut indique que plusieurs valeurs peuvent être spécifiées.  À titre d'exemple, une énumération qui définit les jours de la semaine peut être prévue pour une utilisation dans une application où vous pouvez spécifier plusieurs jours.  Cette énumération doit avoir l'attribut <xref:System.FlagsAttribute> et peut être appelée "jours".  Une énumération semblable qui permet uniquement à un jour d'être spécifié n'a pas d'attribut et peut être appelée "jour".  
  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent ainsi la durée de l'apprentissage requis par les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## Comment corriger les violations  
 Faites du nom de l'énumération un mot pluriel ou supprimez l'attribut <xref:System.FlagsAttribute> si plusieurs valeurs d'énumération ne doivent pas être spécifiées simultanément.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque une violation si le nom est un mot pluriel mais qu'il ne termine pas par "s".  À titre d'exemple, si l'énumération des plusieurs jours décrit précédemment a été nommée "JoursDeLaSemaine", la logique de la règle est enfreinte mais pas son intention.  De telles violations doivent être supprimées.  
  
## Règles connexes  
 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Voir aussi  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Conception d’énumérations](../Topic/Enum%20Design.md)