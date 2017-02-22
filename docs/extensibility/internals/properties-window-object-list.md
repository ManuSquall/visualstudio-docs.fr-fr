---
title: "Objet liste de la fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fenêtre Propriétés, liste d'objets"
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Objet liste de la fen&#234;tre Propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La liste d'objets dans la fenêtre de **Propriétés** est une liste déroulante qui vous permet de modifier la sélection à d'autres objets disponibles dans un ou plusieurs fenêtres sélectionnées.  Sélectionner un autre objet de cette liste déclenche un appel à l' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> pour informer l'environnement d'un nouvel objet a été sélectionné.  Les informations affichées dans la fenêtre de **Propriétés** sont ensuite modifiées pour afficher les propriétés associées à l'objet nouvellement sélectionné.  
  
## La liste d'objets  
 la liste d'objet se compose de deux champs : le nom de l'objet \(affiché en gras\) et le type d'objet.  
  
 Le nom de l'objet affiché à gauche du type d'objet en gras est extrait de l'objet lui\-même à l'aide de la propriété d' `Name` fournies par l'interface d' <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> .  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, la seule méthode sur <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, retourne <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> de la coclasse de cette interface.  La fenêtre de **Propriétés** utilise <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> pour obtenir le nom de la coclasse, qui s'affiche comme nom d'objet de la liste déroulante.  
  
 Si l'objet n'a pas de propriété d' `Name` , un nom n'est pas affiché dans la zone nom de la liste d'objets.  Vous pouvez ajouter une propriété Name à l'objet si vous souhaitez que le nom affiché dans la liste d'objets.  
  
 Si l'objet COM n'implémente pas <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, la fenêtre de **Propriétés** affiche le nom de l'interface à la place du nom d'objet sur le côté gauche de la liste.  
  
## Voir aussi  
 [Étendre les propriétés](../../extensibility/internals/extending-properties.md)