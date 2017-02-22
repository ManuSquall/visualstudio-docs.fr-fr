---
title: "Donn&#233;es de documents et affichage de documents dans les &#233;diteurs personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), personnalisés - données de document et la vue de document"
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Donn&#233;es de documents et affichage de documents dans les &#233;diteurs personnalis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un éditeur personnalisé se compose de deux parties : un objet de données de document et un objet de vue de document. Comme leur nom le suggère, l'objet de données de document représente les données de texte à afficher et l'objet de vue de document \(ou « vue »\) représente une ou plusieurs fenêtres d'affichage de l'objet de données de document.  
  
## Objet de données de document  
 Un objet de données de document est une représentation sous forme de données de texte dans la mémoire tampon de texte. C'est un objet COM qui stocke le texte du document et autres informations, gère la persistance du document et permet à plusieurs vues de ses données. Pour plus d'informations, consultez  
  
 Voir <xref:EnvDTE80.Window2.DocumentData%2A> et [Fenêtres de document](../extensibility/internals/document-windows.md).  
  
 Éditeurs personnalisés et les concepteurs peuvent choisir d'utiliser le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet ou leur propre tampon personnalisé.<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> suit le modèle de l'incorporation simplifié pour un éditeur standard, prend en charge plusieurs vues et fournit des interfaces d'événements qui permettent de gérer plusieurs vues.  
  
## Objet de vue de document  
 Une fenêtre qui affiche le code et autres types de texte est appelée un document de vue ou vue. Lorsque vous créez un éditeur, vous pouvez choisir une vue unique, dans lequel le texte est affiché dans une fenêtre unique, ou un affichage de plusieurs, dans laquelle le texte est affiché dans plusieurs fenêtres. Votre choix dépend de votre application. Par exemple, si vous devez modifier côte à côte, vous choisiriez afficher plusieurs. Chaque vue est associée à une entrée dans l'environnement de développement intégré de \(IDE\) table document \(r & DT\) en cours d'exécution. Fenêtres d'affichage appartient à un projet ou un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet.  
  
 Si votre éditeur prend en charge plusieurs vues d'un objet de données de document, vos données de documents et les objets de vue de document doivent être distincts. Dans le cas contraire, ils peuvent être regroupés. Pour plus d'informations, consultez [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
 L'IDE notifie des vues sur les événements \(par exemple, lors de la fermeture d'une solution contenant un document\) en mettant en correspondance un identificateur d'élément \(ItemID\) pour chaque entrée dans la table de document en cours d'exécution. Pour plus d'informations, consultez [Table de Document en cours d’exécution](../extensibility/internals/running-document-table.md).  
  
 Il existe deux options pour créer un affichage pour un éditeur personnalisé. Un est le modèle d'activation en place, où la vue est hébergée dans une fenêtre à l'aide d'un contrôle ActiveX ou un objet de données de document. Le second est le modèle d'incorporation simplifié, où la vue est hébergée par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> est implémenté pour gérer les commandes de la fenêtre. Pour plus d'informations sur le modèle d'activation sur place, consultez [activation sur place](../misc/in-place-activation.md). Pour plus d'informations sur le modèle d'incorporation simplifié, consultez [Simplifié l'incorporation](../extensibility/simplified-embedding.md).  
  
## Voir aussi  
 [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md)   
 [Simplifié l'incorporation](../extensibility/simplified-embedding.md)   
 [Comment : joindre des vues de données de document](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gestion de détenteur de verrouillage de document](../extensibility/document-lock-holder-management.md)   
 [Vues uniques et multiples d'onglet](../extensibility/single-and-multi-tab-views.md)   
 [Enregistrement d'un Document Standard](../extensibility/internals/saving-a-standard-document.md)   
 [Persistance et la Table de Document en cours d'exécution](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Détermination de l'éditeur s'ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Fabriques d'éditeur](../extensibility/editor-factories.md)