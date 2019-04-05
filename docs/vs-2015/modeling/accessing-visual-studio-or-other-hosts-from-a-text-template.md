---
title: L’accès à Visual Studio 2015 ou autres hôtes à partir d’un modèle de texte | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d26c168780051d3644d04d209001bf0cc9a551cb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953202"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Accès à Visual Studio ou à d'autres hôtes à partir d'un modèle de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un modèle de texte, vous pouvez utiliser les méthodes et propriétés exposées par l’hôte qui exécute le modèle, tel que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Cela s’applique aux modèles de texte standard, les modèles de texte prétraités pas.

## <a name="obtaining-access-to-the-host"></a>Obtention de l’accès à l’hôte
 Définissez `hostspecific="true"` dans la `template` directive. Cela vous permet d’utiliser `this.Host`, qui a le type <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Ce type possède des membres que vous pouvez utiliser, par exemple, pour résoudre les noms de fichier et enregistrer les erreurs.

### <a name="resolving-file-names"></a>Résolution des noms de fichiers
 Pour rechercher le chemin d’accès complet d’un fichier relatif au modèle de texte, l’utiliser. Host.ResolvePath().

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

### <a name="displaying-error-messages"></a>Affichage des Messages d’erreur
 Cet exemple montre comment les messages des journaux lorsque vous transformez le modèle. Si l’hôte est [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ils sont ajoutés à la fenêtre d’erreur.

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

## <a name="using-the-visual-studio-api"></a>À l’aide de l’API Visual Studio
 Si vous exécutez un modèle de texte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez utiliser `this.Host` pour accéder aux services fournis par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et des packages ou les extensions qui sont chargées.

 Définissez hostspecific = « true » et effectuez un cast `this.Host` à <xref:System.IServiceProvider>.

 Cet exemple obtient le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, <xref:EnvDTE.DTE>, en tant que service :

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

## <a name="using-hostspecific-with-template-inheritance"></a>À l’aide de hostSpecific avec l’héritage de modèle
 Spécifiez `hostspecific="trueFromBase"` si vous utilisez également le `inherits` attribut, et si vous héritez d’un modèle qui spécifie `hostspecific="true"`. Cela permet d’éviter un avertissement du compilateur à l’effet que la propriété `Host` a été déclarée deux fois.
