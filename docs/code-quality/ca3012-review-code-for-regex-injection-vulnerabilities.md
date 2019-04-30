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
ms.openlocfilehash: 114b44ec566554c81f5caf3b8ac474f9c5a75c07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806444"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012 : Passez en revue le code pour détecter les vulnérabilités de l’injection regex

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Entrée de demande HTTP potentiellement non fiable atteint une expression régulière.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées, n’oubliez pas d’attaques par injection de regex. Une personne malveillante permettent l’injection d’expression régulière à des fins malveillantes modifient une expression régulière, pour rendre l’expression régulière correspond à des résultats inattendus, ou pour apporter à l’expression régulière de consommer trop de ressources processeur résultant dans une attaque par déni de Service.

Cette règle tente de trouver des informations issues de requêtes HTTP atteint une expression régulière.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui crée une expression régulière, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans `.editorconfig` fichiers.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Certaines solutions d’atténuation contre les injections d’expressions régulières sont les suivantes :

- Utilisez toujours un [correspond à délai d’expiration](/dotnet/standard/base-types/best-practices#use-time-out-values) lors de l’utilisation d’expressions régulières.
- Évitez d’utiliser des expressions régulières, selon l’entrée utilisateur.
- Séquence d’échappement de caractères spéciaux à partir de l’entrée d’utilisateur en appelant <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> ou une autre méthode.
- Autoriser les caractères uniquement non spéciale de l’entrée utilisateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous savez que vous utilisez un [correspond à délai d’attente](/dotnet/standard/base-types/best-practices#use-time-out-values) et l’entrée d’utilisateur est libre de caractères spéciaux, il est OK supprimer cet avertissement.

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
