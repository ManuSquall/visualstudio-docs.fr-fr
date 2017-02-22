---
title: "Simplifi&#233; l&#39;incorporation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs personnalisés de Visual Studio SDK, - simple permet d'afficher l'incorporation"
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Simplifi&#233; l&#39;incorporation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'incorporation simplifiée est activée dans un éditeur lorsque son objet de vue du document \(autrement dit, est lancé à un enfant de\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]qui est apparenté, et l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> est implémentée pour gérer ses commandes de fenêtre.  Simplifié incorporer des éditeurs ne peut pas héberger les contrôles activés.  Les objets utilisés pour créer un éditeur avec l'incorporation simplifiée sont présentés dans l'illustration suivante.  
  
 ![Graphique simplifié de l'éditeur d'incorporation](../extensibility/media/vssimplifiedembeddingeditor.png "vsSimplifiedEmbeddingEditor")  
éditeur avec l'incorporation simplifiée  
  
> [!NOTE]
>  Les objets dans cette illustration, seul l'objet d' `CYourEditorFactory` est requis pour créer un éditeur basé sur des fichiers standard.  Si vous créez un éditeur personnalisé, vous n'êtes pas tenus d'implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, car votre éditeur aura vraisemblablement son propre mécanisme privé de persistance.  Pour les éditeurs non personnalisés, toutefois, vous devez le faire.  
  
 toutes les interfaces implémentées pour créer un éditeur avec l'incorporation simplifiée sont contenues dans l'objet d' `CYourEditorDocument` .  Toutefois, pour prendre en charge plusieurs affichages des données du document, fractionner les interfaces sur les données distinctes et des objets de vue comme indiqué dans le tableau suivant.  
  
|Interface|emplacement d'interface|Utilisation|  
|---------------|-----------------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vue|Fournit la connexion à la fenêtre parente.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Vue|Gère les commandes.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Vue|Active les mises à jour de barre d'état.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Vue|Permet aux éléments de **boîte à outils** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Données|Envoie des notifications lorsque le fichier change.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Données|Active la enregistrer sous fonctionnalités d'un type de fichier.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Données|active la persistance pour le document.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Données|Autorise la suppression des événements de modification du fichier, tels que le déclenchement de rechargement.|