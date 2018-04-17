---
title: Création d’un Package de programme d’installation Windows | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 215e1496d35059448cf11457658b7d1270b5677d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="authoring-a-windows-installer-package"></a>Création d’un Package de programme d’installation de Windows
Les lecteurs de données du modèle de programme d’installation de Windows. Au lieu d’écrire un script de procédure pour copier des fichiers et d’écrire des entrées de Registre, par exemple, vous créer des lignes et des colonnes dans les tables de base de données qui contiennent des données de fichiers et du Registre.  
  
## <a name="database-entries"></a>Entrées de la base de données  
 Pour installer un VSPackage, un package Windows Installer doit contenir des entrées de base de données pour effectuer les tâches suivantes :  
  
-   Rechercher le système pour localiser les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] votre VSPackage prend en charge (à l’aide de tables de Windows Installer qui incluent AppSearch, CompLocator, RegLocator, DrLocator et Signature).  
  
-   Annuler l’installation si aucune version prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est installé ou si un autre système du VSPackage ne sont pas remplies (à l’aide de la table LaunchCondition).  
  
-   Installez le VSPackage et les fichiers dépendants (à l’aide de l’annuaire, composant et tables de fichiers).  
  
-   Ajoutez les informations appropriées pour le VSPackage dans le Registre (à l’aide de la table de Registre).  
  
-   Intégrer le VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en appelant **devenv.exe /setup** (à l’aide de la table CustomAction).  
  
 Pour plus d’informations, consultez [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Le programme d’installation des outils  
 Divers outils de programme d’installation de tiers fournissent un environnement de développement pour les packages Windows Installer. Deux outils gratuits sont les suivants :  
  
-   Installshield Limited Edition  
  
     Vous pouvez obtenir une version limitée de InstallShield via Visual Studio **nouveau projet** boîte de dialogue. Développez **autres Types de projets** , puis sélectionnez **le programme d’installation et de déploiement**. Sélectionnez le modèle d’InstallShield.  
  
-   ensemble d'outils XML de Windows Installer  
  
     L’ensemble d’outils génère des packages Windows Installer à partir des fichiers de source XML. L’ensemble d’outils est un projet open source de Microsoft. Vous pouvez télécharger le code source et les exécutables à partir de [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
 Pour les produits commerciaux qui s’intègre à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l’aide de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], consultez [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)