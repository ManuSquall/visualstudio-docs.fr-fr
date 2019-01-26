---
title: Gestion des composants | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10d5654983de6ced572d60243a7744608b2c3f53
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031381"
---
# <a name="component-management"></a>Gestion des composants
Unités de tâches dans le programme d’installation de Windows sont appelées composants de programme d’installation de Windows (parfois appelés WICs ou composants uniquement). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le décompte de références pour les installations qui utilisent Windows Installer.  
  
 Bien que vous pouvez utiliser plusieurs produits pour créer votre programme d’installation de package Visual Studio, cette discussion suppose l’utilisation du programme d’installation de Windows (*.msi*) les fichiers. Lorsque vous créez votre programme d’installation, vous devez gérer correctement les déploiement de fichiers, afin que le comptage de références correctes effectuée à tout moment. Par conséquent, différentes versions de votre produit ne seront pas interférer avec ou rompre eux dans une combinaison de l’installation et désinstaller des scénarios.  
  
 Dans le programme d’installation de Windows, le comptage de références se produit au niveau du composant. Soigneusement, vous devez organiser vos ressources, fichiers, entrées de Registre et ainsi de suite, en composants. Autres niveaux de l’organisation, tels que les modules, les fonctionnalités et les produits, qui peut aider dans différents scénarios. Pour plus d’informations, consultez [principes fondamentaux du programme d’installation de Windows](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Recommandations en matière de création le programme d’installation pour l’installation de la côte à côte  
  
-   Fichiers de l’auteur et les clés de Registre qui sont partagés entre les versions dans leurs propres composants.  
  
     Cela vous permet de les consommer facilement dans la prochaine version. Par exemple, les bibliothèques de types qui sont inscrits dans le monde entier, les extensions de fichier, les autres éléments enregistrés dans **HKEY_CLASSES_ROOT**, et ainsi de suite.  
  
-   Regrouper des composants partagés dans des modules de fusion distinct.  
  
     Cette stratégie permet de vous auteur correctement pour l’installation côte à côte plus tard.  
  
-   Installer les fichiers partagés et les clés de Registre en utilisant les mêmes composants de programme d’installation de Windows sur les versions.  
  
     Si vous utilisez un autre composant, les fichiers et les entrées de Registre sont désinstallées quand un VSPackage avec contrôle de version est désinstallé, mais un autre VSPackage est toujours installé.  
  
-   Ne mélangez pas les éléments avec version et partagés dans le même composant.  
  
     Cela rend impossible d’installer les éléments partagés vers un emplacement global et des éléments avec version aux emplacements isolés.  
  
-   N’ont pas les clés de Registre partagées qui pointent vers les fichiers de version.  
  
     Si vous le faites, les clés partagées seront remplacées lors de l’installation de VSPackage avec version gérée par un autre. Une fois que vous supprimez la deuxième version, le fichier vers lequel pointe la clé a disparu.  
  
## <a name="see-also"></a>Voir aussi  
 [Choisissez entre les VSPackages partagés et avec contrôle de version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scénarios d’installation de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)