---
title: "CA1018&#160;: Marquer les attributs avec AttributeUsageAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018&#160;: Marquer les attributs avec AttributeUsageAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 L'attribut <xref:System.AttributeUsageAttribute?displayProperty=fullName> n'est pas présent sur l'attribut personnalisé.  
  
## Description de la règle  
 Lorsque vous définissez un attribut personnalisé, marquez\-le à l'aide de <xref:System.AttributeUsageAttribute> pour indiquer où l'attribut personnalisé peut être appliqué dans le code source.  La signification et l'utilisation prévue d'un attribut déterminent ses emplacements valides au sein d'un code.  Par exemple, vous pouvez définir un attribut qui identifie la personne qui est responsable de la maintenance et de l'amélioration de chaque type dans une bibliothèque, et cette responsabilité est toujours assignée au niveau du type.  Dans ce cas, les compilateurs doivent activer l'attribut sur des classes, des énumérations et des interfaces, mais ne doivent pas l'activer sur des méthodes, des événements ou des propriétés.  Les stratégies d'organisation et les procédures dicteraient si l'attribut doit être ou non activé sur des assemblys.  
  
 L'énumération <xref:System.AttributeTargets?displayProperty=fullName> définit les cibles que vous pouvez spécifier pour un attribut personnalisé.  Si vous omettez <xref:System.AttributeUsageAttribute>, votre attribut personnalisé sera valide pour toutes les cibles, comme défini par la valeur `All` de l'énumération de <xref:System.AttributeTargets>.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, spécifiez des cibles pour l'attribut à l'aide de <xref:System.AttributeUsageAttribute>.  Voir l'exemple suivant.  
  
## Quand supprimer les avertissements  
 Vous devez corriger une violation de cette règle au lieu d'exclure le message.  Même si l'attribut hérite de <xref:System.AttributeUsageAttribute>, il doit être présent pour simplifier la maintenance du code.  
  
## Exemple  
 L'exemple à suivre définit deux attributs.  `BadCodeMaintainerAttribute` ignore de manière incorrecte l'instruction <xref:System.AttributeUsageAttribute> et `GoodCodeMaintainerAttribute` implémente de manière correcte l'attribut décrit précédemment dans cette section.  Remarquez que la propriété `DeveloperName` est requise par la règle de design [CA1019 : Définir des accesseurs pour les arguments d'attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) et est intégrée à des fins d'exhaustivité.  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## Règles connexes  
 [CA1019 : Définir des accesseurs pour les arguments d'attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Voir aussi  
 [Attributs](../Topic/Attributes1.md)