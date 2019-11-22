---
title: Création d’un package de Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301136"
---
# <a name="authoring-a-windows-installer-package"></a>Création d’un package Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les données pilotent le modèle de Windows Installer. Plutôt que d’écrire un script procédural pour copier des fichiers et écrire des entrées de Registre, par exemple, vous créez des lignes et des colonnes dans des tables de base de données qui contiennent des données de fichier et de registre.  
  
## <a name="database-entries"></a>Entrées de la base de données  
 Pour installer un VSPackage, un package de Windows Installer doit contenir des entrées de base de données pour effectuer les tâches suivantes :  
  
- Recherchez dans le système les versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que votre VSPackage prend en charge (à l’aide de Windows Installer des tables qui incluent AppSearch, CompLocator, RegLocator, DrLocator et signature).  
  
- Annulez l’installation si aucune version prise en charge de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] n’est installée ou si une autre exigence système du VSPackage n’est pas satisfaite (à l’aide de la table LaunchCondition).  
  
- Installez le VSPackage et les fichiers dépendants (à l’aide des tables Directory, Component et file).  
  
- Ajoutez les informations appropriées pour le VSPackage au registre (à l’aide de la table Registry).  
  
- Intégrez le VSPackage dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en appelant **devenv. exe/setup** (à l’aide de la table CustomAction).  
  
  Pour plus d’informations, consultez [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Outils d’installation  
 Un large éventail d’outils d’installation tiers fournit un environnement de développement pour les packages Windows Installer. Deux outils gratuits sont les suivants :  
  
- Installshield Limited Edition  
  
   Vous pouvez obtenir une version limitée d’InstallShield via la boîte **de dialogue Nouveau projet** de Visual Studio. Développez **autres types de projets** , puis sélectionnez **configuration et déploiement**. Sélectionnez le modèle InstallShield.  
  
- ensemble d'outils XML de Windows Installer  
  
   L’ensemble d’outils génère des packages Windows Installer à partir de fichiers sources XML. L’ensemble d’outils est un projet Microsoft Open source. Vous pouvez télécharger le code source et les exécutables à partir de [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/).  
  
  Pour les produits commerciaux qui s’intègrent à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à l’aide de la [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], consultez [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
