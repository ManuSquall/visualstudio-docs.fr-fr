---
title: Liste des objets de la fenêtre Propriétés | Microsoft Docs
description: En savoir plus sur les interfaces utilisées pour interagir avec la liste d’objets dans la Fenêtre Propriétés dans l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 908acf3f8ecad390266c3d085778dc13077a6fa8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903435"
---
# <a name="properties-window-object-list"></a>Liste d’objets de la fenêtre Propriétés
La liste d’objets de la fenêtre **Propriétés** est une liste déroulante qui vous permet de remplacer la sélection par d’autres objets disponibles dans une ou plusieurs fenêtres sélectionnées. La sélection d’un autre objet dans cette liste déclenche un appel à <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> pour informer l’environnement qu’un nouvel objet a été sélectionné. Les informations affichées dans la fenêtre **Propriétés** sont ensuite modifiées pour afficher les propriétés associées à l’objet nouvellement sélectionné.

## <a name="the-object-list"></a>Liste d’objets
 La liste d’objets est composée de deux champs : le nom de l’objet (affiché en gras) et le type d’objet.

 Le nom de l’objet affiché à gauche du type d’objet en gras est récupéré à partir de l’objet lui-même à l’aide de la `Name` propriété fournie par l' <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interface. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, la seule méthode sur <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , retourne <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> pour la coclasse de cette interface. La fenêtre **Propriétés** utilise <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> pour récupérer le nom de la coclasse, qui est affiché en tant que nom de l’objet dans la liste déroulante.

 Si l’objet n’a pas de `Name` propriété, aucun nom n’est affiché dans la zone nom de la liste d’objets. Vous pouvez ajouter une propriété nom à l’objet si vous souhaitez que le nom s’affiche dans la liste d’objets.

 Si l’objet COM n’implémente pas <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , la fenêtre **Propriétés** affiche le nom de l’interface à la place du nom de l’objet sur le côté gauche de la liste.

## <a name="see-also"></a>Voir aussi
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
