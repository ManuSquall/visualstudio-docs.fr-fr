---
title: Création d’un Package de programme d’installation de Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93c69b2fba2bc866673b294a4f5c975a6ce3eb6a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020943"
---
# <a name="author-a-windows-installer-package"></a>Créer un package Windows Installer
Les lecteurs de données du modèle de programme d’installation de Windows. Au lieu d’écrire un script de procédure pour copier des fichiers et écrire des entrées de Registre, par exemple, vous créer des lignes et des colonnes dans les tables de base de données qui contiennent des données de fichiers et du Registre.  
  
## <a name="database-entries"></a>Entrées de base de données  
Pour installer un package Visual Studio, un package Windows Installer doit contenir des entrées de base de données pour effectuer les tâches suivantes :  
  
- Rechercher le système pour localiser les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] votre VSPackage prend en charge (à l’aide de tables de programme d’installation de Windows qui incluent AppSearch CompLocator, RegLocator, DrLocator et Signature).  
  
- Annuler l’installation si aucune version prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est installé ou si un autre système du VSPackage ne sont pas remplies (à l’aide de la table LaunchCondition).  
  
- Installez le VSPackage et les fichiers dépendants (à l’aide de l’annuaire, composant et tables de fichiers).  
  
- Ajoutez les informations appropriées pour le VSPackage dans le Registre (à l’aide de la table de Registre).  
  
- Intégrer le VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en appelant **devenv.exe /setup** (à l’aide de la table CustomAction).  
  
Pour plus d’informations, consultez [programme d’installation de Windows](/windows/desktop/Msi/windows-installer-portal).
  
## <a name="setup-tools"></a>Outils d’installation  
Une variété d’outils de d’installation tiers fournissent un environnement de développement pour les packages de programme d’installation de Windows. Les outils gratuits suivants sont disponibles :  
  
- InstallShield limited edition  
  
   Vous pouvez obtenir une version limitée de InstallShield via Visual Studio **nouveau projet** boîte de dialogue. Développez **autres Types de projets** , puis sélectionnez **le programme d’installation et de déploiement**. Sélectionnez le modèle de InstallShield.  
  
- Ensemble d’outils Windows Installer XML  
  
   L’ensemble d’outils Windows Installer XML (WiX) génère des packages de programme d’installation de Windows à partir des fichiers de source XML. L’ensemble d’outils WiX est un projet open source de Microsoft. Vous pouvez télécharger le code source et les exécutables à partir de [ensemble d’outils Wix](http://sourceforge.net/projects/wix).  
  
   Pour les produits commerciaux qui s’intègrent dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l’aide de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], consultez [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer des VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)