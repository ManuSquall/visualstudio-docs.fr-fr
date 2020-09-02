---
title: Menus contextuels | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184263"
---
# <a name="context-menus"></a>Menus contextuels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les menus contextuels s’affichent lorsqu’un utilisateur clique avec le bouton droit dans une zone active de la zone cliente et s’efface lorsque le bouton droit de la souris est relâché.  
  
## <a name="editor-context-menus"></a>Menus contextuels de l'éditeur  
 En interceptant `ECMD_SHOWCONTEXTMENU` , votre service de langage peut contrôler les menus contextuels qui s’affichent dans l’éditeur. Pour afficher votre propre menu contextuel, gérez cette commande quand elle est passée à votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> . Si vous ne gérez pas cette commande, l’IDE affiche un menu contextuel standard fourni pour l’éditeur. Vous pouvez également contrôler le contenu du menu contextuel pour chaque marqueur. Pour plus d’informations à ce sujet, consultez [utilisation des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md) et [interception des commandes du service de langage hérité](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)
