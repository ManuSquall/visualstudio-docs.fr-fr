---
title: Directive du paramètre T4
description: Découvrez que dans Visual Studio, la directive de paramètre déclare des propriétés dans votre code de modèle qui sont initialisées à partir de valeurs transmises à partir du contexte externe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ef80179d43996669b9d883fd2ca9163208d18d7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386096"
---
# <a name="t4-parameter-directive"></a>Directive du paramètre T4

Dans un modèle de texte Visual Studio, la `parameter` directive déclare des propriétés dans votre code de modèle qui sont initialisées à partir de valeurs transmises à partir du contexte externe. Vous pouvez définir ces valeurs si vous écrivez du code qui appelle la transformation de texte.

## <a name="using-the-parameter-directive"></a>Utilisation de la directive Parameter

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 La `parameter` directive déclare des propriétés dans votre code de modèle qui sont initialisées à partir de valeurs transmises à partir du contexte externe. Vous pouvez définir ces valeurs si vous écrivez du code qui appelle la transformation de texte. Les valeurs peuvent être passées dans le `Session` dictionnaire, ou dans <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Vous pouvez déclarer des paramètres de n’importe quel type accessible à distance. Autrement dit, le type doit être déclaré avec <xref:System.SerializableAttribute> , ou il doit dériver de <xref:System.MarshalByRefObject> . Cela permet de passer les valeurs de paramètre dans l’AppDomain dans lequel le modèle est traité.

 Par exemple, vous pouvez écrire un modèle de texte avec le contenu suivant :

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Passage de valeurs de paramètre à un modèle
 Si vous écrivez une extension Visual Studio telle qu’une commande de menu ou un gestionnaire d’événements, vous pouvez traiter un modèle à l’aide du service de création de modèles de texte :

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));
```

## <a name="passing-values-in-the-call-context"></a>Passage de valeurs dans le contexte d’appel
 Vous pouvez également passer des valeurs en tant que données logiques dans <xref:System.Runtime.Remoting.Messaging.CallContext> .

 L’exemple suivant passe des valeurs à l’aide des deux méthodes :

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test
```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Passage de valeurs à un modèle de texte Run-Time (prétraité)
 Il n’est généralement pas nécessaire d’utiliser la `<#@parameter#>` directive avec les modèles de texte au moment de l’exécution (prétraités). Au lieu de cela, vous pouvez définir un constructeur supplémentaire ou une propriété définissable pour le code généré, par le biais duquel vous transmettez des valeurs de paramètre. Pour plus d’informations, consultez [génération de texte au moment de l’exécution avec des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Toutefois, si vous souhaitez utiliser `<#@parameter>` dans un modèle au moment de l’exécution, vous pouvez lui passer des valeurs à l’aide du dictionnaire de sessions. Par exemple, supposons que vous avez créé le fichier en tant que modèle prétraité nommé `PreTextTemplate1` . Vous pouvez appeler le modèle dans votre programme à l’aide du code suivant.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Obtention d’arguments à partir de TextTemplate.exe

> [!IMPORTANT]
> La `parameter` directive ne récupère pas les valeurs définies dans le `-a` paramètre de l' `TextTransform.exe` utilitaire. Pour récupérer ces valeurs, définissez `hostSpecific="true"` dans la `template` directive et utilisez `this.Host.ResolveParameterValue("","","argName")` .
