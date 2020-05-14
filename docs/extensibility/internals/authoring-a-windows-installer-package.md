---
title: Auteur d’un forfait Installateur Windows (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710037"
---
# <a name="author-a-windows-installer-package"></a>Auteur d’un package Windows Install
Les données sont le moteur du modèle d’installateur Windows. Plutôt que d’écrire un script procédural pour copier des fichiers et écrire des entrées de registre, par exemple, vous auteurez des rangées et des colonnes dans des tableaux de base de données qui contiennent des données de fichiers et de registre.

## <a name="database-entries"></a>Entrées de base de données
Pour installer un VSPackage, un package d’installateur Windows doit contenir des entrées de base de données pour effectuer les tâches suivantes :

- Recherchez le système pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] localiser les versions de vos supports VSPackage (à l’aide de tables d’installateur Windows qui incluent AppSearch, CompLocator, RegLocator, DrLocator et Signature).

- Annuler l’installation si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aucune version prise en charge n’est installée ou si une autre exigence du système de la VSPackage n’est pas remplie (à l’aide de la table LaunchCondition).

- Installez les fichiers VSPackage et dépendants (à l’aide de l’annuaire, du composant et des tables de fichiers).

- Ajoutez des informations appropriées pour le VSPackage au registre (à l’aide du tableau d’enregistrement).

- Intégrer le VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelant **devenv.exe/setup** (en utilisant la table CustomAction).

Pour plus d’informations, voir [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Outils d’installation
Une variété d’outils d’installation tiers fournissent un environnement de développement pour les paquets Windows Installer. Les outils gratuits suivants sont disponibles :

- InstallShield édition limitée

   Vous pouvez obtenir une version limitée de InstallShield grâce au dialogue Visual Studio **New Project.** Élargissez **d’autres types de projets,** puis sélectionnez **la configuration et le déploiement.** Sélectionnez le modèle InstallShield.

- Windows Installateur XML toolset

   Le ensemble d’outils Windows Installer XML (WiX) construit des paquets d’installateur Windows à partir de fichiers sources XML. Le games WiX est un projet open-source Microsoft. Vous pouvez télécharger le code source et exécutables à partir de [Wix toolset](https://sourceforge.net/projects/wix/).

   Pour les produits [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] commerciaux qui [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]s’intègrent en utilisant le , voir [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Voir aussi
- [Installer VSPackages Avec installateur Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
