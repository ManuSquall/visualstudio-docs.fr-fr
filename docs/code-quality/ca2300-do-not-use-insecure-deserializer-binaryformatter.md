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
ms.openlocfilehash: 2e3ad5c23d880c65a57fdd94739475537c1aebff
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59367297"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300 : N’utilisez pas le désérialiseur non sécurisé BinaryFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> méthode de désérialisation a été appelé ou référencé.

## <a name="rule-description"></a>Description de la règle

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Cette règle recherche <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> la désérialisation des appels de méthode ou de références. Si vous souhaitez désérialiser uniquement lorsque le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriété est définie pour limiter les types, désactiver cette règle et activer les règles de [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) et [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) à la place.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Si possible, utilisez à la place, un sérialiseur sécurisé et **ne pas autoriser une personne malveillante spécifier un type arbitraire à désérialiser**. Certains sérialiseurs plus sûres sont les suivantes :
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> : Ne jamais utiliser <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Si vous devez utiliser un résolveur de type, vous devez restreindre les types désérialisées à une liste attendue.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - NewtonSoft Json.NET - utiliser TypeNameHandling.None. Si vous devez utiliser une autre valeur pour TypeNameHandling, vous devez restreindre les types désérialisées à une liste attendue.
  - Mémoires tampons de protocole
- Rendre les données sérialisées falsifications. Après la sérialisation, signer par chiffrement les données sérialisées. Avant la désérialisation, valider la signature de chiffrement. Vous devez protéger la clé de chiffrement ne soient divulgués et devez concevoir pour les rotations de clés.
- Restreindre les types désérialisées. Implémenter un <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Avant la désérialisation avec <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, définissez le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriété à une instance de votre personnalisation <xref:System.Runtime.Serialization.SerializationBinder>. Dans l’élément substitué <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> (méthode), si le type est inattendu une exception.
 - Si vous limitez les types désérialisées, voulez-vous désactiver cette règle et activer les règles de [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) et [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). L’activation des règles [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) et [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) permet de s’assurer que le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriété est toujours définie avant la désérialisation.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

- Il est possible de supprimer un avertissement de cette règle si vous connaissez que l’entrée est approuvée. Considérez que le flux de limite et les données de confiance de votre application peut changer au fil du temps.
- Il est possible de supprimer cet avertissement si vous avez pris un des précautions ci-dessus sans.

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

[CA2301 : N’appelez pas BinaryFormatter.Deserialize sans définition préalable BinaryFormatter.Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302 : Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)