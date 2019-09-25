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
ms.openlocfilehash: efd30a783f534d76f7f7f3fa18fd181dbe7e98a1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237235"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010 : Passez en revue le code pour détecter les vulnérabilités de l’injection XAML

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une entrée de requête http potentiellement non approuvée atteint <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> une méthode Load.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non fiables, tenez-vous à l’esprit des attaques par injection de code XAML. Le XAML est un langage de balisage qui représente directement l’instanciation d’objets et leur exécution. Cela signifie que les éléments créés en XAML peuvent interagir avec les ressources système (par exemple, l’accès réseau et l’e/s du système de fichiers). Si une personne malveillante peut contrôler l’entrée d' <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> un appel de méthode de chargement, l’attaquant peut exécuter du code.

Cette règle tente de trouver l’entrée à partir des requêtes http <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> qui atteignent une méthode Load.

> [!NOTE]
> Cette règle ne peut pas effectuer le suivi des données dans les assemblys. Par exemple, si un assembly lit l’entrée de la requête HTTP, puis le passe à un autre assembly qui charge le code XAML, cette règle ne génère pas d’avertissement.

> [!NOTE]
> Il existe une limite configurable de la profondeur de cette règle pour analyser le workflow des données entre les appels de méthode. Consultez [configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans un fichier baEditorConfig.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Ne chargez pas de code XAML non fiable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas les avertissements de cette règle.

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
