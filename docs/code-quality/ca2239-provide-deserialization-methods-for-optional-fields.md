---
title: "CA2239 : Sp&#233;cifiez des m&#233;thodes de d&#233;s&#233;rialisation pour les champs facultatifs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2239 : Sp&#233;cifiez des m&#233;thodes de d&#233;s&#233;rialisation pour les champs facultatifs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type présente un champ marqué avec l'attribut <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> et ne fournit aucune méthode de gestion des événements de désérialisation.  
  
## Description de la règle  
 L'attribut <xref:System.Runtime.Serialization.OptionalFieldAttribute> n'a aucun effet sur la sérialisation ; un champ marqué avec l'attribut est sérialisé.  Toutefois, le champ est ignoré en cas de désérialisation et conserve la valeur par défaut associée à son type.  Les gestionnaires d'événements de désérialisation doivent être déclarés pour définir le champ au cours du processus de désérialisation.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez au type des méthodes de gestion des événements de désérialisation.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le champ doit être ignoré au cours du processus de désérialisation.  
  
## Exemple  
 L'exemple suivant présente un type doté d'un champ et de méthodes de gestion des événements de désérialisation facultatifs.  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## Règles connexes  
 [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240 : Implémentez ISerializable comme il se doit](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238 : Implémentez les méthodes de sérialisation comme il se doit](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120 : Sécurisez les constructeurs de sérialisation](../Topic/CA2120:%20Secure%20serialization%20constructors.md)