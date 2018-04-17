---
title: Menus contextuels | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa957e949127663eca7d4e619919edcc07c7a29b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="context-menus"></a>Menus contextuels
Menus contextuels sont affichent lorsqu’un utilisateur clique sur une région active de la zone cliente et désactivez lorsque le bouton droit de la souris est relâché.  
  
## <a name="editor-context-menus"></a>Menus contextuels de l'éditeur  
 En interceptant `ECMD_SHOWCONTEXTMENU`, votre service de langage peut contrôler les menus contextuels qui seront affichent dans l’éditeur. Pour afficher votre propre menu contextuel, gérer cette commande lorsqu’elle est passée dans votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Si vous ne gérez pas cette commande, l’IDE affiche un menu de contexte standard fourni pour l’éditeur. Vous pouvez également contrôler le contenu du menu contextuel sur une base par marqueur. Pour plus d’informations, consultez [à l’aide des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md) et [interception des commandes du Service de langage hérité](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)