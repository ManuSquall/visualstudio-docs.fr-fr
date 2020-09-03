---
title: Création d’un package de Windows Installer | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710037"
---
# <a name="author-a-windows-installer-package"></a>Créer un package Windows Installer
Les données pilotent le modèle de Windows Installer. Plutôt que d’écrire un script procédural pour copier des fichiers et écrire des entrées de Registre, par exemple, vous créez des lignes et des colonnes dans des tables de base de données qui contiennent des données de fichier et de registre.

## <a name="database-entries"></a>Entrées de base de données
Pour installer un VSPackage, un package de Windows Installer doit contenir des entrées de base de données pour effectuer les tâches suivantes :

- Recherchez dans le système les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] votre package pris en charge (à l’aide de Windows Installer des tables qui incluent AppSearch, CompLocator, RegLocator, DrLocator et signature).

- Annulez l’installation si aucune version prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n’est installée ou si une autre exigence système du VSPackage n’est pas satisfaite (à l’aide de la table LaunchCondition).

- Installez le VSPackage et les fichiers dépendants (à l’aide des tables Directory, Component et file).

- Ajoutez les informations appropriées pour le VSPackage au registre (à l’aide de la table Registry).

- Intégrez le VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en appelant **devenv.exe/Setup** (à l’aide de la table CustomAction).

Pour plus d’informations, consultez [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Outils d’installation
Un large éventail d’outils d’installation tiers fournit un environnement de développement pour les packages Windows Installer. Les outils gratuits suivants sont disponibles :

- InstallShield Limited Edition

   Vous pouvez obtenir une version limitée d’InstallShield via la boîte **de dialogue Nouveau projet** de Visual Studio. Développez **autres types de projets** , puis sélectionnez **configuration et déploiement**. Sélectionnez le modèle InstallShield.

- Ensemble d’outils XML Windows Installer

   L’ensemble d’outils Windows Installer XML (WiX) génère des packages Windows Installer à partir de fichiers sources XML. L’ensemble d’outils WiX est un projet Microsoft Open source. Vous pouvez télécharger le code source et les exécutables à partir de l' [ensemble d’outils WiX](https://sourceforge.net/projects/wix/).

   Pour les produits commerciaux qui s’intègrent à à l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aide de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , consultez [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Voir aussi
- [Installer les VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
