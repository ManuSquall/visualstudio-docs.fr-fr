---
title: Menus contextuels | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69048a35514ac35556e04ed5266ff58b21b31e0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="context-menus"></a>Menus contextuels
Menus contextuels sont affichent lorsqu’un utilisateur clique sur une région active de la zone cliente et désactivez lorsque le bouton droit de la souris est relâché.  
  
## <a name="editor-context-menus"></a>Menus contextuels de l'éditeur  
 En interceptant `ECMD_SHOWCONTEXTMENU`, votre service de langage peut contrôler les menus contextuels qui seront affichent dans l’éditeur. Pour afficher votre propre menu contextuel, gérer cette commande lorsqu’elle est passée dans votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Si vous ne gérez pas cette commande, l’IDE affiche un menu de contexte standard fourni pour l’éditeur. Vous pouvez également contrôler le contenu du menu contextuel sur une base par marqueur. Pour plus d’informations, consultez [à l’aide des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md) et [interception des commandes du Service de langage hérité](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)