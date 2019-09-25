---
title: 'CA2310 : N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer'
ms.date: 05/01/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: 5335e72307ea201ad77d6e59b267572d4d9aae56
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237717"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310 : N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> méthode de désérialisation a été appelée ou référencée.

## <a name="rule-description"></a>Description de la règle

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Cette règle recherche <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> des appels ou des références de méthode de désérialisation. Si vous souhaitez désérialiser uniquement lorsque la propriété <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> est définie sur restreindre les types, désactivez cette règle et activez les règles [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) et [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) à la place.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Si possible, utilisez plutôt un sérialiseur sécurisé et **n’autorisez pas une personne malveillante à spécifier un type arbitraire à désérialiser**. Certains sérialiseurs plus sûrs sont les suivants :
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Ne jamais <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>utiliser. Si vous devez utiliser un programme de résolution de type, limitez les types désérialisés à une liste attendue.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-utilise TypeNameHandling. None. Si vous devez utiliser une autre valeur pour TypeNameHandling, limitez les types désérialisés à une liste attendue avec un ISerializationBinder personnalisé.
  - Mémoires tampon de protocole
- Rendez la falsification des données sérialisées. Après la sérialisation, signez les données sérialisées par chiffrement. Avant la désérialisation, validez la signature de chiffrement. Empêcher la clé de chiffrement d’être divulguée et concevoir des rotations de clés.
- Limitez les types désérialisés. Implémentez un <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>personnalisé. Avant de désérialiser <xref:System.Runtime.Serialization.NetDataContractSerializer>avec, affectez à la <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propriété une instance de <xref:System.Runtime.Serialization.SerializationBinder>votre personnalisé. Dans la méthode substituée <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , si le type est inattendu, levez une exception pour arrêter la désérialisation.
  - Si vous limitez les types désérialisés, vous pouvez désactiver cette règle et activer les règles [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) et [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Les règles [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) et [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) permettent de s’assurer <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> que la propriété est toujours définie avant la désérialisation.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Règles associées

[CA2311: Ne pas désérialiser sans définir au préalable NetDataContractSerializer. Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Vérifiez que NetDataContractSerializer. Binder est défini avant la désérialisation](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
