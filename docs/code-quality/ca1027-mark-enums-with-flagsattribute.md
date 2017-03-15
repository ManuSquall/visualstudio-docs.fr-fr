---
title: "CA1027&#160;: Marquer les enums avec FlagsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkEnumsWithFlags"
  - "CA1027"
helpviewer_keywords: 
  - "CA1027"
  - "MarkEnumsWithFlags"
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1027&#160;: Marquer les enums avec FlagsAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Les valeurs d'une énumération publique sont des puissances de deux ou des combinaisons d'autres valeurs définies dans l'énumération, et l'attribut <xref:System.FlagsAttribute?displayProperty=fullName> n'est pas présent.  Pour réduire le nombre de faux positifs, cette règle ne rapporte aucune violation dans le cas d'énumérations présentant des valeurs contiguës.  
  
## Description de la règle  
 Une énumération est un type valeur qui définit un jeu de constantes nommées associées.  Appliquez <xref:System.FlagsAttribute> à une énumération lorsque ses constantes nommées peuvent être combinées de manière pertinente.  Prenons l'exemple de l'énumération des jours de la semaine dans une application chargée de suivre les ressources disponibles chaque jour.  Si la disponibilité de chaque ressource est encodée à l'aide de l'énumération avec le <xref:System.FlagsAttribute> présent, toute combinaison de jours peut être représentée.  Sans l'attribut, un seul jour de la semaine peut être représenté.  
  
 Dans le cas des champs qui stockent des énumérations combinables, les valeurs d'énumération sont traitées individuellement comme des groupes de bits au sein de champs.  Par conséquent, de tels champs sont parfois désignés sous le nom de *champs de bits*.  Pour combiner des valeurs d'énumération destinées au stockage dans un champ de bits, utilisez les opérateurs booléens conditionnels.  Pour tester un champ de bits pour déterminer la présence ou non d'une valeur d'énumération spécifique, utilisez les opérateurs booléens logiques.  Pour qu'un champ de bits stocke et récupère correctement des valeurs d'énumération combinées, chaque valeur définie dans l'énumération doit être une puissance de deux.  Sinon, les opérateurs logiques booléens ne sont pas en mesure d'extraire les valeurs d'énumérations individuelles stockées dans le champ.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez <xref:System.FlagsAttribute> à l'énumération.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si vous ne souhaitez pas que les valeurs d'énumération soient combinables.  
  
## Exemple  
 Dans l'exemple suivant, `DaysEnumNeedsFlags` est une énumération qui satisfait les exigences liées à l'utilisation de <xref:System.FlagsAttribute>, mais en est dépourvue.  L'énumération `ColorEnumShouldNotHaveFlag` ne présente aucune valeur exprimée en puissance de deux, mais spécifie <xref:System.FlagsAttribute> de manière incorrecte.  Ainsi, la règle [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md) est violée.  
  
 [!CODE [FxCop.Design.EnumFlags#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags#1)]  
  
## Règles connexes  
 [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Voir aussi  
 <xref:System.FlagsAttribute?displayProperty=fullName>