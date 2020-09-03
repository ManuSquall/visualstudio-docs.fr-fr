---
title: Gestion des composants | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191850"
---
# <a name="component-management"></a>Gestion des composants
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les unités de tâches dans le Windows Installer sont appelées des composants Windows Installer (parfois appelés WICs ou simplement des composants). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le décompte de références pour les configurations qui utilisent Windows Installer.  
  
 Bien que vous puissiez utiliser plusieurs produits pour créer votre programme d’installation VSPackage, cette discussion suppose l’utilisation de fichiers Windows Installer (. msi). Lorsque vous créez votre programme d’installation, vous devez correctement gérer le déploiement de fichiers afin que le décompte de références correct se produise à tout moment. Par conséquent, les différentes versions de votre produit n’interfèrent ni ne se rompent dans une combinaison de scénarios d’installation et de désinstallation.  
  
 Dans Windows Installer, le décompte de références se produit au niveau du composant. Vous devez soigneusement organiser vos ressources (fichiers, entrées de Registre, etc.) en composants. Il existe d’autres niveaux d’organisation, tels que les modules, les fonctionnalités et les produits, qui peuvent être utiles dans différents scénarios. Pour plus d’informations, consultez [principes de base de Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Instructions relatives à la création de l’installation côte à côte  
  
- Créez les fichiers et les clés de Registre qui sont partagés entre les versions dans leurs propres composants.  
  
     Cela vous permet de les utiliser facilement dans la prochaine version. Par exemple, les bibliothèques de types enregistrées globalement, les extensions de fichier, les autres éléments inscrits dans HKEY_CLASSES_ROOT, etc.  
  
- Regroupez les composants partagés dans des modules de fusion distincts.  
  
     Cela vous aide à créer correctement pour un déplacement côte à côte.  
  
- Installez les fichiers partagés et les clés de registre en utilisant les mêmes composants de Windows Installer dans les versions.  
  
     Si vous utilisez un composant différent, les fichiers et les entrées de Registre sont désinstallés lorsqu’un VSPackage avec version est désinstallé, mais qu’un autre VSPackage est encore installé.  
  
- Ne mélangez pas les versions et les éléments partagés dans le même composant.  
  
     Ainsi, il n’est pas possible d’installer des éléments partagés sur un emplacement global et des éléments avec version dans des emplacements isolés.  
  
- N’ont pas de clés de Registre partagées qui pointent vers des fichiers avec version.  
  
     Si vous le faites, les clés partagées seront remplacées lors de l’installation d’un autre VSPackage avec version. Après la suppression de la deuxième version, le fichier vers lequel pointe la clé est supprimé.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix entre les VSPackages partagés et les VSPackages avec version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scénarios d’installation de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
