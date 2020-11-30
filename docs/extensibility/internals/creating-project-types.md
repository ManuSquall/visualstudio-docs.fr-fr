---
title: Création de types de projets | Microsoft Docs
description: Apprenez à étendre Visual Studio en concevant, en créant et en inscrivant un nouveau type de projet qui prend en charge les tâches de programmation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4038a122c6d2ec5f6ed29df6e529b2bff2e2bb71
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329924"
---
# <a name="create-project-types"></a>Créer des types de projet
Vous pouvez étendre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en créant un nouveau type de projet. Pour créer un nouveau type de projet, vous devez comprendre plusieurs concepts et effectuer un certain nombre d’étapes. Les rubriques suivantes fournissent une vue d’ensemble de la façon de créer des types de projet.

## <a name="in-this-section"></a>Dans cette section
- [Décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md)

 Décrit les décisions de conception relatives à l’élément, à la persistance du fichier projet et aux mécaniciens que vous devez effectuer avant de créer un nouveau type de projet.

- [Liste de vérification : créer des types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)

 Fournit une vue d’ensemble des étapes que vous devez suivre pour créer un nouveau type de projet qui prend en charge des tâches de programmation telles que la modification du code et la compilation, la génération, le débogage et le déploiement d’applications dans votre projet.

- [Créer des instances de projet à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Fournit des informations sur la façon de fournir et d’utiliser une fabrique de projets pour créer des instances d’un nouveau projet.

- [Inscrire un type de projet](../../extensibility/internals/registering-a-project-type.md)

 Fournit des exemples de code d’instructions du Registre qui fournissent des chemins d’accès et des données par défaut, ainsi qu’une table qui contient des entrées du script de Registre pour chaque instruction.

- [Persistance du projet](../../extensibility/internals/project-persistence.md)

 Explique l’utilisation de `IPersistFileFormat` pour conserver les objets de projet de fichier et non basés sur des fichiers.

- [Utiliser MSBuild](../../extensibility/internals/using-msbuild.md)

 Décrit comment votre type de projet peut utiliser le [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] moteur de génération pour permettre aux utilisateurs de générer à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et à partir de la ligne de commande.

## <a name="related-sections"></a>Sections connexes
- [Prise en charge des outils de navigation de symboles](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Explique l’architecture des outils d’affichage du code tels que l' **Explorateur d’objets** et la fenêtre de **affichage de classes** . Décrit les interfaces et les méthodes utilisées pour implémenter l’exploration d’objets dans un VSPackage.

- [Ajouter des modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Explique l’importance que les projets jouent pour déterminer quel éditeur est utilisé lorsqu’un élément de projet est ouvert et comment les ressources de projet peuvent être manipulées.

- [Installer les VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Montre comment fournir à votre VSPackage une identité unique et comment encapsuler vos dll VSPackage et d’autres informations dans un package Windows Installer (*. Fichier MSI* ) pour le déploiement vers vos clients.

- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les vues et les adresses des hiérarchies.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Fournit une vue d’ensemble d’un VSPackage, un objet COM pouvant être installé qui étend l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement et explique comment implémenter votre propre VSPackage.

- [Types de projets](../../extensibility/internals/project-types.md)

 Explique comment utiliser des projets pour modifier du code, compiler et générer du code, exécuter et déboguer du code, et fournit des liens vers des rubriques détaillées sur la façon de créer des types de projet.
