---
title: Accès à Visual Studio 2015 ou à d’autres hôtes à partir d’un modèle de texte | Microsoft Docs
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
ms.openlocfilehash: 053e8b09fd2b52683238f1ffe008e5e7d38b3962
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872003"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Accès à Visual Studio ou à d'autres hôtes à partir d'un modèle de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un modèle de texte, vous pouvez utiliser les méthodes et les propriétés exposées par l’hôte qui exécute le modèle, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]par exemple.

 Cela s’applique aux modèles de texte normaux, et non aux modèles de texte prétraités.

## <a name="obtaining-access-to-the-host"></a>Obtention de l’accès à l’hôte

Défini `hostspecific="true"` dans la `template` directive. Cela vous permet d' `this.Host`utiliser, qui a le type [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Ce type contient des membres que vous pouvez utiliser, par exemple, pour résoudre les noms de fichiers et pour consigner les erreurs.

### <a name="resolving-file-names"></a>Résolution des noms de fichiers
 Pour rechercher le chemin d’accès complet d’un fichier relatif au modèle de texte, utilisez cette. Host. ResolvePath ().

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

### <a name="displaying-error-messages"></a>Affichage des messages d’erreur
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

## <a name="using-the-visual-studio-api"></a>Utilisation de l’API Visual Studio
 Si vous exécutez un modèle de texte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez utiliser `this.Host` pour accéder aux services fournis par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et aux packages ou extensions chargés.

 Définissez hostspecific = « true » et effectuez un cast `this.Host` à <xref:System.IServiceProvider>.

 Cet exemple obtient l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, <xref:EnvDTE.DTE>, en tant que service:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Utilisation de hostSpecific avec l’héritage de modèle
 Spécifiez `hostspecific="trueFromBase"` si vous utilisez également le `inherits` attribut, et si vous héritez d’un modèle qui spécifie `hostspecific="true"`. Cela évite un avertissement du compilateur pour l’effet que la propriété `Host` a été déclarée deux fois.
