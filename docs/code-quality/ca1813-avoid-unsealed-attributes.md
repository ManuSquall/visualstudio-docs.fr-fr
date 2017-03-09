---
title: "CA1813&#160;: &#201;vitez les attributs unsealed | Microsoft Docs"
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
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813&#160;: &#201;vitez les attributs unsealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public hérite de <xref:System.Attribute?displayProperty=fullName>, n'est pas abstrait et n'est pas sealed \(scellé\) \(`NotInheritable` en Visual Basic\).  
  
## Description de la règle  
 La bibliothèque de classes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fournit des méthodes pour récupérer des attributs personnalisés.  Par défaut, ces méthodes recherchent la hiérarchie d'héritage d'attributs ; par exemple, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> recherche le type d'attribut spécifié, ou tout type d'attribut qui étend le type d'attribut spécifié.  Sceller l'attribut élimine la recherche par le biais de la hiérarchie d'héritage et peut améliorer les performances.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, scellez le type d'attribut ou rendez\-le abstrait.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle.  Vous ne devez le faire que si vous définissez une hiérarchie d'attributs et ne pouvez ni sceller l'attribut, ni le rendre abstrait.  
  
## Exemple  
 L'exemple suivant montre un attribut personnalisé qui satisfait cette règle.  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## Règles connexes  
 [CA1019 : Définir des accesseurs pour les arguments d'attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018 : Marquer les attributs avec AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## Voir aussi  
 [Attributs](../Topic/Attributes1.md)