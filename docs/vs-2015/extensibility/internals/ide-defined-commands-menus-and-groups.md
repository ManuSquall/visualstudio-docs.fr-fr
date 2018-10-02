---
title: Commandes définies par l’IDE, les Menus et les groupes | Microsoft Docs
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
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6315c5ca1c7c0e9d26fcef142304668d2565d490
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507430"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Commandes, menus et groupes définis par l’IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDE-Defined commandes, Menus et les groupes](https://docs.microsoft.com/visualstudio/extensibility/internals/ide-defined-commands-menus-and-groups).  
  
Nombreux menus, les commandes et les groupes de commandes sont déjà définis pour une utilisation par le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Ces commandes sont également disponibles pour votre utilisation quand vous étendez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Recherche des commandes définies par l’environnement  
 Les commandes d’environnement sont définies dans un ensemble de quatre fichiers .vsct :  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Ces fichiers se trouvent dans  *\<chemin d’installation de Visual Studio SDK >* \VisualStudioIntegration\Common\Inc\\. Ces fichiers fournissent les définitions et les GUID des menus et des groupes que vous pouvez utiliser dans le fichier de configuration (.vsct) de table de commande de votre VSPackage en tant que conteneurs pour vos propres menus, les groupes et les commandes.  
  
## <a name="in-this-section"></a>Dans cette section  
 [GUID et ID des menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Donne les valeurs GUID et l’ID de menus dans la barre de menus de Visual Studio et des groupes qu’ils contiennent.  
  
 [GUID et ID des barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Donne les valeurs GUID et l’ID des barres d’outils dans l’IDE Visual Studio et des groupes qu’ils contiennent.  
  
 [GUID et ID des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Donne les valeurs GUID et ID de commandes définies par l’IDE Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio Command Table (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

