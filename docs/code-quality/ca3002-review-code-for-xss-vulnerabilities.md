---
title: 'CA3002 : Passez en revue le code pour détecter les vulnérabilités des scripts XSS'
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
ms.openlocfilehash: 6bcf32401abdeae499097bc5187d11154e7dfc6e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237415"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002 : Passez en revue le code pour détecter les vulnérabilités des scripts XSS

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une entrée de requête HTTP potentiellement non approuvée atteint une sortie HTML brute.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées à partir de requêtes Web, gardez à l’esprit les attaques de script entre sites (XSS). Une attaque XSS injecte une entrée non fiable dans une sortie HTML brute, ce qui permet à la personne malveillante d’exécuter des scripts malveillants ou de modifier du contenu de manière malveillante dans votre page Web. Une technique classique consiste à `<script>` placer des éléments avec du code malveillant en entrée. Pour plus d’informations, consultez [OWASP XSS](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Cette règle tente de trouver une entrée à partir de requêtes HTTP pour atteindre une sortie HTML brute.

> [!NOTE]
> Cette règle ne peut pas effectuer le suivi des données dans les assemblys. Par exemple, si un assembly lit l’entrée de la requête HTTP, puis le passe à un autre assembly qui génère du code HTML brut, cette règle ne génère pas d’avertissement.

> [!NOTE]
> Il existe une limite configurable de la profondeur de cette règle pour analyser le workflow des données entre les appels de méthode. Consultez [configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans un fichier baEditorConfig.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Au lieu de sortir du code HTML brut, utilisez une méthode ou une propriété qui encode son entrée au format HTML.
- Encodez les données non approuvées au format HTML avant de sortir le HTML brut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle dans les cas suivants :
- Vous savez que l’entrée est validée par rapport à un ensemble connu de caractères ne contenant pas de code HTML.
- Vous savez que les données sont encodées en HTML d’une manière non détectée par cette règle.

> [!NOTE]
> Cette règle peut signaler des faux positifs pour certaines méthodes ou propriétés qui encodent leur entrée au format HTML.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
    End Sub
End Class
```

### <a name="solution"></a>Solution

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```