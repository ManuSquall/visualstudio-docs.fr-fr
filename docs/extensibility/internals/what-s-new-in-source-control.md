---
title: "Nouveaut&#233;s du contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nouveau contrôle de code source Visual Studio SDK, nouveautés"
  - "contrôle de code source (Visual Studio SDK), nouveautés"
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Nouveaut&#233;s du contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

dans [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] vous pouvez fournir une solution profondément intégrée de contrôle de code source en implémentant un contrôle de code source VSPackage.  Cette section décrit les fonctionnalités du contrôle de code source VSPackages et fournit une vue d'ensemble des étapes d'implémentation.  
  
## Le contrôle de code source VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux types de solutions de contrôle de code source.  Dans toutes les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez toujours intégrer un plug\-in API\-basé par plug\-in contrôle de code source.  Vous pouvez également créer un VSPackage pour le contrôle de code source qui fournit une profond\-intégration, chemin d' [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] approprié pour les solutions de contrôle de code source qui requièrent un niveau élevé de la sophistication et de l'autonomie.  
  
 Un VSPackage peut ajouter quasiment tout type de fonctionnalités à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Un contrôle de code source VSPackage fournit une fonctionnalité achevée de contrôle de code source pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], de l'interface utilisateur présenté à l'utilisateur à la principale communication avec le système de contrôle de code source.  
  
 Implémentation d'un contrôle de code source VSPackage ne requiert un « tout ou rien » stratégie.  Le créateur d'un contrôle de code source VSPackage doit valider une tâche difficile en implémentant un nombre quelconque d'interfaces de contrôle de code source et de nouveaux éléments d'interface utilisateur \(boîtes de dialogue, menus, et barres d'outils\) pour couvrir l'intégralité de la fonctionnalité de contrôle de code source, ainsi qu'interfaces requises de tout package pour intégrer avec succès avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Les étapes suivantes fournissent une vue d'ensemble de ce qui est nécessaire pour implémenter un package de contrôle de code source.  Pour plus d'informations, consultez [Création d'un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  créez un VSPackage qui offre un service de contrôle de code source privé.  
  
2.  Implémentez les interfaces des services contrôle\-mis en relation par source proposés par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(par exemple, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> et l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> \).  
  
3.  enregistrez votre contrôle de code source VSPackage.  
  
4.  Implémentez tout le contrôle de code source interface utilisateur, notamment les éléments de menu, des boîtes de dialogue, des barres d'outils, et des menus contextuels.  
  
5.  Tous les événements contrôle\-mis en relation par source sont passés à votre contrôle de code source VSackage lorsqu'il est actif et doit être géré par le VSPackage.  
  
6.  Votre contrôle de code source VSPackage doit écouter des événements tels que ceux qui implémentent l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> ainsi que des événements de document de \(TPD\) projet de suivre \(comme implémenté par l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> \) et prendre les mesures nécessaires.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Vue d'ensemble](../../extensibility/internals/source-control-integration-overview.md)   
 [Création d'un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md)