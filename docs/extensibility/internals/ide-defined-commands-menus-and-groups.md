---
title: Commandes, menus et groupes IDE-Defined | Microsoft Docs
description: En savoir plus sur les menus, les commandes et les groupes de commandes, qui sont définis dans l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6314199fdf850c377825ee31e58cd9f315c5f672
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761021"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Commandes, menus et groupes définis par l’IDE
De nombreux menus, commandes et groupes de commandes sont déjà définis pour être utilisés par l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Ces commandes sont également disponibles pour votre utilisation lorsque vous étendez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Recherche de Environment-Defined des commandes
 Les commandes d’environnement sont définies dans un ensemble de quatre fichiers. vsct :

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Ces fichiers se trouvent dans *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Ces fichiers fournissent les définitions et les GUID des menus et des groupes que vous pouvez utiliser dans le fichier de configuration de la table de commandes (. vsct) de votre VSPackage en tant que conteneurs pour vos propres menus, groupes et commandes.

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
