---
title: Création de types de projets (fr) Microsoft Docs
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
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709069"
---
# <a name="create-project-types"></a>Créer des types de projets
Vous pouvez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prolonger en créant un nouveau type de projet. Pour créer un nouveau type de projet, vous devez comprendre plusieurs concepts et remplir un certain nombre d’étapes. Les sujets suivants donnent un aperçu de la façon de créer des types de projets.

## <a name="in-this-section"></a>Contenu de cette section
- [Décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md)

 Discute de l’élément, de la persistance des fichiers de projet et des décisions de conception de mécaniciens d’engagement que vous devez prendre avant de créer un nouveau type de projet.

- [Liste de contrôle : Créer de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)

 Fournit un aperçu des étapes que vous devez suivre pour créer un nouveau type de projet qui prend en charge des tâches de programmation telles que l’édition de code et la compilation, la construction, le débogage et le déploiement d’applications dans votre projet.

- [Créer des instances de projet en utilisant des usines de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Fournit des informations sur la façon de fournir et d’utiliser une usine de projet pour créer des exemples d’un nouveau projet.

- [Enregistrer un type de projet](../../extensibility/internals/registering-a-project-type.md)

 Fournit des échantillons de code des relevés du registre qui fournissent des chemins et des données par défaut, et un tableau qui contiennent des entrées du script du registre pour chaque relevé.

- [Persistance du projet](../../extensibility/internals/project-persistence.md)

 Discute de `IPersistFileFormat` l’utilisation de la persistance à la fois des objets de projet basés sur des fichiers et des fichiers.

- [Utiliser MSBuild](../../extensibility/internals/using-msbuild.md)

 Décrit comment votre type de [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] projet peut utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le moteur de construction pour permettre aux utilisateurs de construire à partir et à la ligne de commande.

## <a name="related-sections"></a>Sections connexes
- [Soutenir les outils de navigation des symboles](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Explique l’architecture des outils d’affichage de code tels que le **navigateur d’objets** et la fenêtre **Class View.** Décrit les interfaces et les méthodes qui sont utilisées pour implémenter la navigation d’objets dans un VSPackage.

- [Ajouter des modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Discute de l’importance que jouent les projets pour déterminer quel éditeur est utilisé lors de l’ouverture d’un élément de projet et comment les ressources du projet peuvent être manipulées.

- [Installer VSPackages avec Installateur Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Montre comment donner à votre VSPackage sa propre identité unique et comment envelopper vos DLL VSPackage et d’autres informations dans un package d’installateur Windows (*. Fichier MSI)* pour le déploiement à vos clients.

- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les vues et les adresses hiérarchies.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Fournit un aperçu d’un VSPackage, un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objet COM installable qui étend l’environnement et discute de la façon de mettre en œuvre votre propre VSPackage.

- [Types de projet](../../extensibility/internals/project-types.md)

 Discute de la façon d’utiliser des projets pour modifier le code, compiler et construire du code, et exécuter et déboguer du code, et fournit des liens vers des sujets détaillés sur la façon de créer des types de projets.
