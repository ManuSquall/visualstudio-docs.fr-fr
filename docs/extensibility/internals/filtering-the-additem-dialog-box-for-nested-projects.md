---
title: Filtrage de la boîte de dialogue AddItem pour les projets imbriqués | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8537cb9422639dcf815d7ebe46244e77729d114f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942592"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrer la boîte de dialogue AddItem pour les projets imbriqués
Lorsque vous affichez un **AddItem** boîte de dialogue pour un projet imbriqué, le projet parent peut contrôler quels éléments sont affichés dans la boîte de dialogue.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface vous permet de filtrer les nœuds qui seront dans un **AddItem** boîte de dialogue. Lorsque le projet enfant affiche le **AddItem** boîte de dialogue, le parent peut implémenter la `IVsFilterAddProjectItemDlg` interface et filtrer des éléments qui seraient affichées dans le projet de l’enfant.  
  
 Lorsque les projets sont regroupés par fonction, dans les projets parent spécifique, vous pouvez implémenter `IVsFilterAddProjectItemDlg` lorsque l’utilisateur sélectionne **ajouter un élément de projet** dans le menu contextuel dans un projet imbriqué. Implémentation `IvsFilterAddProjectItemDlg displays` projet uniquement les éléments ou les fichiers spécifique à ce groupe. Éléments de projet pour d’autres groupes sont exclus de la boîte de dialogue, même si elles sont stockées dans le même répertoire.  
  
 Lorsqu’un utilisateur ouvre le **AddItem** boîte de dialogue pour l’enfant, l’implémentation du projet parent de la `IVsFilterAddProjectItemDlg` interface est appelée.  
  
 Le `IVsFilterAddProjectItemDlg` interface peut également implémenter le filtrage par catégorie. Pour plus d’informations, consultez [ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) et [inscrire les modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Inscrire les modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Projets imbriqués](../../extensibility/internals/nesting-projects.md)