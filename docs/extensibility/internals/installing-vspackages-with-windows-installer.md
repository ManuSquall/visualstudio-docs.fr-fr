---
title: "Installation de packages VS avec Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation (Visual Studio SDK), avec Windows Installer"
  - "VSPackages, déploiement"
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# Installation de packages VS avec Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Intégrant votre VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] exige que plus que des fichiers sur l'ordinateur d'un utilisateur.  le programme d'installation de votre VSPackage doit installer le VSPackage et ses fichiers dépendants, et registre et les intégrer dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Votre VSPackage peut tirer parti des fonctionnalités d'intégration comme afficher une icône sur l'écran de démarrage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et sur boîte de dialogue.  
  
 Les fichiers Microsoft Windows Installer est la méthode recommandée pour distribuer votre VSPackages.  Les package Windows Installer faciles à utiliser peuvent s'exécuter sur un système d'exploitation Windows pris en charge par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations, consultez [Windows Installer](http://msdn.microsoft.com/fr-fr/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## Dans cette section  
 [Principes fondamentaux de Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Fournit une vue d'ensemble de Windows Installer.  
  
 [Scénarios d’installation du package VS](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Décrit différentes manières que vous pouvez prendre en charge côte à côte les installations de votre les VSPackages et de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Création d'un Package Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Fournit une vue d'ensemble des étapes classiques que les programmes d'installation suivent correctement pour installer et intégrer des VSPackages dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Détecter la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)  
 Décrit comment un programme d'installation peut détecter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ses composants et installation d'annulation si les spécifications d'un VSPackage ne sont pas satisfaites.  
  
 [Gestion des composants](../../extensibility/internals/component-management.md)  
 Explique comment développer un programme d'installation qui contiendra l'intégrité des versions du produit précédentes.  
  
 [Choisir le répertoire d'Installation pour un VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Résume les options pour localiser les VSPackages.  
  
 [Inscription du package VS](../../extensibility/internals/vspackage-registration.md)  
 Explique comment VSPackages sont stockés au moment de l'installation et pourquoi l'inscription automatique est déconseillé idée.  
  
 [Types de projets de déploiement](../../extensibility/internals/deploying-project-types.md)  
 Explique comment utiliser la nouvelle agrégation de projet\-type pour les types de projet de code managé.  
  
 [Comment : générer des informations de Registre pour un programme d'installation](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Explique comment utiliser RegPkg.exe pour générer un manifeste d'alignement pour un VSPackage managé.  
  
 [Commandes doivent être exécutés après l'Installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Explique comment exécuter des commandes de post\-installation d'intégrer des VSPackages dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Désinstallation d'un VSPackage avec Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Décrit les étapes à votre programme d'installation doit effectuer lorsque les utilisateurs de la désinstallation votre VSPackage.  
  
## Rubriques connexes  
 [Installation de VSPackages](../../misc/installing-vspackages.md)  
 Explique comment générer et installer les VSPackages et comment prendre en charge les utilisateurs qui sont l'exécution de plusieurs versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en même temps.