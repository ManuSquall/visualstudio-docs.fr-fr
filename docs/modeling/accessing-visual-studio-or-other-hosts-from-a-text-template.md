---
title: "Accessing Visual Studio or other Hosts from a Text Template | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 5
---
# Accessing Visual Studio or other Hosts from a Text Template
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans un modèle de texte, vous pouvez utiliser les méthodes et propriétés exposées par l'hôte qui exécute le modèle, comme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Cela s'applique aux modèles de texte normaux, non prétraités.  
  
## Obtention de l'accès à l'hôte  
 Définissez `hostspecific="true"` dans la directive `template`.  Cela vous permet d'utiliser `this.Host`, qui a pour type <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.  Ce type possède des membres que vous pouvez utiliser, par exemple, pour résoudre des noms de fichiers et enregistrer les erreurs.  
  
### Résolution de noms de fichiers  
 Pour trouver le chemin complet d'un fichier par rapport au modèle de texte, utilisez this.Host.ResolvePath\(\).  
  
```c#  
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
  
### Affichage de messages d'erreur  
 Cet exemple enregistre les messages lorsque vous transformez le modèle.  Si l'hôte est [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ils sont ajoutés à la fenêtre d'erreur.  
  
```c#  
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
  
## Utilisation de l'API Visual Studio  
 Si vous exécutez un modèle de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez utiliser `this.Host` pour accéder aux services fournis par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et tous packages ou extensions chargés.  
  
 Définissez hostspecific\="true" et effectuez le cast de `this.Host` en <xref:System.IServiceProvider>.  
  
 Cet exemple obtient l'API [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:EnvDTE.DTE>, comme un service :  
  
```c#  
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
  
## L'utilisation de hostSpecific avec l'héritage du modèle  
 Spécifiez `hostspecific="trueFromBase"` si vous utilisez également la `inherits` attribut, et si vous héritez d'un modèle qui spécifie le `hostspecific="true"`.  Cela permet d'éviter un avertissement du compilateur à l'effet que la propriété `Host` a été déclarée deux fois.