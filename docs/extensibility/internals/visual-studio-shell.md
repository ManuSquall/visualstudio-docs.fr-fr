---
title: Shell Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71b624cee0e55f95f90a86eac943828bbc26ac97
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144354"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interpréteur de commandes est l’agent principal d’intégration dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. L’interpréteur de commandes fournit les fonctionnalités nécessaires pour activer les VSPackages partager des services courants. Étant donné que l’objectif architectural de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consiste à vest fonctionnalité principale dans les VSPackages, l’interpréteur de commandes est une infrastructure pour fournir des fonctionnalités de base et prend en charge les communications entre ses composants VSPackages.  
  
## <a name="shell-responsibilities"></a>Responsabilités de l’interpréteur de commandes  
 L’interpréteur de commandes a les responsabilités clées suivantes :  
  
-   Prise en charge des éléments de l’interface utilisateur (IU) de base (par le biais des interfaces COM). Notamment, les menus par défaut et barres d’outils, les cadres de fenêtre de document ou fenêtres enfants de l’interface multidocument (MDI) et des cadres de fenêtre outil et prise en charge d’ancrage.  
  
-   Gestion d’une liste de tous les documents actuellement ouverts dans une table de documents en cours d’exécution (r & DT) afin de coordonner la persistance des documents et afin de garantir qu’un document ne peut pas être ouvert dans plusieurs façons, ou comme incompatibles.  
  
-   Prise en charge de l’interface de gestion de commande et de routage des commandes, `IOleCommandTarget`.  
  
-   Chargement des VSPackages au moment opportun. Délai de chargement d’un VSPackage est nécessaire à l’amélioration des performances de l’interpréteur de commandes.  
  
-   La gestion de certains des services partagés, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, qui fournit des fonctionnalités de l’interpréteur de commandes de base, et <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui fournit des fonctionnalités de base de fenêtrage.  
  
-   Gestion des fichiers solution (.sln). Les solutions contiennent des groupes de projets connexes, similaires aux fichiers de l’espace de travail (.dsw) dans Visual C++ 6.0.  
  
-   Sélection du suivi à l’échelle de l’interpréteur de commandes, contexte et des devises. L’interpréteur de commandes effectue le suivi des éléments suivants :  
  
    -   Le projet actuel  
  
    -   L’élément de projet en cours ou ItemID actuel <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   La sélection actuelle pour le **propriétés** fenêtre ou `SelectionContainer`  
  
    -   Le contexte de l’interface utilisateur, ID ou CmdUIGuids qui contrôlent la visibilité des commandes, des menus et barres d’outils  
  
    -   Les éléments actuellement actifs tels que la fenêtre active, le document et le Gestionnaire d’annulation  
  
    -   Les attributs du contexte de l’utilisateur qui pilotent aide dynamique  
  
 L’interpréteur de commandes transmet également la communication entre les VSPackages installés et des services en cours. Il prend en charge les fonctionnalités principales de l’interpréteur de commandes et les rend disponibles pour tous les packages VS intégrés dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ces fonctionnalités incluent les éléments suivants :  
  
-   **À propos** écran de démarrage et de la boîte de dialogue  
  
-   **Ajoutez de nouveau et ajouter un élément existant** boîtes de dialogue  
  
-   **Affichage de classes** fenêtre et **Explorateur d’objets**  
  
-   **Références** boîte de dialogue  
  
-   **Structure du document** fenêtre  
  
-   **Aide dynamique** fenêtre  
  
-   **Rechercher** et **remplacer**  
  
-   **Ouvrez le projet** et **ouvrir le fichier** boîtes de dialogue sur le **nouveau** menu  
  
-   **Options** boîte de dialogue sur le **outils** menu  
  
-   **Propriétés** fenêtre  
  
-   **Explorateur de solutions**  
  
-   **Liste des tâches** fenêtre  
  
-   **Boîte à outils**  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)