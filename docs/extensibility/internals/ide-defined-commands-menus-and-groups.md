---
title: Commandes, menus et groupes définis par l’IDE Microsoft Docs
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
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707715"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Commandes, menus et groupes définis par l’IDE
De nombreux menus, commandes et groupes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] commandement sont déjà définis pour être utilisés par l’IDE. Ces commandes sont également disponibles pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]votre utilisation lorsque vous prolongez .

## <a name="finding-environment-defined-commands"></a>Trouver des commandes définies par l’environnement
 Les commandes d’environnement sont définies dans un ensemble de quatre fichiers .vsct :

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Ces fichiers sont situés dans\\ * \<Visual Studio SDK chemin d’installation>*'VisualStudioIntegration’Common 'Inc . Ces fichiers fournissent les définitions et les GUID des menus et des groupes que vous pouvez utiliser dans le fichier de configuration de tableau de commande (.vsct) de votre VSPackage comme conteneurs pour vos propres menus, groupes et commandes.

## <a name="in-this-section"></a>Dans cette section
- [GUID et ID des menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Donne les valeurs GUID et ID des menus sur le menu Visual Studio bar, et des groupes qu’ils contiennent.

- [GUID et ID des barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Donne les valeurs GUID et ID des barres d’outils dans l’IDE Visual Studio, et des groupes qu’ils contiennent.

- [GUID et ID des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Donne les valeurs GUID et ID des commandes définies par l’IDE Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
