---
title: Filtrage de la boîte de dialogue AddItem pour les projets imbriqués | Microsoft Docs
description: Découvrez comment filtrer la boîte de dialogue AddItem pour un projet imbriqué dans Visual Studio en implémentant l’interface IVsFilterAddProjectItemDlg du projet parent.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 668a1c3bae34caa2dc6a12def2bcee56765adbb1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886949"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrer la boîte de dialogue AddItem pour les projets imbriqués
Lorsque vous affichez une boîte de dialogue **AddItem** pour un projet imbriqué, le projet parent peut contrôler les éléments qui sont affichés dans la boîte de dialogue.

 L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface vous permet de filtrer les nœuds qui se trouvent dans une boîte de dialogue **AddItem** . Lorsque le projet enfant affiche la boîte de dialogue **AddItem** , le parent peut implémenter l' `IVsFilterAddProjectItemDlg` interface et filtrer les éléments qui seraient autrement affichés dans le projet de l’enfant.

 Lorsque les projets sont regroupés par fonction dans des projets parents spécifiques, vous pouvez implémenter `IVsFilterAddProjectItemDlg` lorsque l’utilisateur sélectionne **Ajouter un élément de projet** dans le menu contextuel d’un projet imbriqué. Implémenter `IvsFilterAddProjectItemDlg displays` uniquement les éléments de projet ou les fichiers spécifiques à ce groupe. Les éléments de projet des autres groupes sont filtrés à partir de la boîte de dialogue, même s’ils sont stockés dans le même répertoire.

 Lorsqu’un utilisateur ouvre la boîte de dialogue **AddItem** pour l’enfant, l’implémentation de l’interface du projet parent `IVsFilterAddProjectItemDlg` est appelée.

 L' `IVsFilterAddProjectItemDlg` interface peut également implémenter le filtrage par catégorie. Pour plus d’informations, consultez [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) et [inscrire des modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Inscrire des modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
