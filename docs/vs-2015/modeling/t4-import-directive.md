---
title: T4 Import (directive) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 00033640ec7810f97785b38437795906500a7866
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953539"
---
# <a name="t4-import-directive"></a>Directive d'importation T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans les blocs de code d'un modèle de texte T4 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la directive `import` vous permet de faire référence aux éléments dans un autre espace de noms sans fournir de nom qualifié complet. Cela équivaut à `using` en C# ou à `imports` en [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
 Pour obtenir une vue d’ensemble de l’écriture de modèles de texte T4, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).  
  
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
  
- `System`  
  
  De plus, si vous utilisez une directive personnalisée, le processeur de directive peut importer automatiquement des espaces de noms.  
  
  Par exemple, si vous écrivez des modèles pour un langage spécifique à un domaine (DSL), vous n’avez pas besoin d’importer des directives pour les espaces de noms suivants :  
  
- `Microsoft.VisualStudio.Modeling`  
  
- Espace de noms de votre DSL  
  
## <a name="see-also"></a>Voir aussi  
 [Directive d’assembly T4](../modeling/t4-assembly-directive.md)
