---
title: "Prise en charge du contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "prise en charge de Visual Studio SDK, contrôle de la source"
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Prise en charge du contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge les extractions de fichiers, des enregistrements, et d'autres opérations de contrôle de code source pour votre projet ou éditeur.  Comme un client de contrôle de code source, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est conçu pour interagir avec un package de contrôle de code source, tel que [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], qui fournit l'archivage, contrôle de version, et fonctionnalités de contrôle d'un ensemble de fichiers défini dynamiquement.  
  
## Dans cette section  
 [Modèle pour les Packages de contrôle de code Source](../../extensibility/internals/model-for-source-control-packages.md)  
 Décrit les interfaces que type de projet doit implémenter pour prendre en charge le contrôle de code source.  
  
 [Décisions de conception](../../extensibility/internals/source-control-design-decisions.md)  
 Fournit des questions dont les réponses modifient la manière dont vous implémentez un type de projet.  
  
 [Détails de configuration](../../extensibility/internals/source-control-configuration-details.md)  
 Explique comment le contrôle de code source de prise en charge remplace l'implémentation d'un type de projet.  
  
 [Conseils supplémentaires pour les projets et les éditeurs](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Décrit les meilleures pratiques pour les types et les éditeurs de projet.  
  
 [Détails de l'exécution](../../extensibility/internals/source-control-runtime-details.md)  
 Décrit comment inscrire un projet lorsqu'un utilisateur l'ajoute à un système de contrôle de code source.  
  
## Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indique au package d'environnement ou de contrôle de code source qu'un fichier est sur le point d'être modifiée dans la mémoire ou d'être enregistré.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Permet des projets et des hiérarchies de s'inscrire dans le contrôle de code source et d'obtenir des informations sur l'état du contrôle de code source.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implémenté dans un système de projet pour fournir le contrôle de code source pour les fichiers projet et des éléments de projet.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Utilisé par les projets d'interroger l'environnement pour l'autorisation s'ajouter, de supprimer, ou renommer un fichier ou un répertoire dans une solution.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Informe les clients des modifications apportées aux fichiers projet ou répertoires.  
  
## Rubriques connexes  
 [Types de projet](../../extensibility/internals/project-types.md)  
 Fournit une vue d'ensemble des projets en tant que blocs de construction de base de l'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Les liens sont fournis aux autres rubriques qui expliquent comment génération de contrôle de projets et code à compiler.