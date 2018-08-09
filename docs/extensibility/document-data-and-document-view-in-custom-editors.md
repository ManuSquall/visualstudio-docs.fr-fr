---
title: Afficher les données de document et de documents dans les éditeurs personnalisés | Microsoft Docs
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
ms.openlocfilehash: 2076f1a6c96aea717470fa1e955e5b9786f7fcc5
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639813"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Données de document et les vues de document dans les éditeurs personnalisés
Un éditeur personnalisé se compose de deux parties : un objet de données de document et un objet de vue de document. Comme leur nom le suggère, l’objet de données représente les données de texte à afficher. De même, l’objet de vue de document (ou « vue ») représente une ou plusieurs fenêtres d’affichage de l’objet de données de document.  
  
## <a name="document-data-object"></a>Objet de données de document  
 Un objet de données de document est une représentation sous forme de données de texte dans la mémoire tampon de texte. C’est un objet COM qui stocke le texte du document et autres informations. Également, l’objet de données gère la persistance de document et permet à plusieurs vues de ses données. Pour plus d'informations, consultez  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> et [Document Windows](../extensibility/internals/document-windows.md).  
  
 Concepteurs et éditeurs personnalisés peuvent choisir d’utiliser le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet ou leur propre mémoire tampon personnalisé. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> suit le modèle d’incorporation simplifié pour un éditeur standard, prend en charge plusieurs vues et fournit des interfaces d’événements qui permettent de gérer plusieurs vues.  
  
## <a name="document-view-object"></a>Objet de vue de document  
 Une fenêtre qui affiche le code et autres textes est connue comme un document ou un affichage. Lorsque vous créez un éditeur, vous pouvez choisir une seule vue, dans lequel le texte est affiché dans une fenêtre unique. Ou vous pouvez choisir une vue plusieurs, dans lequel le texte est affiché dans plusieurs fenêtres. Votre choix dépend de votre application. Par exemple, si vous avez besoin de modification côte à côte, vous choisiriez MultipleView. Chaque vue est associée à une entrée dans l’environnement de développement intégré de (IDE) en cours d’exécution (RDT) de table de document. Fenêtres d’affichage appartiennent à un projet ou un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet.  
  
 Si votre éditeur prend en charge plusieurs vues d’un objet de données de document, vos données de document et les objets de vue de document doivent être distincts. Sinon, ils peuvent être regroupés. Pour plus d’informations, consultez [prendre en charge plusieurs vues de document](../extensibility/supporting-multiple-document-views.md).  
  
 L’IDE signale des vues sur les événements (par exemple, lors de la fermeture d’une solution contenant un document) en mettant en correspondance un identificateur d’élément (ItemID) pour chaque entrée dans la table de document en cours d’exécution. Pour plus d’informations, consultez [table de documents en cours d’exécution](../extensibility/internals/running-document-table.md).  
  
 Il existe deux options pour la création d’une vue pour un éditeur personnalisé. Un est le modèle d’activation en place, où la vue est hébergée dans une fenêtre à l’aide d’un contrôle ActiveX ou un objet de données de document. Le second est le modèle d’incorporation simplifié, où la vue est hébergée par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> est implémentée pour prendre en charge les commandes de fenêtre. Pour plus d’informations sur le modèle d’activation sur place, consultez [In situ d’activation](../extensibility/in-place-activation.md). Pour plus d’informations sur le modèle d’incorporation simplifiée, consultez [incorporation simplifiée](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prendre en charge plusieurs vues de document](../extensibility/supporting-multiple-document-views.md)   
 [Incorporation simplifiée](../extensibility/simplified-embedding.md)   
 [Comment : joindre des vues de données de document](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gestion du détenteur de verrou document](../extensibility/document-lock-holder-management.md)   
 [Vues uniques et multiples d’onglet](../extensibility/single-and-multi-tab-views.md)   
 [Enregistrer un document standard](../extensibility/internals/saving-a-standard-document.md)   
 [Persistance et la table de document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Déterminer quel éditeur ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Fabriques d’éditeur](../extensibility/editor-factories.md)