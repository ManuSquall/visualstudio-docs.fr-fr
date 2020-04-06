---
title: Commandes définies par l’IDE pour l’extension des systèmes de projets (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707738"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Commandes définies par l’IDE pour l’extension des systèmes de projet
Lorsque vous souhaitez étendre les systèmes de projet, vous [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pouvez utiliser des commandes et des groupes de commandement fournis par l’IDE.

 Les sections suivantes énumèrent les éléments de commande qui sont particulièrement utiles pour l’extension des systèmes de projet.

## <a name="command-menus"></a>Menus de commande
 Le tableau suivant montre les menus de commande qui sont des emplacements utiles pour vous de mettre des commandes de haut niveau qui invoquent un prolongateur de projet.

|Menu de commande|Description|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Le menu de haut niveau **du Projet.**|
|IDM_VS_TOOL_PROJWIN|La barre d’outils **Solution Explorer.**|

## <a name="shortcut-menus"></a>Menus contextuels
 Le tableau suivant montre les menus raccourcis qui s’appliquent lorsqu’un seul nœud est sélectionné dans la **Solution Explorer**, ou lorsqu’il y a plusieurs sélections homogènes dans la **Solution Explorer**, qui est lorsque tous les nœuds sélectionnés sont du même type.

|Menu raccourci|Description|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|S’applique lorsque le nœud de projet est sélectionné.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|S’applique lorsqu’un fichier est sélectionné.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|S’applique lorsqu’un dossier est sélectionné.|
|IDM_VS_CTXT_WEBREFFOLDER|S’applique lorsque le dossier de référence Web est sélectionné.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|S’applique lorsque le nœud racine des références appelé "Références" est sélectionné.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|S’applique lorsque les nœuds de référence sont sélectionnés; il s’agit notamment de l’assemblage, COM, et les références de projet seulement. N’inclut pas les références Web.|

 Le tableau suivant affiche les menus raccourcis qui s’appliquent lorsque la sélection dans la **Solution Explorer** s’étend sur plusieurs hiérarchies,

|Menu raccourci|Description|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|S’applique lorsque la sélection actuelle contient le nœud de solution et les nœuds de projet root.|
|IDM_VS_CTXT_XPROJ_SLNITEM|S’applique lorsque la sélection actuelle contient le nœud de solution et les éléments du projet.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|S’applique lorsque la sélection actuelle se compose de nœuds de projet de racine multiple seulement.|
|IDM_VS_CTXT_XPROJ_PROJITEM|S’applique lorsque la sélection actuelle contient un mélange de nœuds de projets racinaires et d’éléments de projet. En outre, la sélection peut contenir le nœud de solution.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|S’applique lorsque la sélection actuelle contient des éléments de projet provenant de plusieurs projets dans la solution, ou lorsque des éléments de différents types sont sélectionnés dans le même projet.|

## <a name="command-groups"></a>Groupes de commandement
 Le tableau suivant montre les groupes de commande que vous pouvez utiliser <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> lorsque vous prolongez des projets, et que vous pouvez accéder par le menu raccourci.

|Groupe de commandement|Description|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Commandements pour la construction, la reconstruction et le déploiement du projet.|
|IDG_VS_CTXT_COMPILELINK|Commandes pour la compilation et l’établissement de liens entre le projet.|
|IDG_VS_CTXT_PROJECT_CONFIG|Commandes qui définitent la configuration du projet et construisent l’ordre.|
|IDG_VS_CTXT_PROJECT_ADD|Commandes qui ajoutent des éléments au projet.|
|IDG_VS_CTXT_PROJECT_START|Commandes qui fixent le projet de démarrage associé à la clé F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Commandes pour sauver les éléments du projet.|
|IDG_VS_CTXT_PROJECT_DEBUG|Commandes pour débogage.|
|IDG_VS_CTXT_PROJECT_SCC|Commandes pour le contrôle des sources.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Commandes pour les opérations de coupe, de copie et de pâte.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Commandes qui donnent accès à la boîte de dialogue **Project Properties.**|

## <a name="see-also"></a>Voir aussi

- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Création de groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md)
