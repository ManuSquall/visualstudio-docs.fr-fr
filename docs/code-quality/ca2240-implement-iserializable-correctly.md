---
title: "CA2240 : Implémentez ISerializable correctement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b60f145d31b966ebdc05af975baf5c862cc76251
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240 : Implémentez ISerializable comme il se doit
|||  
|-|-|  
|TypeName|ImplementISerializableCorrectly|  
|CheckId|CA2240|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type visible de l’extérieur ne peut être assigné à la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface et une des conditions suivantes est vraie :  
  
-   Le type hérite mais ne remplace pas le <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> (méthode) et le type déclare des champs d’instance qui ne sont pas marqués avec le <xref:System.NonSerializedAttribute?displayProperty=fullName> attribut.  
  
-   Le type n’est pas sealed et le type implémente une <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode qui n’est pas visible et substituable de façon externe.  
  
## <a name="rule-description"></a>Description de la règle  
 Champs d’instance qui sont déclarés dans un type qui hérite du <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface ne sont pas inclus automatiquement dans le processus de sérialisation. Pour inclure les champs, le type doit implémenter la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> (méthode) et le constructeur de sérialisation. Si les champs ne doivent pas être sérialisés, appliquez le <xref:System.NonSerializedAttribute> pour les champs pour indiquer explicitement la décision d’attribut.  
  
 Pour les types non sealed, les implémentations de la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode doit être visible de l’extérieur. Par conséquent, la méthode peut être appelée par des types dérivés et est substituable.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez le <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode visible et substituable et assurez-vous que tous les champs d’instance sont inclus dans le processus de sérialisation ou sont marqués explicitement avec le <xref:System.NonSerializedAttribute> attribut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux types sérialisables qui enfreint la règle.  
  
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant résout les deux violations ci-dessus en fournissant une implémentation substituable de <xref:System.Runtime.Serialization.ISerializable.GetObjectData> sur la classe Book et en fournissant une implémentation de `GetObjectData` sur la classe de bibliothèque.  
  
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)  
 [CA2238 : Implémentez les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
 [CA2235 : Marquez tous les champs non sérialisables](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
 [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
 [CA2120 : Sécurisez les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)  
