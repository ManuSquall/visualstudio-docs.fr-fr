---
title: Commandes définies par l’IDE, les Menus et les groupes | Microsoft Docs
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
ms.openlocfilehash: 5158a9d1a06ec6f08c67777e4f1ce2e4d37220e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315658"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Commandes, menus et groupes définis par l’IDE
Nombreux menus, les commandes et les groupes de commandes sont déjà définis pour une utilisation par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Ces commandes sont également disponibles pour votre utilisation quand vous étendez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Recherche des commandes définies par l’environnement
 Les commandes d’environnement sont définies dans un ensemble de quatre fichiers .vsct :

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Ces fichiers se trouvent dans  *\<chemin d’installation de Visual Studio SDK >* \VisualStudioIntegration\Common\Inc\\. Ces fichiers fournissent les définitions et les GUID des menus et des groupes que vous pouvez utiliser dans le fichier de configuration (.vsct) de table de commande de votre VSPackage en tant que conteneurs pour vos propres menus, les groupes et les commandes.

## <a name="in-this-section"></a>Dans cette section
- [GUID et ID des menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Donne les valeurs GUID et l’ID de menus dans la barre de menus de Visual Studio et des groupes qu’ils contiennent.

- [GUID et ID des barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Donne les valeurs GUID et l’ID des barres d’outils dans l’IDE Visual Studio et des groupes qu’ils contiennent.

- [GUID et ID des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Donne les valeurs GUID et ID de commandes définies par l’IDE Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)