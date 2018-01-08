---
title: T4 Import (directive) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 5d581e182b39ac5a786b2d66a1a3798ba7fe82ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="t4-import-directive"></a>Directive d'importation T4
Dans les blocs de code d'un modèle de texte T4 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la directive `import` vous permet de faire référence aux éléments dans un autre espace de noms sans fournir de nom qualifié complet. Cela équivaut à `using` en C# ou à `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Pour obtenir une vue d’ensemble de l’écriture de modèles de texte T4, consultez [l’écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-import-directive"></a>Utilisation de la directive d'importation  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 Dans cet exemple, le code du modèle peut omettre un espace de noms explicite pour les membres de System.IO :  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## <a name="standard-imports"></a>Importations standard  
 L'espace de noms suivant est importé automatiquement, afin que vous n'ayez pas besoin d'écrire une directive d'importation pour lui :  
  
-   `System`  
  
 De plus, si vous utilisez une directive personnalisée, le processeur de directive peut importer automatiquement des espaces de noms.  
  
 Par exemple, si vous écrivez des modèles pour un langage spécifique à un domaine (DSL), vous n’avez pas besoin d’importer des directives pour les espaces de noms suivants :  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Espace de noms de votre DSL  
  
## <a name="see-also"></a>Voir aussi  
 [Directive d’assembly T4](../modeling/t4-assembly-directive.md)