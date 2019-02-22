---
title: Liste d’objets de fenêtre de propriétés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eccc7cfc432918a80723251a7b9a87ec4e13450d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619769"
---
# <a name="properties-window-object-list"></a>Liste d’objets de la fenêtre Propriétés
La liste d’objets dans le **propriétés** fenêtre est une liste déroulante qui vous permet de modifier la sélection à d’autres objets disponibles au sein d’une ou plusieurs fenêtres sélectionnés. Sélection d’un objet différent dans cette liste déclenche un appel à <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> pour informer l’environnement qu’un nouvel objet a été sélectionné. Les informations affichées dans le **propriétés** fenêtre est ensuite modifiée pour afficher les propriétés associées à l’objet qui vient d’être sélectionné.

## <a name="the-object-list"></a>La liste d’objets
 La liste d’objets se compose de deux champs : le nom d’objet (affiché en gras) et le type d’objet.

 Le nom de l’objet affiché à gauche du type d’objet en gras est récupéré à partir de l’objet lui-même à l’aide de la `Name` propriété fournie par le <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interface. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, la seule méthode sur <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, retourne <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> pour coclasse de cette interface. Le **propriétés** fenêtre utilise <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> pour obtenir le nom de la coclasse, qui s’affiche en tant que le nom d’objet dans la liste déroulante.

 Si l’objet n’a pas un `Name` propriété, un nom n’est pas affichée dans la zone Nom de la liste d’objets. Si vous souhaitez que le nom affiché dans la liste d’objets, vous pouvez ajouter une propriété de nom à l’objet.

 Si l’objet COM n’implémente pas <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, le **propriétés** fenêtre affiche le nom de l’interface à la place le nom de l’objet sur le côté gauche de la liste.

## <a name="see-also"></a>Voir aussi
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)