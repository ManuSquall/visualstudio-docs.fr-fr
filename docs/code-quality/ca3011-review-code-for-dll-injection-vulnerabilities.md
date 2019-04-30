---
title: 'CA3011 : Passez en revue le code pour détecter les vulnérabilités de l’injection de DLL'
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
ms.openlocfilehash: a6f3a2db89e35408a19cec47c971821fedf5f85a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541140"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011 : Passez en revue le code pour détecter les vulnérabilités de l’injection de DLL

|||
|-|-|
|TypeName|ReviewCodeForDllInjectionVulnerabilities|
|CheckId|CA3011|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Potentiellement non fiables de requête HTTP entrée atteint une méthode qui charge un assembly.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées, n’oubliez pas de chargement de code non fiable. Si votre application web charge de code non fiable, une personne malveillante peut être en mesure d’injecter des DLL malveillants dans votre processus et exécuter du code malveillant.

Cette règle tente de trouver l’entrée à partir d’une requête HTTP qui atteigne une méthode qui charge un assembly.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui charge un assembly, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans `.editorconfig` fichiers.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Ne pas charger les DLL non approuvés à partir de l’entrée d’utilisateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne pas supprimer les avertissements de cette règle.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.Reflection;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] rawAssembly = Convert.FromBase64String(input);
        Assembly.Load(rawAssembly);
    }
}
```

```vb
Imports System
Imports System.Reflection

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim rawAssembly As Byte() = Convert.FromBase64String(input)
        Assembly.Load(rawAssembly)
    End Sub
End Class
```
