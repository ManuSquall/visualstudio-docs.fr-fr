---
title: "Fenêtres de document | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03e61b80aaf4c5c8b0e25f5b2a4a42f13d75d305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="document-windows"></a>Fenêtres de document
Dans Visual Studio, un *fenêtre de document* est une fenêtre enfant encadré qui est associée à une fenêtre de l’interface multidocument (MDI). Fenêtres de document sont généralement utilisés pour l’affichage et la modification de code source ou de texte, mais qu’ils peuvent également héberger des autres types fonctionnelles. Fenêtres de document :  
  
-   Peuvent être organisés dans les groupes d’onglets distincts de horizontal ou vertical dans le parent MDI afin que plusieurs fichiers peuvent être affichées en même temps.  
  
-   Peut être ancrée dans n’importe quel ordre dans le parent MDI.  
  
-   Peut flotter librement.  
  
-   Sont liées dans l’ordre de tabulation pour les autres fenêtres MDI.  
  
 Les commandes pour le regroupement, ancrer et rendre flottantes sont accessibles dans le menu contextuel d’un onglet de fenêtre de document.  
  
 Pour plus d’informations sur le comportement de la fenêtre dans Visual Studio, consultez [personnalisation des dispositions de fenêtre](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implémentation de fenêtre de document  
 Fenêtres de document sont créées en implémentant un éditeur. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface crée des fenêtres de document dans le cadre de l’instanciation d’un éditeur. Pour plus d’informations, consultez [hérité des Interfaces dans l’éditeur](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Pour fournir en arrière et transférer des points de navigation dans une fenêtre, vous devez implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interface. L’éditeur de texte utilise des marqueurs de texte pour identifier les points de navigation dans le document.  
  
## <a name="the-running-document-table"></a>La Table de Document en cours d’exécution  
 L’IDE utilise la table de document en cours d’exécution (r & DT) pour suivre l’état de chaque fenêtre de document. La r & DT est le mécanisme de notification via le document dans lequel windows des événements, tels que lors de la fermeture d’une solution ou un fichier a été modifié. Pour plus d’informations, consultez [Table de documents en cours d’exécution](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Chargement de document différé](../../extensibility/internals/delayed-document-loading.md)