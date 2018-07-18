---
title: Accès à Visual Studio ou à d'autres hôtes à partir d'un modèle de texte
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 657abba976e0f0d167651943289296d340981e62
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946515"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Accéder à Visual Studio ou autres hôtes à partir d’un modèle de texte

Dans un modèle de texte, vous pouvez utiliser les méthodes et propriétés qui sont exposées par l’hôte qui exécute le modèle. Visual Studio est un exemple d’un ordinateur hôte.

> [!NOTE]
> Vous pouvez utiliser les propriétés et méthodes de l’hôte dans les modèles de texte standard, mais pas dans *prétraité* modèles de texte.

## <a name="obtain-access-to-the-host"></a>Obtenir l’accès à l’hôte

Pour accéder à l’ordinateur hôte, définissez `hostspecific="true"` dans la `template` directive. Vous pouvez désormais utiliser `this.Host`, qui a le type <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Le <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> type possède des membres que vous pouvez utiliser, par exemple, pour résoudre les noms de fichiers et de consigner les erreurs.

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

### <a name="display-error-messages"></a>Afficher les Messages d’erreur

Cet exemple enregistre des messages lorsque vous transformez le modèle. Si l’hôte est Visual Studio, les erreurs sont ajoutés à la **liste d’erreurs**.

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

## <a name="use-the-visual-studio-api"></a>Utilisez l’API Visual Studio

Si l’exécution d’un modèle de texte dans Visual Studio, vous pouvez utiliser `this.Host` pour accéder aux services fournis par Visual Studio et des packages ou les extensions qui sont chargées.

Définissez hostspecific = « true » et effectuez un cast `this.Host` à <xref:System.IServiceProvider>.

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

## <a name="use-hostspecific-with-template-inheritance"></a>Utilisez hostSpecific avec héritage de modèle

Spécifiez `hostspecific="trueFromBase"` si vous utilisez également le `inherits` attribut, et si vous héritez d’un modèle qui spécifie `hostspecific="true"`. Si vous ne le faites pas, vous pouvez obtenir un avertissement qui du compilateur de la propriété `Host` a été déclarée deux fois.