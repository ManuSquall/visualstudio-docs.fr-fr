---
title: 'CA2300 : N’utilisez pas le désérialiseur non sécurisé BinaryFormatter'
ms.date: 04/05/2019
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
- CA2300
- DoNotUseInsecureDeserializerBinaryFormatter
ms.openlocfilehash: 4ca4990308ceab21e2c6e256770ff37a3ca9a6fc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237953"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300 : N’utilisez pas le désérialiseur non sécurisé BinaryFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> méthode de désérialisation a été appelée ou référencée.

## <a name="rule-description"></a>Description de la règle

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Cette règle recherche <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> des appels ou des références de méthode de désérialisation. Si vous souhaitez désérialiser uniquement lorsque la propriété <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> est définie sur restreindre les types, désactivez cette règle et activez les règles [ca2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) et [ca2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) à la place.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Si possible, utilisez plutôt un sérialiseur sécurisé et **n’autorisez pas une personne malveillante à spécifier un type arbitraire à désérialiser**. Certains sérialiseurs plus sûrs sont les suivants :
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Ne jamais <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>utiliser. Si vous devez utiliser un programme de résolution de type, limitez les types désérialisés à une liste attendue.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-utilise TypeNameHandling. None. Si vous devez utiliser une autre valeur pour TypeNameHandling, limitez les types désérialisés à une liste attendue avec un ISerializationBinder personnalisé.
  - Mémoires tampon de protocole
- Rendez la falsification des données sérialisées. Après la sérialisation, signez les données sérialisées par chiffrement. Avant la désérialisation, validez la signature de chiffrement. Empêcher la clé de chiffrement d’être divulguée et concevoir des rotations de clés.
- Limitez les types désérialisés. Implémentez un <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>personnalisé. Avant de désérialiser <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>avec, affectez à la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriété une instance de <xref:System.Runtime.Serialization.SerializationBinder>votre personnalisé. Dans la méthode substituée <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , si le type est inattendu, levez une exception pour arrêter la désérialisation.
  - Si vous limitez les types désérialisés, vous pouvez désactiver cette règle et activer les règles [ca2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) et [ca2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). Les règles [ca2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) et [ca2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) permettent de s’assurer <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> que la propriété est toujours définie avant la désérialisation.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Règles associées

[CA2301 : N’appelez pas BinaryFormatter. Deserialize sans définir au préalable BinaryFormatter. Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302 : Vérifiez que BinaryFormatter. Binder est défini avant d’appeler BinaryFormatter. Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)