---
title: "L’accès à Visual Studio ou autres hôtes à partir d’un modèle de texte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: "5"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: cc0f756637921b9f470e744ec8875ba3a2b54012
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Accès à Visual Studio ou à d'autres hôtes à partir d'un modèle de texte
Dans un modèle de texte, vous pouvez utiliser les méthodes et propriétés exposées par l’hôte qui exécute le modèle, telles que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Cela s’applique aux modèles de texte standard, les modèles de texte prétraités pas.  
  
## <a name="obtaining-access-to-the-host"></a>Obtention de l’accès à l’hôte  
 Définissez `hostspecific="true"` dans la `template` directive. Cela vous permet d’utiliser `this.Host`, qui a le type <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Ce type possède des membres que vous pouvez utiliser, par exemple, pour résoudre les noms de fichiers et de consigner les erreurs.  
  
### <a name="resolving-file-names"></a>Résolution des noms de fichiers  
 Pour rechercher le chemin d’accès complet d’un fichier relatif au modèle de texte, utilisez-le. Host.ResolvePath().  
  
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
 Cet exemple enregistre des messages lorsque vous transformez le modèle. Si l’hôte est [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ils sont ajoutés à la fenêtre d’erreur.  
  
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
 Si vous exécutez un modèle de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez utiliser `this.Host` pour accéder aux services fournis par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et des packages ou les extensions qui sont chargées.  
  
 Définissez hostspecific = « true » et effectuez un cast `this.Host` à <xref:System.IServiceProvider>.  
  
 Cet exemple obtient le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API, <xref:EnvDTE.DTE>, en tant que service :  
  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>À l’aide de hostSpecific avec héritage de modèle  
 Spécifiez `hostspecific="trueFromBase"` si vous utilisez également le `inherits` attribut, et si vous héritez d’un modèle qui spécifie `hostspecific="true"`. Cela permet d’éviter un avertissement du compilateur de l’effet que la propriété `Host` a été déclarée deux fois.