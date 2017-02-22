---
title: "Prend en charge plusieurs vues de Document | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), personnalisés - plusieurs vues du document"
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Prend en charge plusieurs vues de Document
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez fournir plusieurs vue d'un document en créant des objets de vue distincts de données et le fichier de document de votre éditeur.  Certains cas dans lesquels la vue supplémentaire de document est utile sont :  
  
-   prise en charge de nouvelle fenêtre : Vous souhaitez que votre éditeur pour fournir deux vues ou plus de la même type, afin qu'un utilisateur qui possède déjà une fenêtre ouverte dans l'éditeur puisse l'ouvrir une nouvelle fenêtre en activant la commande de **Nouvelle fenêtre** dans le menu de **Fenêtre** .  
  
-   prise en charge de formulaire et de mode Code : Vous souhaitez que votre éditeur pour fournir des vues de types différents.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], par exemple, fournit un mode formulaire et un mode Code.  
  
 Pour plus d'informations à ce sujet, consultez la procédure de CreateEditorInstance dans le fichier d'EditorFactory.cs dans le projet personnalisé d'éditeur créé par le modèle de package Visual Studio.  Pour plus d'informations sur ce projet, consultez [Procédure pas à pas : Création d'un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## synchroniser des vues  
 Lorsque vous implémentez plusieurs vues, l'objet de données du document est chargé de conserver toutes les vues synchronisées avec les données.  Vous pouvez utiliser les interfaces de gestion des événements sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> pour synchroniser plusieurs vues sur les données.  
  
 Si vous n'utilisez pas l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> pour synchroniser plusieurs vues, vous devez implémenter votre propre système d'événements pour gérer les modifications apportées à l'objet de données du document.  Vous pouvez utiliser différents niveaux de granularité pour contenir plusieurs vues à jour.  Avec un paramètre de granularité maximum, lorsque vous tapez une vue d'autres vues sont mises à jour immédiatement.  avec la granularité minimum, d'autres vues ne sont pas mises à jour jusqu'à ce qu'elles soient activées.  
  
## Déterminer si les données de document est déjà ouverte  
 Le tableau en cours de exécution de \(RDT\) document dans des \(IDE\) outils d'environnement de développement intégré suivent si les données d'un document est déjà ouverte, comme illustré dans le diagramme suivant.  
  
 ![Graphique DocDataView](../extensibility/media/docdataview.png "Docdataview")  
plusieurs vues  
  
 Par défaut, chaque vue \(objet de vue du document\) est contenue dans son propre frame de fenêtre \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>\).  Comme déjà indiqué, toutefois, les données du document peut être affiché dans plusieurs vues.  Pour cela, Visual Studio permet le transformateur rotatif pour déterminer si le document en question est déjà ouvert dans un éditeur.  Lorsque l'IDE appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> pour créer l'éditeur, une valeur non null retournée dans le paramètre d' `punkDocDataExisting` indique que le document est déjà ouvert dans un autre éditeur.  Pour plus d'informations sur la façon dont le transformateur rotatif fonctionne, consultez [Table de Document en cours d’exécution](../extensibility/internals/running-document-table.md).  
  
 Dans votre implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , examinez l'objet de données du document retourné dans `punkDocDataExisting` pour déterminer si les données de document est appropriée pour votre éditeur.  \(Par exemple, les données HTML doivent être affichées par un éditeur HTML.\) Si cela est approprié, votre fabrique d'éditeur doit fournir une deuxième vue pour les données.  Si le paramètre d' `punkDocDataExisting` n'est pas `NULL`, il est possible l'un ou l'autre que l'objet de données du document ne soit ouvert dans un autre éditeur, ou, plus probable, que les données du document ne soit déjà ouverte dans une vue différente avec mêmes l'éditeur.  Si les données du document s'ouvre dans un éditeur différent de votre fabrique d'éditeur ne prend pas en charge, Visual Studio n'ouvre pas votre fabrique d'éditeur.  Pour plus d'informations, consultez [Comment : joindre des vues de données de document](../extensibility/how-to-attach-views-to-document-data.md).