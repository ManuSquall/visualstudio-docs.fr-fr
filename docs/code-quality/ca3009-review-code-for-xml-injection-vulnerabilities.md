---
title: 'CA3009 : Passez en revue le code pour détecter les vulnérabilités de l’injection XML'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2daf2713175e9a512a31454ff4b76ef994bb809c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541218"
---
# <a name="ca3009-review-code-for-xml-injection-vulnerabilities"></a>CA3009 : Passez en revue le code pour détecter les vulnérabilités de l’injection XML

|||
|-|-|
|TypeName|ReviewCodeForXmlInjectionVulnerabilities|
|CheckId|CA3009|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Entrée de demande HTTP potentiellement non fiable atteint la sortie XML brute.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées, n’oubliez pas d’attaques par injection de XML. Une personne malveillante peut utiliser l’injection de code XML pour insérer des caractères spéciaux dans un document XML, rendant le document non valide XML. Ou bien, un attaquant pourrait insérer à des fins malveillantes des nœuds XML de leur choix.

Cette règle tente de trouver l’entrée à partir des demandes HTTP atteindre une écriture XML brute.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui écrit le code XML brut, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans `.editorconfig` fichiers.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Ne pas écrire du code XML brut. Au lieu de cela, utilisez méthodes ou propriétés ce XML à encoder leur entrée.

Ou bien, encoder en XML d’entrée avant d’écrire le code XML brut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne pas supprimer les avertissements de cette règle.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.Xml;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        XmlDocument d = new XmlDocument();
        XmlElement root = d.CreateElement("root");
        d.AppendChild(root);

        XmlElement allowedUser = d.CreateElement("allowedUser");
        root.AppendChild(allowedUser);

        allowedUser.InnerXml = "alice";

        // If an attacker uses this for input:
        //     some text<allowedUser>oscar</allowedUser>
        // Then the XML document will be:
        //     <root>some text<allowedUser>oscar</allowedUser></root>
        root.InnerXml = input;
    }
}
```

```vb
Imports System
Imports System.Xml

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim d As XmlDocument = New XmlDocument()
        Dim root As XmlElement = d.CreateElement("root")
        d.AppendChild(root)

        Dim allowedUser As XmlElement = d.CreateElement("allowedUser")
        root.AppendChild(allowedUser)

        allowedUser.InnerXml = "alice"

        ' If an attacker uses this for input:
        '     some text<allowedUser>oscar</allowedUser>
        ' Then the XML document will be:
        '     <root>some text<allowedUser>oscar</allowedUser></root>
        root.InnerXml = input
    End Sub
End Class
```

### <a name="solution"></a>Solution

```csharp
using System;
using System.Xml;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        XmlDocument d = new XmlDocument();
        XmlElement root = d.CreateElement("root");
        d.AppendChild(root);

        XmlElement allowedUser = d.CreateElement("allowedUser");
        root.AppendChild(allowedUser);

        allowedUser.InnerText = "alice";

        // If an attacker uses this for input:
        //     some text<allowedUser>oscar</allowedUser>
        // Then the XML document will be:
        //     <root>&lt;allowedUser&gt;oscar&lt;/allowedUser&gt;some text<allowedUser>alice</allowedUser></root>
        root.InnerText = input;
    }
}
```

```vb
Imports System
Imports System.Xml

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim d As XmlDocument = New XmlDocument()
        Dim root As XmlElement = d.CreateElement("root")
        d.AppendChild(root)

        Dim allowedUser As XmlElement = d.CreateElement("allowedUser")
        root.AppendChild(allowedUser)

        allowedUser.InnerText = "alice"

        ' If an attacker uses this for input:
        '     some text<allowedUser>oscar</allowedUser>
        ' Then the XML document will be:
        '     <root>&lt;allowedUser&gt;oscar&lt;/allowedUser&gt;some text<allowedUser>alice</allowedUser></root>
        root.InnerText = input
    End Sub
End Class
```
