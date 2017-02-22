---
title: "CA2237 : Marquer les types ISerializable avec SerializableAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2237 : Marquer les types ISerializable avec SerializableAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type visible extérieurement implémente l'interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> et n'est pas marqué avec l'attribut <xref:System.SerializableAttribute?displayProperty=fullName>.  La règle ignore des types dérivés dont le type de base n'est pas sérialisable.  
  
## Description de la règle  
 Pour être reconnus par le Common Language Runtime comme sérialisables, les types doivent être marqués de l'attribut <xref:System.SerializableAttribute> même s'ils utilisent une routine de sérialisation personnalisée par le biais de l'implémentation de l'interface <xref:System.Runtime.Serialization.ISerializable>.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appliquez l'attribut <xref:System.SerializableAttribute> au type.  
  
## Quand supprimer les avertissements  
 Ne supprimez pas d'avertissement de cette règle pour les classes d'exception car celles\-ci doivent être sérialisables pour fonctionner correctement à l'échelle des différents domaines d'application.  
  
## Exemple  
 L'exemple suivant présente un type qui enfreint la règle.  Supprimez les marques de commentaire de la ligne de l'attribut <xref:System.SerializableAttribute> pour satisfaire la règle.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## Règles connexes  
 [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240 : Implémentez ISerializable comme il se doit](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238 : Implémentez les méthodes de sérialisation comme il se doit](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120 : Sécurisez les constructeurs de sérialisation](../Topic/CA2120:%20Secure%20serialization%20constructors.md)