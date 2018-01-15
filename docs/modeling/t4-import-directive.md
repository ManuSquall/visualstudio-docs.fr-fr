---
title: T4 Import (directive) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f9d3abdc07b2fc937b08431df4d7d4e75800e700
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
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