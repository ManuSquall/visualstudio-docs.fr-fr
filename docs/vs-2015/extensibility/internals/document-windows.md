---
title: Fenêtres de document | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e62be456422b7ee5e9f2828a44a6be05e1211d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839461"
---
# <a name="document-windows"></a>Fenêtres de document
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans Visual Studio, une *fenêtre de document* est une fenêtre enfant encadrée qui est associée à une fenêtre d’interface multidocument (MDI, multiple-document interface). Les fenêtres de document sont généralement utilisées pour l’affichage et la modification du code source ou du texte, mais elles peuvent également héberger d’autres types fonctionnels. Fenêtres de document :  
  
- Peut être organisé dans des groupes d’onglets horizontaux ou verticaux séparés dans le MDI parent afin que plusieurs fichiers puissent être affichés en même temps.  
  
- Peuvent être ancrées dans n’importe quel ordre dans l’MDI parent.  
  
- Peut être flottant librement.  
  
- Sont liés dans l’ordre de tabulation aux autres fenêtres MDI.  
  
  Les commandes de regroupement, d’ancrage et de flottement sont accessibles dans le menu contextuel d’un onglet de fenêtre de document.  
  
  Pour plus d’informations sur le comportement des fenêtres dans Visual Studio, consultez [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implémentation de la fenêtre de document  
 Les fenêtres de document sont créées en implémentant un éditeur. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface crée des fenêtres de document dans le cadre de l’instanciation d’un éditeur. Pour plus d’informations, consultez [interfaces héritées dans l’éditeur](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
> Pour fournir des points de navigation arrière et avant dans une fenêtre, implémentez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interface. L’éditeur de texte utilise des marqueurs de texte pour identifier les points de navigation dans le document.  
  
## <a name="the-running-document-table"></a>Table de document en cours d’exécution  
 L’IDE utilise la table de document en cours d’exécution (RDT) pour suivre l’état de chaque fenêtre de document. Le RDT est le mécanisme par lequel les fenêtres de document sont notifiées des événements, par exemple lorsqu’une solution est fermée ou lorsqu’un fichier a été modifié. Pour plus d’informations, consultez exécution de la [table des documents](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Chargement de document différé](../../extensibility/internals/delayed-document-loading.md)
