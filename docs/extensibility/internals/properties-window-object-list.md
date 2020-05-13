---
title: Liste des objets de fenêtre des propriétés (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706148"
---
# <a name="properties-window-object-list"></a>Liste d’objets de la fenêtre Propriétés
La liste d’objets dans la fenêtre **Propriétés** est une liste d’abandon qui vous permet de modifier la sélection vers d’autres objets disponibles dans une ou plusieurs fenêtres sélectionnées. La sélection d’un objet différent de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> cette liste déclenche un appel pour informer l’environnement qu’un nouvel objet a été sélectionné. Les informations affichées dans la fenêtre **Propriétés** sont ensuite modifiées pour afficher les propriétés associées à l’objet nouvellement sélectionné.

## <a name="the-object-list"></a>La liste des objets
 La liste d’objets se compose de deux champs : le nom de l’objet (affiché en gras) et le type d’objet.

 Le nom de l’objet affiché à gauche du type d’objet en gras est récupéré de l’objet lui-même à l’aide de la `Name` propriété fournie par l’interface. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, la seule <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>méthode <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> sur , retourne pour la coclasse de cette interface. La fenêtre <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> **Propriétés** utilise pour obtenir le nom de la coclasse, qui est affiché comme le nom de l’objet dans la liste de dépôt.

 Si l’objet n’a pas de `Name` propriété, un nom n’est pas affiché dans la zone nom de la liste d’objets. Vous pouvez ajouter une propriété Nom à l’objet si vous voulez que le nom s’affiche dans la liste d’objets.

 Si l’objet COM <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>ne s’implémente pas, la fenêtre **Propriété** affiche le nom de l’interface à la place du nom de l’objet sur le côté gauche de la liste.

## <a name="see-also"></a>Voir aussi
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
