---
title: Objet liste de la fenêtre Propriétés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6b7d238f7ce64122ac18a52dab59afb063ce47e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130134"
---
# <a name="properties-window-object-list"></a>Objet liste de la fenêtre Propriétés
La liste d’objets dans le **propriétés** fenêtre est une liste déroulante qui vous permet de modifier la sélection à d’autres objets disponibles au sein d’une ou plusieurs fenêtres sélectionnés. Sélection d’un autre objet à partir de cette liste déclenche un appel à <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> pour informer l’environnement qu’un objet a été sélectionné. Les informations affichées dans le **propriétés** fenêtre est ensuite modifiée pour afficher les propriétés associées à l’objet qui vient d’être sélectionné.  
  
## <a name="the-object-list"></a>La liste d’objets  
 La liste d’objets se compose de deux champs : le nom d’objet (affiché en gras) et le type d’objet.  
  
 Le nom de l’objet affiché à gauche du type d’objet en gras est récupéré à partir de l’objet lui-même à l’aide de la `Name` cette propriété est fournie par le <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interface. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, la seule méthode sur <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, retourne <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> pour (coclasse) de cette interface. Le **propriétés** fenêtre utilise <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> pour obtenir le nom de la coclasse, qui s’affiche comme le nom d’objet dans la liste déroulante.  
  
 Si l’objet n’a pas un `Name` un nom de propriété n’est pas affichée dans la zone Nom de la liste d’objets. Si vous souhaitez que le nom affiché dans la liste d’objets, vous pouvez ajouter une propriété de nom à l’objet.  
  
 Si l’objet COM n’implémente pas <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, le **propriétés** affiche le nom de l’interface à la place du nom de l’objet sur le côté gauche de la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)