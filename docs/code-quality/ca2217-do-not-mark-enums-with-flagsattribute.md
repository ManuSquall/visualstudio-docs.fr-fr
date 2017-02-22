---
title: "CA2217 : Ne pas marquer les enums avec FlagsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotMarkEnumsWithFlags"
  - "CA2217"
helpviewer_keywords: 
  - "CA2217"
  - "DoNotMarkEnumsWithFlags"
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2217 : Ne pas marquer les enums avec FlagsAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une énumération extérieurement visible est marquée par <xref:System.FlagsAttribute> et possède une ou plusieurs valeurs qui ne sont pas des puissances de deux ou d'une combinaison des autres valeurs définies dans l'énumération.  
  
## Description de la règle  
 Une énumération ne doit présenter <xref:System.FlagsAttribute> que si chaque valeur définie dans celle\-ci est une puissance de deux, ou une combinaison de valeurs définies.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez <xref:System.FlagsAttribute> de l'énumération.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant affiche une énumération de couleurs qui contient la valeur 3, qui n'est ni une puissance de deux, ni une combinaison de l'une des valeurs définies.  Cette énumération ne doit pas être marquée par l'attribut <xref:System.FlagsAttribute>.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## Exemple  
 L'exemple suivant affiche une énumération de jours qui satisfait aux exigences liées au marquage par l'attribut System.FlagsAttribute.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## Règles connexes  
 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## Voir aussi  
 <xref:System.FlagsAttribute?displayProperty=fullName>