---
title: "Création de Types de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1ab4f9f41fc2e98fcc9b2f7a9aeec6885e3b3005
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-project-types"></a>Création de Types de projets
Vous pouvez étendre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en créant un nouveau type de projet. Pour créer un nouveau type de projet, vous devez comprendre les différents concepts et effectuer un certain nombre d’étapes. Les rubriques suivantes fournissent une vue d’ensemble de la création de types de projets.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md)  
 Décrit l’élément, persistance d’un fichier projet et les décisions de conception mécanique engagement que vous avez à faire avant de créer un nouveau type de projet.  
  
 [Liste de vérification : création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Fournit une vue d’ensemble des étapes à suivre pour créer un nouveau type de projet qui prend en charge les tâches de programmation en tant que la modification de code et la compilation, création, le débogage et déploiement d’applications dans votre projet.  
  
 [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fournit des informations sur la façon de fournir et d’utiliser une fabrique de projet pour créer des instances d’un nouveau projet.  
  
 [Inscription d’un type de projet](../../extensibility/internals/registering-a-project-type.md)  
 Fournit des exemples de code des instructions à partir du Registre qui fournissent des chemins d’accès par défaut et des données et une table contenant des entrées à partir du script de Registre pour chaque instruction.  
  
 [Persistance d’un projet](../../extensibility/internals/project-persistence.md)  
 Décrit l’utilisation de `IPersistFileFormat` pour conserver les fichiers et les objets non basée sur un fichier de projet.  
  
 [Utilisation de MSBuild](../../extensibility/internals/using-msbuild.md)  
 Décrit comment utiliser votre type de projet le [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] moteur pour permettre aux utilisateurs de construire à partir de génération [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et à la ligne de commande.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explique l’architecture de code des outils d’affichage tels que le **Explorateur d’objets** et **affichage de classes** fenêtre. Décrit les interfaces et les méthodes qui permettent d’implémenter l’exploration des objets dans un VSPackage.  
  
 [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Explique la signification de lire les projets de détermination de l’éditeur est utilisé lorsqu’un élément de projet est ouvert et la façon dont les ressources de projet peuvent être manipulées.  
  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Montre comment donner votre VSPackage sa propre identité unique et intégrer vos DLL VSPackage et autres informations dans un package Windows Installer (. Fichier MSI) pour le déploiement à vos clients.  
  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les vues et les adresses des hiérarchies.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Fournit une vue d’ensemble d’un VSPackage, un objet COM installable qui étend la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement et explique comment implémenter votre propre VSPackage.  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Explique comment utiliser des projets pour modifier le code, compiler et générer du code, exécuter et déboguer du code et fournit des liens vers des rubriques détaillées sur la création de types de projets.