---
title: Filtrage de la boîte de dialogue AddItem pour les projets imbriqués | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c007a2aa0895460f539acb50f49844f8ec158fa7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504734"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrage de la boîte de dialogue AddItem pour les projets imbriqués
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [filtrage de la boîte de dialogue AddItem pour les projets imbriqués](https://docs.microsoft.com/visualstudio/extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects).  
  
Lorsque vous affichez un **AddItem** boîte de dialogue pour un projet imbriqué, le projet parent peut contrôler quels éléments sont affichés dans la boîte de dialogue.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface vous permet de filtrer les nœuds qui seront dans un **AddItem** boîte de dialogue. Lorsque le projet enfant affiche le **AddItem** boîte de dialogue, le parent peut implémenter la `IVsFilterAddProjectItemDlg` interface et filtrer des éléments qui seraient affichées dans le projet de l’enfant.  
  
 Lorsque les projets sont regroupés par fonction, dans les projets parent spécifique, vous pouvez implémenter `IVsFilterAddProjectItemDlg` lorsque l’utilisateur sélectionne **ajouter un élément de projet** dans le menu contextuel dans un projet imbriqué. Implémentation `IvsFilterAddProjectItemDlg displays` projet uniquement les éléments ou les fichiers spécifique à ce groupe. Éléments de projet pour d’autres groupes sont exclus de la boîte de dialogue, même si elles sont stockées dans le même répertoire.  
  
 Lorsqu’un utilisateur ouvre le **AddItem** boîte de dialogue pour l’enfant, l’implémentation du projet parent de la `IVsFilterAddProjectItemDlg` interface est appelée.  
  
 Le `IVsFilterAddProjectItemDlg` interface peut également implémenter le filtrage par catégorie. Pour plus d’informations, consultez [Ajout d’éléments pour les boîtes de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) et [l’inscription de Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Ajout d’éléments à l’ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
