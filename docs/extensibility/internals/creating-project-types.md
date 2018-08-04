---
title: Création de Types de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a453e8ed6c59f242e8a3aadbf056f956aedcaca
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499914"
---
# <a name="create-project-types"></a>Créer des types de projets
Vous pouvez étendre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en créant un nouveau type de projet. Pour créer un nouveau type de projet, vous devez comprendre les différents concepts et effectuer un certain nombre d’étapes. Les rubriques suivantes fournissent une vue d’ensemble de la création de types de projets.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md)  
 Décrit l’élément, persistance d’un fichier projet et les décisions de conception mécanique d’engagement que vous avez à faire avant de créer un nouveau type de projet.  
  
 [Liste de vérification : Créer des types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Fournit une vue d’ensemble des étapes à suivre pour créer un nouveau type de projet qui prend en charge de ces tâches de programmation en tant que la modification du code et compilation, création, le débogage et déploiement d’applications dans votre projet.  
  
 [Créer des instances de projet à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fournit des informations sur la façon de fournir et d’utiliser une fabrique de projet pour créer des instances d’un nouveau projet.  
  
 [Inscrire un type de projet](../../extensibility/internals/registering-a-project-type.md)  
 Fournit des exemples de code d’instructions à partir du Registre qui fournissent des chemins d’accès par défaut et des données et une table contenant des entrées à partir du script de Registre pour chaque instruction.  
  
 [Persistance d’un projet](../../extensibility/internals/project-persistence.md)  
 Explique comment utiliser `IPersistFileFormat` pour conserver les objets fichier et non basée sur un fichier de projet.  
  
 [Utilisation de MSBuild](../../extensibility/internals/using-msbuild.md)  
 Décrit comment votre type de projet peut utiliser le [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] moteur pour permettre aux utilisateurs de générer à partir de génération [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et à la ligne de commande.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Prend en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explique l’architecture de code des outils d’affichage tels que le **Explorateur d’objets** et **affichage de classes** fenêtre. Décrit les interfaces et les méthodes qui sont utilisées pour implémenter l’exploration des objets dans un VSPackage.  
  
 [Ajouter le projet et les modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Explique la signification qui jouent des projets pour déterminer quel éditeur est utilisé lorsqu’un élément de projet est ouvert et comment les ressources de projet peuvent être manipulées.  
  
 [Installer des VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Montre comment accorder à votre VSPackage sa propre identité unique et comment encapsuler votre DLL de VSPackage et d’autres informations dans un package Windows Installer (*. MSI* fichier) pour le déploiement de vos clients.  
  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hiérarchies des vues et des adresses.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Fournit une vue d’ensemble d’un VSPackage, un objet COM installable qui étend la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement et explique comment implémenter votre propre VSPackage.  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Explique comment utiliser les projets pour modifier le code, compiler et générer du code, exécuter et déboguer du code et fournit des liens vers des rubriques détaillées sur la création de types de projets.