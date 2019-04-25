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
ms.openlocfilehash: a10f72297746a1e7bda3c69f8f7daf0efacd20bc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115612"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002 : Passez en revue le code pour détecter les vulnérabilités des scripts XSS

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Entrée de demande HTTP potentiellement non fiable atteint une sortie HTML brute.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées des requêtes web, n’oubliez pas d’attaques par (XSS) de scripts entre sites. Une attaque XSS injecte des entrées non approuvées dans HTML brut de la sortie, qui lui permet d’exécuter des scripts malveillants ou à des fins malveillantes modifier du contenu dans votre page web. Place d’une technique classique `<script>` éléments contenant du code malveillant d’entrée. Pour plus d’informations, consultez [XSS de OWASP](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Cette règle tente de trouver l’entrée à partir des demandes HTTP atteindre une sortie HTML brute.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et transmet ensuite à un autre assembly qui génère le code HTML brut, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans `.editorconfig` fichiers.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Au lieu de la sortie HTML brut, utilisez une méthode ou propriété ce premier au format HTML son entrée.
- Données non fiables encoder en HTML avant de sortir le HTML brut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si :
- Vous savez que l’entrée est validée par rapport à un ensemble sûr connu de caractères ne contenant ne pas de HTML.
- Vous savez que les données sont encodées en HTML de manière non détectée par cette règle.

> [!NOTE]
> Cette règle peut signaler des faux positifs pour certaines méthodes ou propriétés que-encoder en HTML leur entrée.

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