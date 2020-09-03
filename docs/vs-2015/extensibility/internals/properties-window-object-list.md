---
title: Liste des objets de la fenêtre Propriétés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95ef509491e05daf575e211ae479c815994eb3d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148329"
---
# <a name="properties-window-object-list"></a>Liste d’objets de la fenêtre Propriétés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La liste d’objets de la fenêtre **Propriétés** est une liste déroulante qui vous permet de remplacer la sélection par d’autres objets disponibles dans une ou plusieurs fenêtres sélectionnées. La sélection d’un autre objet dans cette liste déclenche un appel à <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> pour informer l’environnement qu’un nouvel objet a été sélectionné. Les informations affichées dans la fenêtre **Propriétés** sont ensuite modifiées pour afficher les propriétés associées à l’objet nouvellement sélectionné.  
  
## <a name="the-object-list"></a>Liste d’objets  
 La liste d’objets est composée de deux champs : le nom de l’objet (affiché en gras) et le type d’objet.  
  
 Le nom de l’objet affiché à gauche du type d’objet en gras est récupéré à partir de l’objet lui-même à l’aide de la `Name` propriété fournie par l' <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interface. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, la seule méthode sur <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , retourne <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> pour la coclasse de cette interface. La fenêtre **Propriétés** utilise <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> pour récupérer le nom de la coclasse, qui est affiché en tant que nom de l’objet dans la liste déroulante.  
  
 Si l’objet n’a pas de `Name` propriété, aucun nom n’est affiché dans la zone nom de la liste d’objets. Vous pouvez ajouter une propriété nom à l’objet si vous souhaitez que le nom s’affiche dans la liste d’objets.  
  
 Si l’objet COM n’implémente pas <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , la fenêtre **Propriétés** affiche le nom de l’interface à la place du nom de l’objet sur le côté gauche de la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)
