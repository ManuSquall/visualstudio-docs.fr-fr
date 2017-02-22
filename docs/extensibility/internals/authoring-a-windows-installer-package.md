---
title: "Cr&#233;ation d&#39;un Package Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers .msi, les packages VS"
  - "fichiers MSI, les packages VS"
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Cr&#233;ation d&#39;un Package Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les lecteurs de données du modèle de programme d'installation de Windows. Plutôt que d'écrire un script de procédure pour copier les fichiers et écrire des entrées de Registre, par exemple, vous créer des lignes et des colonnes dans les tables de base de données qui contiennent des données de fichiers et du Registre.  
  
## Entrées de base de données  
 Pour installer un package VS, un package Windows Installer doit contenir les entrées de base de données pour effectuer les tâches suivantes :  
  
-   Rechercher le système afin de localiser les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] votre VSPackage prend en charge \(à l'aide de tables de Windows Installer qui incluent AppSearch, CompLocator, RegLocator, DrLocator et la Signature\).  
  
-   Annuler l'installation, si aucune version prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est installé ou si un autre système du VSPackage ne sont pas remplies \(à l'aide de la table LaunchCondition\).  
  
-   Installez le VSPackage et les fichiers dépendants \(à l'aide de l'annuaire, composant et tables de fichiers\).  
  
-   Ajoutez les informations appropriées pour le VSPackage dans le Registre \(à l'aide de la table de Registre\).  
  
-   Intégrer le VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en appelant **devenv.exe \/setup** \(à l'aide de la table CustomAction\).  
  
 Pour plus d'informations, consultez [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## Outils d'installation  
 Une variété d'outils d'installation tiers fournissent un environnement de développement pour les packages Windows Installer. Deux outils gratuits sont les suivants :  
  
-   Installshield Limited Edition  
  
     Vous pouvez obtenir une version limitée de InstallShield via Visual Studio **Nouveau projet** boîte de dialogue. Développez **autres Types de projets** puis sélectionnez **le programme d'installation et de déploiement**. Sélectionnez le modèle de InstallShield.  
  
-   ensemble d'outils XML de Windows Installer  
  
     L'ensemble d'outils génère des packages Windows Installer à partir des fichiers de source XML. L'ensemble d'outils est un projet open source de Microsoft. Vous pouvez télécharger le code source et les exécutables à partir de [http:\/\/sourceforge.net\/projects\/wix](http://sourceforge.net/projects/wix).  
  
 Pour les produits commerciaux qui s'intègrent dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l'aide de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], consultez [http:\/\/visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## Voir aussi  
 [Installation de packages VS avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)