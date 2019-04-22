---
title: 'CA2302 : Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize'
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
ms.openlocfilehash: fb997d8184ea9459b46eee95bfe2863e8c1c6ed0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59367287"
---
# <a name="ca2302-ensure-binaryformatterbinder-is-set-before-calling-binaryformatterdeserialize"></a>CA2302 : Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize

|||
|-|-|
|TypeName|EnsureBinaryFormatterBinderIsSetBeforeCallingBinaryFormatterDeserialize|
|CheckId|CA2302|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> méthode de désérialisation a été appelé ou référencé et le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriété peut être null.

## <a name="rule-description"></a>Description de la règle

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Cette règle recherche <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> la désérialisation des appels de méthode ou de références, lorsque <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lors de son <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> peut être null. Si vous souhaitez interdire toute la désérialisation avec <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> quel que soit le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriété, désactiver cette règle et [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)et activer sa règle [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

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
  - Assurez-vous que tous les chemins de code ont le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> jeu de propriétés.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

- Il est possible de supprimer un avertissement de cette règle si vous connaissez que l’entrée est approuvée. Considérez que le flux de limite et les données de confiance de votre application peut changer au fil du temps.
- Il est possible de supprimer cet avertissement si vous avez pris un des précautions ci-dessus sans.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BinaryFormatter Formatter { get; set; }

    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) this.Formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Property Formatter As BinaryFormatter

    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(Me.Formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Solution
```csharp
using System;
using System.IO;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Binary;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", "typeName");
        }
    }
}

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        formatter.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization
Imports System.Runtime.Serialization.Formatters.Binary

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", "typeName")
        End If
    End Function
End Class

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        formatter.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Règles associées

[CA2300 : N’utilisez pas le désérialiseur non sécurisé BinaryFormatter](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2301 : N’appelez pas BinaryFormatter.Deserialize sans définition préalable BinaryFormatter.Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)
