---
title: "Commandes définies par l’IDE, les Menus et les groupes | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 34e0e95475457e2a5f206ad4ecb0d7e42e2bb9ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ide-defined-commands-menus-and-groups"></a>Les groupes, les Menus et commandes définies par l’IDE
Nombreux menus, les commandes et les groupes de commandes sont déjà définis pour une utilisation par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Ces commandes sont également disponibles lorsque vous étendez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Commandes de recherche définis par l’environnement  
 Les commandes d’environnement sont définies dans un jeu de quatre fichiers .vsct :  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Ces fichiers se trouvent dans  *\<chemin d’installation de Visual Studio SDK >*\VisualStudioIntegration\Common\Inc\\. Ces fichiers fournissent les définitions et les GUID des menus et des groupes que vous pouvez utiliser dans le fichier de configuration (.vsct) de table de commande de votre VSPackage en tant que conteneurs pour vos propres menus, les groupes et les commandes.  
  
## <a name="in-this-section"></a>Dans cette section  
 [GUID et ID des menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Donne les valeurs GUID et l’ID des menus dans la barre de menus de Visual Studio et des groupes qu’ils contiennent.  
  
 [GUID et ID des barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Donne les valeurs GUID et l’ID de barres d’outils dans l’IDE de Visual Studio et des groupes qu’ils contiennent.  
  
 [GUID et ID des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Donne les valeurs GUID et l’ID de commandes définies par l’IDE Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Tableau de commandes de Visual Studio (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)