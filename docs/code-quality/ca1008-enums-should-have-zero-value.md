---
title: "CA1008&#160;: Les enums doivent avoir la valeur z&#233;ro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
helpviewer_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1008&#160;: Les enums doivent avoir la valeur z&#233;ro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture \- Lorsque vous êtes invité à ajouter une valeur **Aucun** à une énumération sans indicateur. Modification avec rupture \- Lorsque vous êtes invité à renommer ou à supprimer une valeur d'énumération.|  
  
## Cause  
 Une énumération sans un <xref:System.FlagsAttribute?displayProperty=fullName> appliqué ne définit pas de membre de valeur zéro ; ou une énumération avec un <xref:System.FlagsAttribute> appliqué définit un membre de valeur zéro, mais son nom n'est pas 'None', ou l'énumération définit plusieurs membres de valeur zéro.  
  
## Description de la règle  
 La valeur par défaut d'une énumération non initialisée, comme d'autres types valeur, est zéro.  Une énumération attribuée sans indicateur doit définir un membre de valeur zéro afin que la valeur par défaut soit une valeur valide de l'énumération.  Si besoin, nommez le membre 'None'.  Sinon, assignez zéro au membre le plus utilisé.  Remarquez que, par défaut, si la valeur du premier membre de l'énumération n'est pas définie dans la déclaration, sa valeur est zéro.  
  
 Si une énumération qui dispose du <xref:System.FlagsAttribute> appliquée définit un membre de valeur zéro, son nom doit être 'None' pour indiquer qu'aucune valeur n'a été définie dans l'énumération.  Utiliser un membre de valeur zéro à toute autre fin est contraire à l'utilisation du <xref:System.FlagsAttribute> en ce que les opérateurs de niveau bit AND et OR sont inutiles avec le membre.  Ce qui implique que seul un membre doit se voir assigner la valeur zéro.  Remarquez que si plusieurs membres ont pour valeur zéro dans une énumération attribuée par indicateurs, `Enum.ToString()` retourne des résultats inexacts dans le cas des membres non nuls.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle dans le cas d'énumérations attribuée sans indicateur, définissez un membre de valeur zéro ; il s'agit d'une modification sans rupture.  Dans le cas d'énumérations attribuées par indicateurs qui définissent un membre de valeur zéro, nommez ce membre 'None' et supprimez tout autre membre de valeur zéro ; il s'agit d'une modification avec rupture.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle, sauf dans le cas d'énumérations attribuées par indicateurs fournies antérieurement.  
  
## Exemple  
 L'exemple suivant présente deux énumérations qui satisfont la règle et une énumération, `BadTraceOptions`, qui l'enfreint.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-cs[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## Règles connexes  
 [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700 : Ne nommez pas les valeurs enum 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028 : Enum Storage doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## Voir aussi  
 <xref:System.Enum?displayProperty=fullName>