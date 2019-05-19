---
title: 'CA3007 : Passez en revue le code pour détecter les vulnérabilités de la redirection ouverte'
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
ms.openlocfilehash: e60d0fad1262138b57f079485bc7455e55c7ec25
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841341"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007 : Passez en revue le code pour détecter les vulnérabilités de la redirection ouverte

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Entrée de demande HTTP potentiellement non fiable atteint une redirection de la réponse HTTP.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées, n’oubliez pas de vulnérabilités de redirection ouverte. Un attaquant peut exploiter cette vulnérabilité par redirection ouverte pour utiliser votre site Web afin de donner l’apparence d’une URL légitime, mais si rediriger un visiteur peu méfiant à un anti-hameçonnage ou une autre page Web malveillant.

Cette règle tente de trouver des informations issues de requêtes HTTP atteindre une URL de redirection HTTP.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui répond avec une redirection HTTP, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans un fichier EditorConfig.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Certaines approches pour la correction des vulnérabilités de redirection ouverte sont les suivantes :

- Ne pas autoriser les utilisateurs à lancer les redirections.
- Ne pas autoriser les utilisateurs à spécifier n’importe quelle partie de l’URL dans un scénario de redirection.
- Limiter les redirections à un prédéfinis « liste verte » de l’URL.
- Valider des URL de redirection.
- Le cas échéant, envisagez d’utiliser une page d’exclusion de responsabilité lorsque les utilisateurs sont redirigés en dehors de votre site.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous savez que vous avez validé l’entrée doit être limité aux URL prévus, il est OK supprimer cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
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
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
