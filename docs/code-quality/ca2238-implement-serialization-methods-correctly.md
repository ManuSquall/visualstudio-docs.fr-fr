---
title: "CA2238&#160;: Impl&#233;mentez les m&#233;thodes de s&#233;rialisation comme il se doit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementSerializationMethodsCorrectly"
  - "CA2238"
helpviewer_keywords: 
  - "CA2238"
  - "ImplementSerializationMethodsCorrectly"
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2238&#160;: Impl&#233;mentez les m&#233;thodes de s&#233;rialisation comme il se doit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Avec rupture \- Si la méthode est visible à l'extérieur de l'assembly.<br /><br /> Sans rupture \- Si la méthode n'est pas visible à l'extérieur de l'assembly.|  
  
## Cause  
 Une méthode qui gère un événement de sérialisation n'a pas la signature, le type de retour ou la visibilité appropriée.  
  
## Description de la règle  
 Une méthode est désignée en tant que gestionnaire d'événements de sérialisation en s'appliquant l'un des attributs d'événement de sérialisation suivants :  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
 Les gestionnaires d'événements de sérialisation acceptent un unique paramètre de type <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, retournent `void` et présentent la visibilité `private`.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, corrigez la signature, le type de retour ou la visibilité du gestionnaire d'événements de sérialisation.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente des gestionnaires d'événements de sérialisation déclarés correctement.  
  
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-cs[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]  
  
## Règles connexes  
 [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240 : Implémentez ISerializable comme il se doit](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120 : Sécurisez les constructeurs de sérialisation](../Topic/CA2120:%20Secure%20serialization%20constructors.md)