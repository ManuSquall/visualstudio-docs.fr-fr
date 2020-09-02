---
title: Commandes, menus et groupes définis par l’IDE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e8135328c11fd74311371d07645a525426371e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192729"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Commandes, menus et groupes définis par l’IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

De nombreux menus, commandes et groupes de commandes sont déjà définis pour être utilisés par l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Ces commandes sont également disponibles pour votre utilisation lorsque vous étendez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="finding-environment-defined-commands"></a>Recherche de commandes définies par l’environnement  
 Les commandes d’environnement sont définies dans un ensemble de quatre fichiers. vsct :  
  
- SharedCmdDef. vsct  
  
- SharedCmdPlace. vsct  
  
- ShellCmdDef. vsct  
  
- ShellCmdPlace. vsct  
  
  Ces fichiers se trouvent dans *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Ces fichiers fournissent les définitions et les GUID des menus et des groupes que vous pouvez utiliser dans le fichier de configuration de la table de commandes (. vsct) de votre VSPackage en tant que conteneurs pour vos propres menus, groupes et commandes.  
  
## <a name="in-this-section"></a>Dans cette section  
 [GUID et ID des menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Fournit les valeurs GUID et ID des menus dans la barre de menus de Visual Studio, ainsi que des groupes qu’ils contiennent.  
  
 [GUID et ID des barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Fournit les valeurs GUID et ID des barres d’outils dans l’IDE de Visual Studio et des groupes qu’ils contiennent.  
  
 [GUID et ID des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Fournit les valeurs GUID et ID des commandes définies par l’IDE de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Table de commandes Visual Studio (. Fichiers vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
