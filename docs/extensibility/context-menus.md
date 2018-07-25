---
title: Menus contextuels | Microsoft Docs
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
ms.openlocfilehash: afd67578bee63408b50e402fb0bd8b29be3fc6eb
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232531"
---
# <a name="context-menus"></a>Menus contextuels
Menus contextuels sont affichent quand un utilisateur clique sur une région active de la zone cliente et désactivez lorsque le bouton droit de la souris est relâché.  
  
## <a name="editor-context-menus"></a>Menus contextuels de l’éditeur  
 En interceptant `ECMD_SHOWCONTEXTMENU`, votre service de langage peut contrôler les menus contextuels qui seront affiche dans l’éditeur. Pour afficher votre propre menu contextuel, gérer cette commande lorsqu’elle est passée dans votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Si vous ne gérez pas cette commande, l’IDE affiche un menu de contexte standard fourni pour l’éditeur. Vous pouvez également contrôler le contenu du menu contextuel sur une base par marqueur. Pour plus d’informations, consultez [utiliser des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md) et [intercepter des commandes de service de langage hérité](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Étendre des menus et commandes](../extensibility/extending-menus-and-commands.md)