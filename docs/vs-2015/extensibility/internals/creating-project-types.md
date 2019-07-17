---
title: Création de Types de projet | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155033"
---
# <a name="creating-project-types"></a>Création de types de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous pouvez étendre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en créant un nouveau type de projet. Pour créer un nouveau type de projet, vous devez comprendre les différents concepts et effectuer un certain nombre d’étapes. Les rubriques suivantes fournissent une vue d’ensemble de la création de types de projets.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md)  
 Décrit l’élément, persistance d’un fichier projet et les décisions de conception mécanique d’engagement que vous avez à faire avant de créer un nouveau type de projet.  
  
 [Liste de contrôle : Création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Fournit une vue d’ensemble des étapes à suivre pour créer un nouveau type de projet qui prend en charge les tâches de programmation en tant que la modification du code et compilation, création, le débogage et déploiement d’applications dans votre projet.  
  
 [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fournit des informations sur la façon de fournir et d’utiliser une fabrique de projet pour créer des instances d’un nouveau projet.  
  
 [Inscription d’un type de projet](../../extensibility/internals/registering-a-project-type.md)  
 Fournit des exemples de code d’instructions à partir du Registre qui fournissent des chemins d’accès par défaut et des données et une table contenant des entrées à partir du script de Registre pour chaque instruction.  
  
 [Persistance d’un projet](../../extensibility/internals/project-persistence.md)  
 Explique comment utiliser `IPersistFileFormat` pour conserver les objets fichier et non basée sur un fichier de projet.  
  
 [Utilisation de MSBuild](../../extensibility/internals/using-msbuild.md)  
 Décrit comment votre type de projet peut utiliser le [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] moteur pour permettre aux utilisateurs de générer à partir de génération [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et à la ligne de commande.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explique l’architecture de code des outils d’affichage tels que le **Explorateur d’objets** et **affichage de classes** fenêtre. Décrit les interfaces et les méthodes qui sont utilisées pour implémenter l’exploration des objets dans un VSPackage.  
  
 [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Explique la signification qui jouent des projets pour déterminer quel éditeur est utilisé lorsqu’un élément de projet est ouvert et comment les ressources de projet peuvent être manipulées.  
  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Montre comment accorder à votre VSPackage sa propre identité unique et comment encapsuler votre DLL de VSPackage et d’autres informations dans un package Windows Installer (. Fichier MSI) pour le déploiement de vos clients.  
  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Décrit comment [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hiérarchies des vues et des adresses.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Fournit une vue d’ensemble d’un VSPackage, un objet COM installable qui étend la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement et explique comment implémenter votre propre VSPackage.  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Explique comment utiliser les projets pour modifier le code, compiler et générer du code, exécuter et déboguer du code et fournit des liens vers des rubriques détaillées sur la création de types de projets.
