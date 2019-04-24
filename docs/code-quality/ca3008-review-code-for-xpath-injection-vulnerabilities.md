---
title: 'CA3008 : Passez en revue le code pour détecter les vulnérabilités de l’injection XPath'
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
ms.openlocfilehash: e66b75160df0e8ecf9d33601ee383ec71cd62c4d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044809"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008 : Passez en revue le code pour détecter les vulnérabilités de l’injection XPath

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|CheckId|CA3008|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Entrée de demande HTTP potentiellement non fiable atteint une requête XPath.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées, n’oubliez pas d’attaques par injection de XPath. Construire des requêtes XPath à l’aide d’entrées non approuvées peut permettre à un attaquant à des fins malveillantes manipuler la requête pour retourner un résultat inattendu et éventuellement divulguer le contenu du fichier XML demandé. 

Cette règle tente de trouver des informations issues de requêtes HTTP atteint une expression XPath.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui effectue une requête XPath, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans `.editorconfig` fichiers.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Certaines approches pour résoudre les vulnérabilités d’injection XPath sont les suivantes :

- Ne construire des requêtes XPath à partir de l’entrée d’utilisateur.
- Vérifiez que l’entrée contient uniquement un ensemble sûr de caractères.
- Séquence d’échappement des guillemets.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous savez que vous avez validé l’entrée pour plus de sécurité, il est OK supprimer cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")
        
        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```
