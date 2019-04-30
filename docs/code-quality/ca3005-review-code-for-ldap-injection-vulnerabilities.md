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
ms.openlocfilehash: 38c28153fa513c4f4db5b3a7833d279674f66734
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541296"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005 : Passez en revue le code pour détecter les vulnérabilités de l’injection LDAP

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Entrée de demande HTTP potentiellement non fiable atteint une instruction LDAP.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées, n’oubliez pas d’attaques par injection de Lightweight Directory Access Protocol (LDAP). Un attaquant peut éventuellement l’exécuter les instructions LDAP malveillantes par rapport aux annuaires d’informations. Les applications qui utilisent l’entrée d’utilisateur à créer des instructions pour accéder aux services d’annuaire LDAP dynamiques sont particulièrement vulnérables.

Cette règle tente de trouver des informations issues de requêtes HTTP atteint une instruction LDAP.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui exécute une instruction LDAP, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans `.editorconfig` fichiers.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour la partie contrôlée par l’utilisateur des instructions de LDAP, envisagez l’une des :
- Autoriser uniquement la liste des caractères spéciaux non safe.
- Interdire les caractères spéciaux
- Séquence d’échappement des caractères spéciaux.

Consultez [LDAP Injection Prevention Cheat Sheet de OWASP](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) pour obtenir des instructions.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous connaissez l’entrée a été validée ou séquence d’échappement pour plus de sécurité, il est OK supprimer cet avertissement.

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
