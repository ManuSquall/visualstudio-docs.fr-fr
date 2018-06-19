---
title: Gestion des composants | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2798d820249f0a1c4310569d22d8510710ca13ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129533"
---
# <a name="component-management"></a>Gestion des composants
Unités de tâches dans le programme d’installation de Windows sont appelées composants de Windows Installer (parfois appelés WICs ou simplement des composants). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le décompte de références pour les installations qui utilisent Windows Installer.  
  
 Bien que vous pouvez utiliser plusieurs produits pour créer votre programme d’installation de VSPackage, cette discussion suppose que l’utilisation des fichiers Windows Installer (.msi). Lorsque vous créez votre programme d’installation, vous devez gérer correctement les déploiement de fichiers afin que le comptage de référence adéquat qui se produit à tout moment. Par conséquent, différentes versions de votre produit ne seront pas interférer avec ou interrompre eux dans une combinaison d’une installation et désinstallation de scénarios.  
  
 Dans le programme d’installation de Windows, le décompte de références se produit au niveau du composant. Avec soin, vous devez organiser vos ressources, fichiers, entrées de Registre et ainsi de suite, en composants. Autres niveaux d’organisation, tels que les modules, les fonctionnalités et les produits, qui peuvent vous aider à différents scénarios. Pour plus d’informations, consultez [concepts de base de Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Instructions de la création du programme d’installation pour l’Installation côte à  
  
-   Fichiers de l’auteur et les clés de Registre qui sont partagés entre les versions dans leurs propres composants.  
  
     Cela vous permet de les consommer facilement dans la prochaine version. Par exemple, les bibliothèques de types qui sont inscrits globalement, extensions de fichier, autres éléments enregistrés dans HKEY_CLASSES_ROOT et ainsi de suite.  
  
-   Regrouper des composants partagés dans les modules de fusion distincts.  
  
     Cela permet de vous auteur correctement pour progresser côte à côte.  
  
-   Installer les fichiers partagés et les clés de Registre en utilisant les mêmes composants de Windows Installer entre les versions.  
  
     Si vous utilisez un autre composant, les fichiers et les entrées de Registre sont désinstallées quand un VSPackage avec version est désinstallé, mais un autre VSPackage est toujours installé.  
  
-   Ne mélangez pas les éléments avec version et partagées dans le même composant.  
  
     Ainsi, il est impossible d’installer les éléments partagés vers un emplacement global et des éléments avec version aux emplacements isolés.  
  
-   N’ont pas les clés de Registre partagées qui pointent vers les fichiers de version.  
  
     Si vous le faites, les clés partagées sont écrasées quand le VSPackage avec version gérée par un autre est installé. Après la suppression de la deuxième version, le fichier vers lequel pointe la clé a disparu.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix entre les VSPackages partagés et version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scénarios d’installation de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)