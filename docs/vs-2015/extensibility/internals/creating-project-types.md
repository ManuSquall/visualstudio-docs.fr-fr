---
title: Création de types de projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155033"
---
# <a name="creating-project-types"></a>Création de types de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous pouvez étendre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en créant un nouveau type de projet. Pour créer un nouveau type de projet, vous devez comprendre plusieurs concepts et effectuer un certain nombre d’étapes. Les rubriques suivantes fournissent une vue d’ensemble de la façon de créer des types de projet.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md)  
 Décrit les décisions de conception relatives à l’élément, à la persistance du fichier projet et aux mécaniciens que vous devez effectuer avant de créer un nouveau type de projet.  
  
 [Checklist : création de types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Fournit une vue d’ensemble des étapes que vous devez suivre pour créer un nouveau type de projet qui prend en charge les tâches de programmation comme la modification du code et la compilation, la génération, le débogage et le déploiement d’applications dans votre projet.  
  
 [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fournit des informations sur la façon de fournir et d’utiliser une fabrique de projets pour créer des instances d’un nouveau projet.  
  
 [Inscription d’un type de projet](../../extensibility/internals/registering-a-project-type.md)  
 Fournit des exemples de code d’instructions du Registre qui fournissent des chemins d’accès et des données par défaut, ainsi qu’une table qui contient des entrées du script de Registre pour chaque instruction.  
  
 [Persistance d’un projet](../../extensibility/internals/project-persistence.md)  
 Explique l’utilisation de `IPersistFileFormat` pour conserver les objets de projet de fichier et non basés sur des fichiers.  
  
 [Utilisation de MSBuild](../../extensibility/internals/using-msbuild.md)  
 Décrit comment votre type de projet peut utiliser le [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] moteur de génération pour permettre aux utilisateurs de générer à partir de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et à partir de la ligne de commande.  
  
## <a name="related-sections"></a>Sections connexes  
 [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explique l’architecture des outils d’affichage du code tels que l' **Explorateur d’objets** et la fenêtre de **affichage de classes** . Décrit les interfaces et les méthodes utilisées pour implémenter l’exploration d’objets dans un VSPackage.  
  
 [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Explique l’importance que les projets jouent pour déterminer quel éditeur est utilisé lorsqu’un élément de projet est ouvert et comment les ressources de projet peuvent être manipulées.  
  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Montre comment fournir à votre VSPackage une identité unique et comment encapsuler vos dll VSPackage et d’autres informations dans un package Windows Installer (. Fichier MSI) pour le déploiement vers vos clients.  
  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Décrit comment [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] les vues et les adresses des hiérarchies.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Fournit une vue d’ensemble d’un VSPackage, un objet COM pouvant être installé qui étend l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement et explique comment implémenter votre propre VSPackage.  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Explique comment utiliser des projets pour modifier du code, compiler et générer du code, exécuter et déboguer du code, et fournit des liens vers des rubriques détaillées sur la façon de créer des types de projet.
