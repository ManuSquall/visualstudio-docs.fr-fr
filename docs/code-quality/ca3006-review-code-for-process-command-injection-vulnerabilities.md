---
title: 'CA3006 : Passez en revue le code pour détecter les vulnérabilités de l’injection de commande de processus'
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
ms.openlocfilehash: 986607d7f42f49c99396bbb021c48bad549930c9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237292"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006 : Passez en revue le code pour détecter les vulnérabilités de l’injection de commande de processus

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une entrée de requête HTTP potentiellement non approuvée atteint une commande Process.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non fiables, tenez-vous à l’esprit des attaques par injection de commande. Une attaque par injection de commande peut exécuter des commandes malveillantes sur le système d’exploitation sous-jacent, compromettant ainsi la sécurité et l’intégrité de votre serveur.

Cette règle tente de trouver une entrée à partir des requêtes HTTP qui atteignent une commande Process.

> [!NOTE]
> Cette règle ne peut pas effectuer le suivi des données dans les assemblys. Par exemple, si un assembly lit l’entrée de la requête HTTP, puis le passe à un autre assembly qui démarre un processus, cette règle ne génère pas d’avertissement.

> [!NOTE]
> Il existe une limite configurable de la profondeur de cette règle pour analyser le workflow des données entre les appels de méthode. Consultez [configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans un fichier baEditorConfig.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Si possible, évitez de démarrer les processus en fonction de l’entrée de l’utilisateur.
- Valider l’entrée par rapport à un ensemble de caractères et une longueur connus.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous savez que l’entrée a été validée ou placée dans une séquence d’échappement pour être sécurisée, il est possible de supprimer cet avertissement en toute sécurité.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.Diagnostics;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Process p = Process.Start(input);
    }
}
```

```vb
Imports System
Imports System.Diagnostics

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs as EventArgs)
        Dim input As String = Me.Request.Form("in")
        Dim p As Process = Process.Start(input)
    End Sub
End Class
```
