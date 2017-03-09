---
title: "D&#233;termination de l’espace de noms par d&#233;faut d’un projet | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils personnalisés, calcul de l’espace de noms par défaut"
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# D&#233;termination de l’espace de noms par d&#233;faut d’un projet
Pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], si la propriété d' `CustomToolNamespace` est définie sur le fichier d'entrée, la valeur d' `CustomToolNamespace` devient la valeur du paramètre par défaut de l'espace de noms passé à la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> .  Sinon, le paramètre d' `wszDefaultNamespace` passé à `Generate` est toujours égale à l'espace de noms racine.  Pour plus d'informations sur les espaces de noms, consultez [Mots clés d'espaces de noms](/dotnet/csharp/language-reference/keywords/namespace-keywords).  
  
 les utilisations de[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dossier\-ont basé sur les espaces de noms.  Autrement dit, l'espace de noms inclut l'espace de noms racine, ainsi que des noms de tous les dossiers contenant l'outil personnalisé.  Chaque nom du dossier est converti en un identificateur valide, et les points séparent tous les noms.  Par exemple, si le fichier d'entrée est Dossiera \\FolderB\\FolderC\\MyInput.txt, and the root namespace is CL 9, puis l'espace de noms par défaut calculé assurez **CL9.FolderA.FolderB.FolderC**.  
  
 Une exception à cette règle se produit lorsque la chaîne de hiérarchie contient un dossier de référence Web.  Par exemple, si :  
  
-   FolderC s'agissait d'un dossier de référence Web, l'espace de noms serait **CL9.FolderC**.  
  
-   Dossierb s'agissait d'un dossier de référence Web, l'espace de noms serait **CL9.FolderB.FolderC**.  
  
 Autrement dit, l'espace de noms utilise le format suivant :  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## Voir aussi  
 [L'implémentation de générateurs de fichier unique](../extensibility/internals/implementing-single-file-generators.md)   
 [Enregistrement de générateurs de fichier unique](../extensibility/internals/registering-single-file-generators.md)   
 [Exposer des Types pour les concepteurs visuels](../extensibility/internals/exposing-types-to-visual-designers.md)