---
title: "CA2229&#160;: Impl&#233;mentez des constructeurs de s&#233;rialisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2229&#160;: Impl&#233;mentez des constructeurs de s&#233;rialisation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Le type implémente l'interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, n'est ni un délégué ni une interface, et l'une des conditions suivantes est vraie :  
  
-   Le type ne dispose d'aucun constructeur qui accepte un objet <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> et un objet <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> \(la signature du constructeur de sérialisation\).  
  
-   Le type est non\-sealed \(non scellé\) et le modificateur d'accès pour son constructeur de sérialisation n'est pas protégé \(famille\).  
  
-   Le type est sealed \(scellé\) et le modificateur d'accès pour son constructeur de sérialisation n'est pas privé.  
  
## Description de la règle  
 Cette règle est pertinente pour les types qui prennent en charge la sérialisation personnalisée.  Un type prend en charge la sérialisation personnalisée s'il implémente l'interface <xref:System.Runtime.Serialization.ISerializable>.  Le constructeur de sérialisation est tenu de désérialiser ou de recréer des objets qui ont été sérialisés à l'aide de la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation.  Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez\-lui l'état protégé.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucune violation de la règle.  Le type ne sera pas désérialisable et ne fonctionnera pas dans de nombreux scénarios.  
  
## Exemple  
 L'exemple suivant présente un type qui satisfait la règle.  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## Règles connexes  
 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>