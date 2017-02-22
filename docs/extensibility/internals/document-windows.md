---
title: "Fen&#234;tres de document | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK, les fenêtres de document"
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Fen&#234;tres de document
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans Visual Studio, un *fenêtre de document* est une fenêtre enfant encadré qui est associée à une fenêtre d’interface multidocument \(MDI\). Fenêtres de document sont généralement utilisés pour l’affichage et la modification de code source ou du texte, mais ils peuvent également héberger des autres types fonctionnelles. Fenêtres de document :  
  
-   Peuvent être organisés dans des groupes distincts onglet horizontal ou vertical dans le parent MDI afin que plusieurs fichiers peuvent être affichés en même temps.  
  
-   Peut être ancrée dans n’importe quel ordre dans le parent MDI.  
  
-   Peuvent flotter librement.  
  
-   Sont liées dans l’ordre de tabulation pour les autres fenêtres MDI.  
  
 Les commandes pour le regroupement, ancrées et flottantes sont accessibles dans le menu contextuel d’un onglet de fenêtre de document.  
  
 Pour plus d’informations sur le comportement de la fenêtre dans Visual Studio, consultez [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## Implémentation de fenêtres de document  
 Fenêtres de document sont créés en implémentant un éditeur. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface crée des fenêtres de document dans le cadre de l’instanciation d’un éditeur. Pour plus d'informations, consultez [Interfaces héritées dans l’éditeur](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Pour fournir en arrière et envoyer les points de navigation dans une fenêtre, vous devez implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interface. L’éditeur de texte utilise des marqueurs de texte pour identifier les points de navigation dans le document.  
  
## La Table de Document en cours d’exécution  
 L’IDE utilise la table de document en cours d’exécution \(r & DT\) pour suivre l’état de chaque fenêtre de document. La r & DT est le mécanisme dans le document windows sont avertis des événements, par exemple lors de la fermeture d’une solution ou un fichier a été modifié. Pour plus d'informations, consultez [Table de Document en cours d’exécution](../../extensibility/internals/running-document-table.md).  
  
## Voir aussi  
 [Document chargement différé](../../extensibility/internals/delayed-document-loading.md)