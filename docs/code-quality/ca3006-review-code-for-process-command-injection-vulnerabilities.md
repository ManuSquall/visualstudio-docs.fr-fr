---
title: 'CA3006 : Passez en revue de code pour les vulnérabilités d’injection de commande de processus'
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
ms.openlocfilehash: da161e611ca1d802c8da16370907029233bfd785
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018531"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006 : Passez en revue de code pour les vulnérabilités d’injection de commande de processus

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Entrée de demande HTTP potentiellement non fiable atteint une commande de processus.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées, n’oubliez pas d’attaques par injection de commande. Une attaque par injection de commande peut exécuter des commandes nuisibles sur le système d’exploitation sous-jacent, compromettre la sécurité et l’intégrité de votre serveur.

Cette règle tente de trouver des informations issues de parvenir à une commande traiter les requêtes HTTP.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui démarre un processus, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans `.editorconfig` fichiers.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Si possible, évitez de démarrage des processus en fonction de l’entrée d’utilisateur.
- Valider l’entrée par rapport à un ensemble sûr connu de caractères et de longueur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous connaissez l’entrée a été validée ou séquence d’échappement pour plus de sécurité, il est possible de supprimer cet avertissement sans.

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
