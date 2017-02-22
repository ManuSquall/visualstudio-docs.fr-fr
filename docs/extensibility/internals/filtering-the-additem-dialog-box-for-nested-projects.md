---
title: "Filtrage de la bo&#238;te de dialogue AddItem de projets imbriqu&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtrage, les projets imbriqués"
  - "projets imbriqués, boîte de dialogue AddItem zone de filtrage"
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Filtrage de la bo&#238;te de dialogue AddItem de projets imbriqu&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque vous affichez une boîte de dialogue d' **AddItem** pour un projet imbriqué, le projet parent peut contrôler les éléments sont affichés dans la boîte de dialogue.  
  
 L'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> vous permet de filtrer les nœuds qui sont dans une boîte de dialogue d' **AddItem** .  Lorsque le projet enfant affiche la boîte de dialogue d' **AddItem** , le parent peut implémenter l'interface de `IVsFilterAddProjectItemDlg` et filtrer les éléments devant être affichés dans le projet de l'enfant.  
  
 Lorsque les projets sont regroupés selon leur fonction sous projets parents spécifiques, vous pouvez implémenter `IVsFilterAddProjectItemDlg` lorsque l'utilisateur sélectionne **ajoutez l'élément de projet** dans le menu contextuel dans un projet imbriqué.  Implémentant des éléments de fichiers projet ou d' `IvsFilterAddProjectItemDlg displays` uniquement spécifiques à ce groupe.  Les éléments de projet pour d'autres groupes sont filtrés en dehors de la boîte de dialogue, même s'ils sont stockés dans le même répertoire.  
  
 Lorsqu'un utilisateur ouvre la boîte de dialogue d' **AddItem** pour l'enfant, l'implémentation de projet parent de l'interface d' `IVsFilterAddProjectItemDlg` est appelée.  
  
 l'interface d' `IVsFilterAddProjectItemDlg` peut également implémenter filtrer par catégorie.  Pour plus d'informations, consultez [Ajout d'éléments à l'ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) et [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Ajout d'éléments à l'ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Projets d'imbrication](../../extensibility/internals/nesting-projects.md)