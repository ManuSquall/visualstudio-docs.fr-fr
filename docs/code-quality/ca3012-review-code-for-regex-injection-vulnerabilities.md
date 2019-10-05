---
title: 'CA3012 : Passez en revue le code pour détecter les vulnérabilités de l’injection regex'
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
ms.openlocfilehash: 42808b3961b18a23f594800f9d0782c908c9b1ba
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237176"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012 : Passez en revue le code pour détecter les vulnérabilités de l’injection regex

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une entrée de requête HTTP potentiellement non approuvée atteint une expression régulière.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non fiables, soyez attentif aux attaques par injection de Regex. Une personne malveillante peut utiliser l’injection Regex pour modifier une expression régulière de manière malveillante, pour faire correspondre des résultats inattendus par l’expression régulière, ou pour faire en sorte que l’expression régulière consomme un processeur excessif, entraînant une attaque par déni de service.

Cette règle tente de trouver une entrée à partir des requêtes HTTP qui atteignent une expression régulière.

> [!NOTE]
> Cette règle ne peut pas effectuer le suivi des données dans les assemblys. Par exemple, si un assembly lit l’entrée de la requête HTTP, puis le passe à un autre assembly qui crée une expression régulière, cette règle ne génère pas d’avertissement.

> [!NOTE]
> Il existe une limite configurable de la profondeur de cette règle pour analyser le workflow des données entre les appels de méthode. Consultez [configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans un fichier baEditorConfig.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Certaines atténuations par rapport aux injections regex sont les suivantes :

- Utilisez toujours un [délai d’expiration de correspondance](/dotnet/standard/base-types/best-practices#use-time-out-values) lors de l’utilisation d’expressions régulières.
- Évitez d’utiliser des expressions régulières basées sur l’entrée d’utilisateur.
- Échapper les caractères spéciaux de l’entrée d' <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> utilisateur en appelant ou une autre méthode.
- Autorise uniquement les caractères non spéciaux de l’entrée d’utilisateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous savez que vous utilisez un [délai d’expiration de correspondance](/dotnet/standard/base-types/best-practices#use-time-out-values) et que l’entrée utilisateur ne contient pas de caractères spéciaux, il est possible de supprimer cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.Text.RegularExpressions;

public partial class WebForm : System.Web.UI.Page
{
    public string SearchableText { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string findTerm = Request.Form["findTerm"];
        Match m = Regex.Match(SearchableText, "^term=" + findTerm);
    }
}
```

```vb
Imports System
Imports System.Text.RegularExpressions

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Public Property SearchableText As String

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim findTerm As String = Request.Form("findTerm")
        Dim m As Match = Regex.Match(SearchableText, "^term=" + findTerm)
    End Sub
End Class
```
