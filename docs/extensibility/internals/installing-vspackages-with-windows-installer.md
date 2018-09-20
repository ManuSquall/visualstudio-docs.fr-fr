---
title: Installation de VSPackages avec Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3bb49f02b7c160aa879c0652a081d8fd6cb026a
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370534"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installation de VSPackages avec Windows Installer
L’intégration de votre VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nécessite plus qu’une simple copie de fichiers à l’ordinateur d’un utilisateur. Programme d’installation de votre VSPackage doit installer le package Visual Studio et ses fichiers dépendants et de s’inscrire et de les intégrer à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Votre VSPackage peut tirer parti des fonctionnalités d’intégration tels que l’affichage d’une icône sur la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] écran et la boîte de dialogue à propos de démarrage.  
  
 Les fichiers de programme d’installation de Microsoft Windows sont la méthode recommandée pour distribuer vos VSPackages. Facile à utiliser les packages de programme d’installation de Windows peuvent s’exécuter sur n’importe quel système d’exploitation Windows pris en charge par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [programme d’installation de Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Éléments de base de Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Fournit une vue d’ensemble de Windows Installer.  
  
 [Scénarios d’installation de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Aborde les diverses manières vous pouvez prendre en charge les installations côte à côte de deux vos VSPackages et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Création d’un package Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Fournit une vue d’ensemble des étapes classiques suivent des programmes d’installation pour installer correctement et d’intégrer des VSPackages en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)  
 Décrit comment un programme d’installation peut détecter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ses composants et les annuler le programme d’installation si le VSPackage ne sont pas satisfaites.  
  
 [Gestion des composants](../../extensibility/internals/component-management.md)  
 Explique comment développer un programme d’installation qui préserve l’intégrité des versions précédentes du produit.  
  
 [Choix du répertoire d’installation d’un VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Résume les options permettant de localiser les VSPackages.  
  
 [Inscription de VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Explique comment les VSPackages sont enregistrés au moment de l’installation et pourquoi l’inscription automatique est une mauvaise idée.  
  
 [Déploiement des types de projets](../../extensibility/internals/deploying-project-types.md)  
 Explique comment utiliser le nouvel aggregator de type de projet pour les types de projet de code managé.  
  
 [Guide pratique pour générer des informations de registre pour un programme d’installation](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Explique comment utiliser RegPkg.exe pour générer un manifeste de l’inscription d’un VSPackage managé.  
  
 [Commandes à exécuter après l’installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Explique comment exécuter des commandes de post-installation pour intégrer des VSPackages en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Désinstallation d’un VSPackage avec Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Décrit les étapes de que votre programme d’installation doit effectuer lorsque les utilisateurs le désinstallent votre VSPackage.  