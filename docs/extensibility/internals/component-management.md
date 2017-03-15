---
title: "Gestion des composants | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation (Visual Studio SDK), composants"
  - "installation (Visual Studio SDK), gestion de fichiers"
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Gestion des composants
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les unités de tâches dans Windows Installer est appelée des composants Windows Installer \(WICs parfois appelé ou simplement composants\).  GUID identifie chaque WIC, qui est l'unité de base d'installation et de décompte de références des installations qui utilisent Windows Installer.  
  
 Bien que vous puissiez utiliser plusieurs produits pour créer votre programme d'installation d'un VSPackage, cette rubrique part du principe que les fichiers Windows Installer \(.msi\).  En créant votre programme d'installation, vous devez gérer correctement le déploiement de fichier afin que le décompte de références correct se produise à tout moment.  Par conséquent, les différentes versions de votre produit ne gêneront pas ou l'arrêt dans une combinaison de installez et désinstallez les scénarios.  
  
 dans Windows Installer, le décompte de références se produit au niveau composant.  Vous devez soigneusement organiser vos fichiers de ressources, entrées du Registre, etc.\) dans les composants.  Il existe d'autres niveaux d'organisation \(tels que des modules, des fonctionnalités, et les produits \)qui peuvent aider dans des scénarios différents.  Pour plus d'informations, consultez [Principes fondamentaux de Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## Les instructions de la conception ont installé pour l'installation côte à côte  
  
-   Créez les fichiers et les clés de Registre qui sont partagés entre les versions dans leurs propres composants.  
  
     Cela vous permet de les utiliser facilement dans la version suivante.  Par exemple, les bibliothèques de types inscrites globalement, les extensions de fichier, d'autres éléments stockées dans HKEY\_CLASSES\_ROOT, et ainsi de suite.  
  
-   Le groupe a des composants partagés dans les modules de fusion séparés.  
  
     Cela vous aide à créer correctement pour en avant côte à côte mobile.  
  
-   Installez les fichiers partagés et des clés de Registre à l'aide de les mêmes composants de Windows Installer entre les versions.  
  
     Si vous utilisez un autre composant, les fichiers et les entrées du Registre sont désinstallés lorsqu'un VSPackage avec version est désinstallé mais un autre VSPackage est encore installé.  
  
-   Ne combinez pas les éléments avec version et partagés dans le même composant.  
  
     Effectuer le rend donc impossible d'installer des éléments partagés à un emplacement global et aux éléments avec version dans des emplacements d'isolation.  
  
-   n'ont pas partagé les clés de Registre qui indiquent les fichiers avec version.  
  
     Si vous faites, les clés existantes sont remplacées lorsqu'un autre VSPackage avec version est installé.  Après avoir supprimé la deuxième version, le fichier à laquelle la clé pointe est succès.  
  
## Voir aussi  
 [Choix entre les packages VS partagés et version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scénarios d’installation du package VS](../../extensibility/internals/vspackage-setup-scenarios.md)