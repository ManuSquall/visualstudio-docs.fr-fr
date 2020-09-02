---
title: Filtrage de la boîte de dialogue AddItem pour les projets imbriqués | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538094"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrage de la boîte de dialogue AddItem pour les projets imbriqués
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lorsque vous affichez une boîte de dialogue **AddItem** pour un projet imbriqué, le projet parent peut contrôler les éléments qui sont affichés dans la boîte de dialogue.  
  
 L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface vous permet de filtrer les nœuds qui se trouvent dans une boîte de dialogue **AddItem** . Lorsque le projet enfant affiche la boîte de dialogue **AddItem** , le parent peut implémenter l' `IVsFilterAddProjectItemDlg` interface et filtrer les éléments qui seraient autrement affichés dans le projet de l’enfant.  
  
 Lorsque les projets sont regroupés par fonction dans des projets parents spécifiques, vous pouvez implémenter `IVsFilterAddProjectItemDlg` lorsque l’utilisateur sélectionne **Ajouter un élément de projet** dans le menu contextuel d’un projet imbriqué. Implémenter `IvsFilterAddProjectItemDlg displays` uniquement les éléments de projet ou les fichiers spécifiques à ce groupe. Les éléments de projet des autres groupes sont filtrés à partir de la boîte de dialogue, même s’ils sont stockés dans le même répertoire.  
  
 Lorsqu’un utilisateur ouvre la boîte de dialogue **AddItem** pour l’enfant, l’implémentation de l’interface du projet parent `IVsFilterAddProjectItemDlg` est appelée.  
  
 L' `IVsFilterAddProjectItemDlg` interface peut également implémenter le filtrage par catégorie. Pour plus d’informations, consultez [Ajout d’éléments aux boîtes de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) et [inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Ajout d’éléments aux boîtes de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
