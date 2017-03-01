---
title: "Les commandes définies par l’IDE pour l’extension des systèmes de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8ef8f9d3bd75057708f7e1d380da83a38d7efb4b
ms.lasthandoff: 02/22/2017

---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Commandes définies par l’IDE pour l’extension des systèmes de projet
Lorsque vous souhaitez étendre les systèmes de projet, vous pouvez utiliser les commandes et commande groupes fournis par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Les sections suivantes répertorient les éléments de commande qui sont particulièrement utiles pour l’extension des systèmes de projet.  
  
## <a name="command-menus"></a>Menus contextuels  
 Le tableau suivant présente les menus contextuels qui sont des emplacements utiles placer les commandes de haut niveau qui appellent une extension de projet.  
  
|Menu de commande|Description|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|Le **projet** menu de niveau supérieur.|  
|IDM_VS_TOOL_PROJWIN|Le **l’Explorateur de solutions** barre d’outils.|  
  
## <a name="shortcut-menus"></a>Menus contextuels  
 Le tableau suivant présente les menus contextuels qui s’appliquent lorsqu’un seul nœud est sélectionné dans le **l’Explorateur de solutions**, ou lorsqu’il existe plusieurs sélections homogènes dans le **l’Explorateur de solutions**, lorsque tous les nœuds sélectionnés sont du même type.  
  
|Menu contextuel|Description|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|S’applique lorsque le nœud de projet est sélectionné.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|S’applique lorsqu’un fichier est sélectionné.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|S’applique lorsqu’un dossier est sélectionné.|  
|IDM_VS_CTXT_WEBREFFOLDER|S’applique lorsque le dossier de référence Web est sélectionné.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|S’applique lorsque les références du nœud racine appelé « Références ».|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|S’applique lorsque les nœuds de référence sont sélectionnés ; notamment, assembly, COM et uniquement les références de projet. N’inclut pas les références Web.|  
  
 Le tableau suivant présente les menus contextuels qui s’appliquent lorsque la sélection dans le **l’Explorateur de solutions** s’étend sur plusieurs hiérarchies,  
  
|Menu contextuel|Description|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|S’applique lors de la sélection actuelle contient le nœud de la solution et les nœuds de projet racine.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|S’applique lors de la sélection actuelle contient les éléments de projet et le nœud de la solution.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|S’applique lors de la sélection en cours se compose de plusieurs nœuds de projet racine uniquement.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|S’applique lors de la sélection actuelle contient un mélange de nœuds de projet racine et des éléments de projet. En outre, la sélection peut contenir le nœud de la solution.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|S’applique lors de la sélection actuelle contient des éléments de projet à partir de plusieurs projets dans la solution, ou lorsque les éléments de types différents sont sélectionnés dans le même projet.|  
  
## <a name="command-groups"></a>Groupes de commandes  
 Le tableau suivant répertorie les groupes de commandes que vous pouvez utiliser lorsque vous étendez des projets et que vous pouvez accéder via le <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>menu contextuel.</xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>  
  
|Groupe de commandes|Description|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Commandes pour la création, la reconstruction et le déploiement du projet.|  
|IDG_VS_CTXT_COMPILELINK|Commandes de compilation et de liaison du projet.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Commandes pour définir la configuration de projet et l’ordre de génération.|  
|IDG_VS_CTXT_PROJECT_ADD|Commandes pour ajouter des éléments au projet.|  
|IDG_VS_CTXT_PROJECT_START|Commandes qui définissent le projet de démarrage associé à la touche F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Commandes pour l’enregistrement des éléments de projet.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Commandes de débogage.|  
|IDG_VS_CTXT_PROJECT_SCC|Commandes de contrôle de code source.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Commandes pour couper, copier et coller.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Les commandes qui permettent d’accéder à la **propriétés du projet** boîte de dialogue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ajouter des éléments d’Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands et OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Création de groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md)
