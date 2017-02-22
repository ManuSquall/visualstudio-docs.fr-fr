---
title: "Menus contextuels | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - menus contextuels"
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Menus contextuels
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les menus contextuels sont affichés lorsqu'un utilisateur clique avec le bouton droit dans zone active de la zone cliente et de l'espace libre lorsque le bouton droit de la souris est relâché.  
  
## menus contextuels d'éditeur  
 En interceptant `ECMD_SHOWCONTEXTMENU`, votre service de langage peut contrôler les menus contextuels qui s'afficheront dans l'éditeur.  Pour afficher votre propre menu contextuel, exécutez cette commande lorsqu'il est passé dans votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> par <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>appelant.  Si vous ne gérez pas cette commande, alors l'IDE affiche un menu contextuel standard fourni pour l'éditeur.  vous pouvez également contrôler le contenu du menu contextuel sur une base de par\-marque.  Pour plus d'informations à ce sujet, consultez [À l'aide de marqueurs de texte avec l'API héritée](../extensibility/using-text-markers-with-the-legacy-api.md) et [Interception des commandes de Service de langage hérité](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## Voir aussi  
 [Développement d'un Service de langage](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)