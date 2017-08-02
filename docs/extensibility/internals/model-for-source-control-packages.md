---
title: "Mod&#232;le pour les Packages de contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèle de Visual Studio SDK, de contrôle de source"
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Mod&#232;le pour les Packages de contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le modèle suivant représente un exemple d'implémentation de contrôle de code source.  Dans le modèle, les interfaces que vous devez implémenter et les services d'environnement que vous devez appeler.  Comme tous les services, vous appelez réellement les méthodes d'interface particulière que vous obtenez via le service.  Les noms de classes sont identifiés pour visualiser plus facilement comment le contrôle de code source est exécuté.  
  
 ![Exemples SCC&#95;TUP](~/extensibility/internals/media/scc_tup.gif "SCC\_TUP")  
Projet de contrôle de l'exemple de code source  
  
## Interfaces  
 Vous pouvez implémenter le contrôle de code source pour votre nouveau projet dans Visual Studio à l'aide de la liste d'interfaces répertoriées dans le tableau suivant.  
  
|Interface|Utilisation|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Appelé par les projets et les éditeurs avant d'enregistrer ou modifient des fichiers \(modifiés\).  Cette interface est accessible à l'aide de le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Appelé par les projets de demander l'autorisation sur ajouter, supprimer, ou renommer un fichier ou un répertoire.  Cette interface est également appelée par les projets d'informer l'environnement lorsqu'un approuvé ajouter, de supprimer, ou renomme l'action est terminé.  Elle est accessible à l'aide de le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implémentée par toute entité qui s'inscrit pour être annoncée lorsque les projets ajout, renommer, ou supprimer un fichier ou un répertoire.  De s'enregistrer pour la notification d'événements, appelez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Appelé par les projets de s'inscrire au package de contrôle de code source et d'obtenir des informations sur l'état du contrôle de code source.  Cette interface est accessible à l'aide de le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implémentée par le projet pour répondre aux demandes des informations de contrôle de code source sur les fichiers et d'obtenir les paramètres de contrôle de code source requis pour le fichier projet.|  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Prise en charge du contrôle de code Source](../../extensibility/internals/supporting-source-control.md)