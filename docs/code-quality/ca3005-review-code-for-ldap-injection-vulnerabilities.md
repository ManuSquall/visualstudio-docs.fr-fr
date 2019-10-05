---
title: 'CA3005 : Passez en revue le code pour détecter les vulnérabilités de l’injection LDAP'
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
ms.openlocfilehash: c0c99d5d0adb145a061693f8a83b1f674e05eed4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237340"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005 : Passez en revue le code pour détecter les vulnérabilités de l’injection LDAP

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une entrée de requête HTTP potentiellement non approuvée atteint une instruction LDAP.

## <a name="rule-description"></a>Description de la règle

Lors de l’utilisation d’une entrée non fiable, tenez à l’esprit des attaques par injection LDAP (Lightweight Directory Access Protocol). Une personne malveillante peut potentiellement exécuter des instructions LDAP malveillantes sur des répertoires d’informations. Les applications qui utilisent une entrée d’utilisateur pour construire des instructions LDAP dynamiques pour accéder aux services d’annuaire sont particulièrement vulnérables.

Cette règle tente de trouver une entrée à partir de requêtes HTTP qui atteignent une instruction LDAP.

> [!NOTE]
> Cette règle ne peut pas effectuer le suivi des données dans les assemblys. Par exemple, si un assembly lit l’entrée de la requête HTTP, puis le transmet à un autre assembly qui exécute une instruction LDAP, cette règle ne génère pas d’avertissement.

> [!NOTE]
> Il existe une limite configurable de la profondeur de cette règle pour analyser le workflow des données entre les appels de méthode. Consultez [configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans un fichier baEditorConfig.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour la partie contrôlée par l’utilisateur des instructions LDAP, envisagez l’une des opérations suivantes :
- Autorisez uniquement une liste sécurisée de caractères non spéciaux.
- Interdire le caractère spécial
- Caractères spéciaux d’échappement.

Pour plus d’informations, consultez l’aide-mémoire sur [la prévention de l’injection LDAP de OWASP](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous savez que l’entrée a été validée ou placée dans une séquence d’échappement pour être sécurisée, il est possible de supprimer cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*).
        // The resulting LDAP statement will make the server return any object that
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*).
        ' The resulting LDAP statement will make the server return any object that
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
