---
title: Données du document et Document afficher dans les éditeurs personnalisés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb445ca70ac74cf2601e9f1035549bb686fca798
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Données du document et affichage de documents dans des éditeurs personnalisés
Un éditeur personnalisé se compose de deux parties : un objet de données de document et un objet de vue de document. Comme leur nom le suggère, l’objet de données de document représente les données de texte à afficher, et l’objet de vue de document (ou « vue ») représente une ou plusieurs fenêtres d’affichage de l’objet de données du document.  
  
## <a name="document-data-object"></a>Objet de données de document  
 Un objet de données de document est une représentation sous forme de données de texte dans la mémoire tampon de texte. Il s’agit d’un objet COM qui stocke le texte du document et autres informations, gère la persistance du document et permet à plusieurs vues de ses données. Pour plus d'informations, consultez  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> et [fenêtres de Document](../extensibility/internals/document-windows.md).  
  
 Concepteurs et éditeurs personnalisés peuvent choisir d’utiliser le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet ou leur propre tampon personnalisé. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> suit le modèle simplifié de l’incorporation d’un éditeur standard, prend en charge plusieurs vues et fournit des interfaces d’événements qui permettent de gérer plusieurs vues.  
  
## <a name="document-view-object"></a>Objet de vue de document  
 Une fenêtre qui affiche le code et tout autre texte est appelée un document de vue ou la vue. Lorsque vous créez un éditeur, vous pouvez choisir une seule vue, dans laquelle le texte est affiché dans une fenêtre unique, ou un affichage de plusieurs, dans laquelle le texte est affiché dans plusieurs fenêtres. Votre choix dépend de votre application. Par exemple, si vous avez besoin de modification de la côte à côte, vous choisiriez MultipleView. Chaque vue est associée à une entrée dans l’environnement de développement intégré de (IDE de) la table de documents (r & DT) en cours d’exécution. Vue windows appartient à un projet ou une <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet.  
  
 Si votre éditeur prend en charge plusieurs vues d’un objet de données de document, vos données de document et les objets de vue de document doivent être distinctes. Dans le cas contraire, ils peuvent être regroupés. Pour plus d’informations, consultez [prenant en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
 L’IDE signale des vues sur les événements (par exemple, lors de la fermeture d’une solution contenant un document) en mettant en correspondance un identificateur d’élément (ItemID) pour chaque entrée dans la table de document en cours d’exécution. Pour plus d’informations, consultez [Table de documents en cours d’exécution](../extensibility/internals/running-document-table.md).  
  
 Il existe deux options pour créer un affichage pour un éditeur personnalisé. Un est le modèle d’activation en place, où la vue est hébergée dans une fenêtre à l’aide d’un contrôle ActiveX ou un objet de données du document. Le deuxième est le modèle d’incorporation simplifié, où la vue est hébergée par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> est implémenté pour gérer les commandes de la fenêtre. Pour plus d’informations sur le modèle d’activation en place, consultez [Activation en Place](../extensibility/in-place-activation.md). Pour plus d’informations sur le modèle simplifié de l’incorporation, consultez [incorporation simplifié](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md)   
 [Simplifié incorporation](../extensibility/simplified-embedding.md)   
 [Comment : joindre des vues de données de document](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gestion du détenteur du verrouillage du document](../extensibility/document-lock-holder-management.md)   
 [Vues uniques et multiples d’onglet](../extensibility/single-and-multi-tab-views.md)   
 [Enregistrement d’un Document Standard](../extensibility/internals/saving-a-standard-document.md)   
 [Persistance et la Table de Document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Détermination pour ouvrir l’éditeur à un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Fabriques d’éditeur](../extensibility/editor-factories.md)