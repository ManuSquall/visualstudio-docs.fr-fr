---
title: Accès à Visual Studio ou à d'autres hôtes à partir d'un modèle de texte
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652361"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Accéder à Visual Studio ou à d’autres hôtes à partir d’un modèle de texte

Dans un modèle de texte, vous pouvez utiliser des méthodes et des propriétés exposées par l’hôte qui exécute le modèle. Visual Studio est un exemple d’hôte.

> [!NOTE]
> Vous pouvez utiliser des méthodes et des propriétés d’hôte dans des modèles de texte standard, mais pas dans des modèles de texte *prétraités* .

## <a name="obtain-access-to-the-host"></a>Obtenir l’accès à l’hôte

Pour accéder à l’hôte, définissez `hostspecific="true"` dans la directive `template`. Vous pouvez maintenant utiliser `this.Host`, qui a le type [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Le type [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) contient des membres que vous pouvez utiliser pour résoudre les noms de fichiers et les erreurs de journal, par exemple.

### <a name="resolve-file-names"></a>Résoudre les noms de fichiers

Pour rechercher le chemin d’accès complet d’un fichier relatif au modèle de texte, utilisez `this.Host.ResolvePath()`.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Afficher les messages d’erreur

Cet exemple consigne des messages lorsque vous transformez le modèle. Si l’hôte est Visual Studio, les erreurs sont ajoutées au **liste d’erreurs**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Utiliser l’API Visual Studio

Si vous exécutez un modèle de texte dans Visual Studio, vous pouvez utiliser `this.Host` pour accéder aux services fournis par Visual Studio et aux packages ou extensions chargés.

Définissez hostspecific = "true" et effectuez un cast `this.Host` en <xref:System.IServiceProvider>.

Cet exemple obtient l’API Visual Studio, <xref:EnvDTE.DTE>, en tant que service :

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Utiliser hostSpecific avec l’héritage de modèle

Spécifiez `hostspecific="trueFromBase"` si vous utilisez également l’attribut `inherits`, et si vous héritez d’un modèle qui spécifie `hostspecific="true"`. Si vous ne le faites pas, vous pouvez obtenir un avertissement du compilateur indiquant que la propriété `Host` a été déclarée deux fois.