---
title: Document Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d669485eb13c8d9f089a54dcbfcf92fac710f474
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784583"
---
# <a name="document-windows"></a>Fenêtres de document
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans Visual Studio, un *fenêtre de document* est une fenêtre enfant encadré qui est associée à une fenêtre d’interface multidocument (MDI). Fenêtres de document sont généralement utilisés pour l’affichage et la modification de code source ou de texte, mais elles peuvent héberger également d’autres types fonctionnels. Fenêtres de document :  
  
- Peuvent être organisés dans des groupes distincts onglet horizontal ou vertical dans le parent MDI afin que plusieurs fichiers peuvent être affichées en même temps.  
  
- Peuvent être ancrées dans n’importe quel ordre dans le parent MDI.  
  
- Peut flotter librement.  
  
- Sont liées dans l’ordre de tabulation à d’autres fenêtres MDI.  
  
  Les commandes pour le regroupement, ancrer et rendre flottantes sont accessibles dans le menu contextuel d’un onglet de fenêtre de document.  
  
  Pour plus d’informations sur le comportement de la fenêtre dans Visual Studio, consultez [personnalisation des dispositions de fenêtre](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implémentation de fenêtres de document  
 Les fenêtres de document sont créées en implémentant un éditeur. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface crée des fenêtres de document dans le cadre de l’instanciation d’un éditeur. Pour plus d’informations, consultez [Interfaces hérité dans l’éditeur](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Pour fournir en arrière et transférer des points de navigation dans une fenêtre, vous devez implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interface. L’éditeur de texte utilise des marqueurs de texte pour identifier les points de navigation dans le document.  
  
## <a name="the-running-document-table"></a>La Table de Document en cours d’exécution  
 L’IDE utilise la table de document en cours d’exécution (RDT) pour suivre l’état de chaque fenêtre de document. La RDT est le mécanisme via quel document windows sont informés des événements, tels que lors de la fermeture d’une solution ou un fichier a été modifié. Pour plus d’informations, consultez [Table de Document en cours d’exécution](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Chargement de document différé](../../extensibility/internals/delayed-document-loading.md)

