---
title: "CA2235&#160;: Marquez tous les champs non s&#233;rialis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2235&#160;: Marquez tous les champs non s&#233;rialis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable.  
  
## Description de la règle  
 Un type sérialisable est marqué avec l'attribut <xref:System.SerializableAttribute?displayProperty=fullName>.  Lorsque le type est sérialisé, une exception <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> est levée si un type contient un champ d'instance d'un type qui n'est pas sérialisable.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appliquez l'attribut <xref:System.NonSerializedAttribute?displayProperty=fullName> au champ qui n'est pas sérialisable.  
  
## Quand supprimer les avertissements  
 Supprimez uniquement un avertissement de cette règle en cas de déclaration d'un type <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> qui autorise des instances du champ à être sérialisées et désérialisées.  
  
## Exemple  
 L'exemple suivant présente un type qui viole la règle et un autre qui satisfait la règle.  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## Règles connexes  
 [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240 : Implémentez ISerializable comme il se doit](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238 : Implémentez les méthodes de sérialisation comme il se doit](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120 : Sécurisez les constructeurs de sérialisation](../Topic/CA2120:%20Secure%20serialization%20constructors.md)