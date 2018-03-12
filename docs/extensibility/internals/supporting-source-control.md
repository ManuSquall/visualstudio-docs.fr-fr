---
title: "Prise en charge du contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f5dd2a98ec84b656dc70a00236775710266c54ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-source-control"></a>Prise en charge du contrôle de code Source
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge les extractions de fichiers, des archivages et autres opérations de contrôle de source de votre projet ou l’éditeur. Comme un client de contrôle de code source, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est conçu pour interagir avec un package de contrôle de code source, tel que [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], qui fournit l’archivage, le contrôle de version et des fonctionnalités de contrôle d’un ensemble de fichiers définis dynamiquement.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèle des packages de contrôle de code source](../../extensibility/internals/model-for-source-control-packages.md)  
 Décrit les interfaces d’un type de projet doit implémenter pour prendre en charge le contrôle de code source.  
  
 [Décisions de conception](../../extensibility/internals/source-control-design-decisions.md)  
 Fournit des questions dont les réponses modifier la façon dont vous implémentez un type de projet.  
  
 [Détails de configuration](../../extensibility/internals/source-control-configuration-details.md)  
 Décrit comment la prise en charge du contrôle de code source change l’implémentation d’un type de projet.  
  
 [Recommandations supplémentaires pour les projets et les éditeurs](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Décrit les meilleures pratiques pour les éditeurs et les types de projets.  
  
 [Détails de l’exécution](../../extensibility/internals/source-control-runtime-details.md)  
 Décrit comment enregistrer un projet quand un utilisateur ajoute à un système de contrôle de code source.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indique à l’environnement ou d’un package de contrôle de source un fichier est sur le point d’être modifiée dans la mémoire ou enregistré.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Permet de projets et des hiérarchies à inscrire avec le contrôle de code source et obtenir des informations sur l’état de contrôle de code source.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implémenté dans un système de projet pour fournir un contrôle de code source pour les fichiers projet et des éléments de projet.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Utilisé par les projets pour interroger l’environnement pour l’autorisation d’ajouter, supprimer ou renommer un fichier ou répertoire dans une solution.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifie les clients des modifications apportées aux fichiers de projet ou des répertoires.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit une vue d’ensemble des projets en tant que les blocs de construction de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Vous trouverez des liens vers d’autres rubriques qui expliquent comment projets de contrôle de génération et compilation du code.