---
title: Commandes définies par l’IDE pour l’extension des systèmes de projet | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b00a83774185b4fe65ee2b7171e25492320b5bfb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503803"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Commandes définies par l’IDE pour l’extension des systèmes de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDE-Defined des commandes pour les systèmes de projet d’extension](https://docs.microsoft.com/visualstudio/extensibility/internals/ide-defined-commands-for-extending-project-systems).  
  
Lorsque vous souhaitez étendre les systèmes de projet, vous pouvez utiliser les commandes et commande de groupes fournis par le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Les sections suivantes répertorient les éléments de commande qui sont particulièrement utiles pour l’extension des systèmes de projet.  
  
## <a name="command-menus"></a>Menus contextuels  
 Le tableau suivant présente les menus de commande qui sont des emplacements utiles vous permettant de placer des commandes de haut niveau qui appellent un extendeur de projet.  
  
|Menu de commande|Description|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|Le **projet** menu de niveau supérieur.|  
|IDM_VS_TOOL_PROJWIN|Le **l’Explorateur de solutions** barre d’outils.|  
  
## <a name="shortcut-menus"></a>Menus contextuels  
 Le tableau suivant présente les menus contextuels qui s’appliquent lorsqu’un seul nœud est sélectionné dans le **l’Explorateur de solutions**, ou lorsqu’il y a plusieurs sélections homogènes dans le **l’Explorateur de solutions**, c'est-à-dire lorsque tous les nœuds sélectionnés sont du même type.  
  
|Menu contextuel|Description|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|S’applique lorsque le nœud de projet est sélectionné.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|S’applique lorsqu’un fichier est sélectionné.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|S’applique lorsqu’un dossier est sélectionné.|  
|IDM_VS_CTXT_WEBREFFOLDER|S’applique lorsque le dossier de référence Web est sélectionné.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|S’applique lorsque le nœud racine références appelé « Références » est sélectionné.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|S’applique lorsque les nœuds de référence sont sélectionnés ; celles-ci incluent assembly, COM et uniquement les références de projet. N’inclut pas les références Web.|  
  
 Le tableau suivant présente les menus contextuels qui s’appliquent lorsque la sélection dans le **l’Explorateur de solutions** s’étend sur plusieurs hiérarchies,  
  
|Menu contextuel|Description|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|S’applique lors de la sélection actuelle contient le nœud de la solution et les nœuds de projet racine.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|S’applique lors de la sélection actuelle contient les éléments de projet et le nœud de solution.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|S’applique lors de la sélection actuelle est composé de plusieurs nœuds de projet racine uniquement.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|S’applique lors de la sélection actuelle contient un mélange de nœuds de projet racine et les éléments de projet. En outre, la sélection peut contenir le nœud de la solution.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|S’applique lors de la sélection actuelle contient des éléments de projet à partir de plusieurs projets dans la solution, ou lorsque des éléments de types différents sont sélectionnés dans le même projet.|  
  
## <a name="command-groups"></a>Groupes de commandes  
 Le tableau suivant présente les groupes de commandes que vous pouvez utiliser lorsque vous étendez des projets, et que vous pouvez accéder via le <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu contextuel.  
  
|Groupe de commandes|Description|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Commandes de création, la reconstruction et le déploiement du projet.|  
|IDG_VS_CTXT_COMPILELINK|Commandes pour la compilation et liaison du projet.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Commandes que vous définissez la configuration de projet et l’ordre de génération.|  
|IDG_VS_CTXT_PROJECT_ADD|Commandes qui ajoutent des éléments au projet.|  
|IDG_VS_CTXT_PROJECT_START|Commandes qui définissent le projet de démarrage associé à la touche F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Commandes pour l’enregistrement des éléments de projet.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Commandes pour le débogage.|  
|IDG_VS_CTXT_PROJECT_SCC|Commandes pour le contrôle de code source.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Commandes pour les actions Couper, copier et coller.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Les commandes qui permettent d’accéder à la **propriétés du projet** boîte de dialogue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands et OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Création de groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md)

