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
ms.openlocfilehash: e4af6bbfbd7e14b99f39ffa0adb5d1117c200d9a
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135427"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310 : N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> méthode de désérialisation a été appelé ou référencé.

## <a name="rule-description"></a>Description de la règle

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Cette règle recherche <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> la désérialisation des appels de méthode ou de références. Si vous souhaitez désérialiser uniquement lorsque le <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propriété est définie pour limiter les types, désactiver cette règle et activer les règles de [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) et [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) à la place.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Si possible, utilisez à la place, un sérialiseur sécurisé et **ne pas autoriser une personne malveillante spécifier un type arbitraire à désérialiser**. Certains sérialiseurs plus sûres sont les suivantes :
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> : Ne jamais utiliser <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Si vous devez utiliser un résolveur de type, restreindre les types désérialisées à une liste attendue.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET - utiliser TypeNameHandling.None. Si vous devez utiliser une autre valeur pour TypeNameHandling, restreindre les types désérialisées à une liste attendue avec un ISerializationBinder personnalisé.
  - Mémoires tampons de protocole
- Vérifiez la falsification de données sérialisées. Après la sérialisation, signer par chiffrement les données sérialisées. Avant la désérialisation, valider la signature de chiffrement. Protéger la clé de chiffrement ne soient divulgués et de la conception pour les rotations de clés.
- Restreindre les types désérialisées. Implémenter un <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Avant la désérialisation avec <xref:System.Runtime.Serialization.NetDataContractSerializer>, définissez le <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propriété à une instance de votre personnalisation <xref:System.Runtime.Serialization.SerializationBinder>. Dans l’élément substitué <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> méthode, si le type est inattendu, lever une exception.
- Si vous limitez les types désérialisées, voulez-vous désactiver cette règle et activer les règles de [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) et [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Règles [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) et [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) aide pour vous assurer que le <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propriété est toujours définie avant la désérialisation.

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

[CA2311 : Ne pas désérialiser sans définition préalable NetDataContractSerializer.Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312 : Vérifiez que NetDataContractSerializer.Binder est défini avant la désérialisation](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
