---
title: 'CA2229 : Implémentez des constructeurs de sérialisation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04906c737c7581b0b1a0c5a3dcc80407aa35659a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229 : Implémentez des constructeurs de sérialisation
|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Le type implémente le <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> de l’interface n’est pas un délégué ou une interface, et une des conditions suivantes est remplie :  
  
-   Le type n’a pas de constructeur qui accepte un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objet et un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objet (la signature du constructeur de sérialisation).  
  
-   Le type est non scellé, et le modificateur d’accès pour son constructeur de sérialisation n’est pas protégé (famille).  
  
-   Le type est sealed et le modificateur d’accès pour son constructeur de sérialisation n’est pas privé.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle s’applique pour les types qui prennent en charge la sérialisation personnalisée. Un type prend en charge la sérialisation personnalisée s’il implémente la <xref:System.Runtime.Serialization.ISerializable> interface. Le constructeur de sérialisation est requis pour désérialiser ou recréer des objets qui ont été sérialisés à l’aide de la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> (méthode).  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez pas une violation de la règle. Impossible de désérialiser le type et ne fonctionnera pas dans de nombreux scénarios.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui satisfait la règle.  
  
 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>