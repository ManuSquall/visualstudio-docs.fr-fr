---
title: Commandes, menus et groupes définis par l’IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af6d3e180e2b3d5eb2e0f6c85b7488761e160c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727293"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Commandes, menus et groupes définis par l’IDE
De nombreux menus, commandes et groupes de commandes sont déjà définis pour être utilisés par l’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ces commandes sont également disponibles pour votre utilisation lorsque vous étendez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Recherche de commandes définies par l’environnement
 Les commandes d’environnement sont définies dans un ensemble de quatre fichiers. vsct :

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Ces fichiers se trouvent dans *\<chemin d’installation du kit de développement logiciel Visual Studio >* \VisualStudioIntegration\Common\Inc\\. Ces fichiers fournissent les définitions et les GUID des menus et des groupes que vous pouvez utiliser dans le fichier de configuration de la table de commandes (. vsct) de votre VSPackage en tant que conteneurs pour vos propres menus, groupes et commandes.

## <a name="in-this-section"></a>Dans cette section
- [GUID et ID des menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Fournit les valeurs GUID et ID des menus dans la barre de menus de Visual Studio, ainsi que des groupes qu’ils contiennent.

- [GUID et ID des barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Fournit les valeurs GUID et ID des barres d’outils dans l’IDE de Visual Studio et des groupes qu’ils contiennent.

- [GUID et ID des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Fournit les valeurs GUID et ID des commandes définies par l’IDE de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)