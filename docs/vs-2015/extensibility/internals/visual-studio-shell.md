---
title: Shell Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ec79aab58e167ff2c935317897ba10a042a2e5a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065543"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell est l’agent principal d’intégration dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. L’interpréteur de commandes fournit les fonctionnalités nécessaires pour activer les VSPackages partager des services courants. Étant donné que l’objectif architectural de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] consiste à vest des fonctionnalités principales dans les VSPackages, l’interpréteur de commandes est une infrastructure pour fournir des fonctionnalités de base et prend en charge les communications entre son composant VSPackages.  
  
## <a name="shell-responsibilities"></a>Responsabilités de l’interpréteur de commandes  
 L’interpréteur de commandes a les responsabilités clées suivantes :  
  
- Prise en charge des éléments de base de l’interface utilisateur (IU) (par le biais des interfaces COM). Celles-ci incluent les menus par défaut et barres d’outils, frames de fenêtre de document ou fenêtres enfants de plusieurs documents MDI (interface) et les frames de fenêtre outil et prise en charge d’ancrage.  
  
- Gérer la liste en cours d’exécution de tous les documents actuellement ouverts dans une table de documents en cours d’exécution (RDT) afin de coordonner la persistance de documents et de garantir qu’un document ne peut pas être ouvert de façon plus d’une ou de manière incompatible.  
  
- Prise en charge de l’interface de routage des commandes et la gestion des commandes, `IOleCommandTarget`.  
  
- Chargement de VSPackages aux moments opportuns. Un VSPackage à chargement différé est nécessaire pour améliorer les performances de l’interpréteur de commandes.  
  
- La gestion de certains des services partagés, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, qui fournit une fonctionnalité d’interpréteur de commandes de base, et <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui fournit des fonctionnalités de base.  
  
- Gestion des fichiers solution (.sln). Solutions contiennent des groupes de projets connexes, similaires aux fichiers (.dsw) de l’espace de travail dans Visual C++ 6.0.  
  
- Sélection d’interpréteur de commandes à l’échelle du suivi, contexte et des devises. L’interpréteur de commandes effectue le suivi des éléments suivants :  
  
  - Le projet actuel  
  
  - L’élément de projet actuel ou ItemID actuel <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
  - La sélection actuelle pour le **propriétés** fenêtre ou `SelectionContainer`  
  
  - Le contexte de l’interface utilisateur, ID ou CmdUIGuids qui contrôlent la visibilité des commandes, menus et barres d’outils  
  
  - Les éléments actuellement actifs, tels que la fenêtre active, le document et le Gestionnaire d’annulation  
  
  - Les attributs de contexte de l’utilisateur qui pilotent l’aide dynamique  
  
  L’interpréteur de commandes transmet également la communication entre les VSPackages installés et les services en cours. Il prend en charge les fonctionnalités principales de l’interpréteur de commandes et les rend disponibles pour tous les packages VS intégrés dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ces fonctionnalités incluent les éléments suivants :  
  
- **Sur** écran de démarrage et de la boîte de dialogue  
  
- **Ajouter de nouveau et ajouter un élément existant** boîtes de dialogue  
  
- **Affichage de classes** fenêtre et **Explorateur d’objets**  
  
- **Références** boîte de dialogue  
  
- **Structure du document** fenêtre  
  
- **Aide dynamique** fenêtre  
  
- **Rechercher** et **remplacer**  
  
- **Ouvrez le projet** et **ouvrir un fichier** boîtes de dialogue sur le **New** menu  
  
- **Options** boîte de dialogue sur le **outils** menu  
  
- Fenêtre **Propriétés**  
  
- **Explorateur de solutions**  
  
- **Liste des tâches** fenêtre  
  
- **Boîte à outils**  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)
