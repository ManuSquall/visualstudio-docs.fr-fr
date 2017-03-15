---
title: "CA2236&#160;: Appelez les m&#233;thodes de la classe de base sur les types ISerializable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2236&#160;: Appelez les m&#233;thodes de la classe de base sur les types ISerializable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type dérive d'un type qui implémente l'interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, et une des conditions suivantes est vraie :  
  
-   Le type implémente le constructeur de sérialisation, c'est\-à\-dire un constructeur doté de la signature de paramètre <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, mais n'appelle pas le constructeur de sérialisation du type de base.  
  
-   Le type implémente la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> mais n'appelle pas la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> du type de base.  
  
## Description de la règle  
 Dans un processus de sérialisation personnalisé, un type implémente la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> pour sérialiser ses champs, et implémente le constructeur de sérialisation pour les désérialiser.  Si le type dérive d'un type qui implémente l'interface <xref:System.Runtime.Serialization.ISerializable>, la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> et le constructeur de sérialisation du type de base doivent être appelés pour sérialiser\/désérialiser les champs du type de base.  Sinon, le type ne sera pas correctement sérialisé et désérialisé.  Remarquez que si le type dérivé n'ajoute aucun champ nouveau, le type n'a besoin d'implémenter ni la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> ni le constructeur de sérialisation, ni encore d'appeler les équivalents du type de base.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> ou le constructeur de sérialisation du type de base issus du constructeur ou de la méthode du type dérivé correspondant.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente un type dérivé qui satisfait la règle en appelant le constructeur de sérialisation et la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> de la classe de base.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## Règles connexes  
 [CA2240 : Implémentez ISerializable comme il se doit](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238 : Implémentez les méthodes de sérialisation comme il se doit](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120 : Sécurisez les constructeurs de sérialisation](../Topic/CA2120:%20Secure%20serialization%20constructors.md)