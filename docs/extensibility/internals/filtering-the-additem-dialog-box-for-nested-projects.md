---
title: Filtrage de la boîte de dialogue AddItem pour les projets imbriqués (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708387"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrer la boîte de dialogue AddItem pour les projets imbriqués
Lorsque vous affichez une boîte de dialogue **AddItem** pour un projet imbriqué, le projet parent peut contrôler quels éléments sont affichés dans la boîte de dialogue.

 L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> vous permet de filtrer les nœuds qui seront dans une boîte de dialogue **AddItem.** Lorsque le projet pour enfants affiche la boîte de `IVsFilterAddProjectItemDlg` dialogue **AddItem,** le parent peut implémenter l’interface et filtrer les éléments qui seraient autrement affichés dans le projet de l’enfant.

 Lorsque les projets sont regroupés par fonction `IVsFilterAddProjectItemDlg` dans le cadre de projets parentaux spécifiques, vous pouvez implémenter lorsque l’utilisateur sélectionne **Ajouter l’élément du projet** sur le menu raccourci d’un projet imbriqué. Mise `IvsFilterAddProjectItemDlg displays` en œuvre uniquement d’éléments de projet ou de fichiers spécifiques à ce groupe. Les éléments du projet pour d’autres groupes sont filtrés hors de la boîte de dialogue, même s’ils sont stockés dans le même répertoire.

 Lorsqu’un utilisateur ouvre la boîte de dialogue **AddItem** pour l’enfant, la mise en œuvre de l’interface par le `IVsFilterAddProjectItemDlg` projet parent est appelée.

 L’interface `IVsFilterAddProjectItemDlg` peut également implémenter le filtrage par catégorie. Pour plus d’informations, voir [Ajouter des éléments à la boîte de dialogue Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) et enregistrer des modèles de projet et [d’élément](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Ajouter des éléments à la boîte de dialogue Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Enregistrer les modèles de projets et d’objets](../../extensibility/internals/registering-project-and-item-templates.md)
- [Projets nest](../../extensibility/internals/nesting-projects.md)
