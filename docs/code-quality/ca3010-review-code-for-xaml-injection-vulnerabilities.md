---
title: 'CA3010 : Passez en revue le code pour détecter les vulnérabilités de l’injection XAML'
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
ms.openlocfilehash: ea53f5e0cddf1dc6c6caf4c7fcfb79af52ce354e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806522"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010 : Passez en revue le code pour détecter les vulnérabilités de l’injection XAML

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Potentiellement non fiable demande HTTP d’entrée atteint un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> méthode de charge.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées, n’oubliez pas d’attaques par injection de XAML. Le XAML est un langage de balisage qui représente directement l’instanciation d’objets et leur exécution. Cela signifie que les éléments créés dans XAML peuvent interagir avec les ressources système (par exemple, accès et fichier système réseau d’e/s). Si un attaquant peut contrôler l’entrée à un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> charger l’appel de méthode, puis l’attaquant peut exécuter du code.

Cette règle tente de trouver l’entrée à partir de requêtes HTTP qui atteigne un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> méthode de charge.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui charge le XAML, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans `.editorconfig` fichiers.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Ne pas charger XAML non approuvé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne pas supprimer les avertissements de cette règle.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
