---
title: Sous-types de projet | Microsoft Docs
description: Découvrez comment les sous-types de projet vous permettent de personnaliser le comportement des systèmes de projet de Visual Studio. Les VSPackages implémentent des sous-types de projet à l’aide de l’agrégation COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd0f959d300fdc797d9e42d581a163b8b0892591
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903578"
---
# <a name="project-subtypes"></a>Sous-types de projets
Les sous-types de projet vous permettent de personnaliser ou de parfumer le comportement des systèmes de projet de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Les personnalisations incluent l’enregistrement de données supplémentaires dans le fichier projet, l’ajout ou le filtrage d’éléments dans la boîte de dialogue **Ajouter un nouvel élément** , le contrôle de la façon dont les assemblys sont débogués et déployés et l’extension de la boîte de dialogue **pages de propriétés** du projet. Les VSPackages implémentent des sous-types de projet à l’aide de l’agrégation COM.

> [!NOTE]
> Le système de projet Visual C++ ne prend pas en charge les sous-types de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elle-même utilise des sous-types de projet pour implémenter SQL Server et des projets Smart Device.

## <a name="in-this-section"></a>Dans cette section

- [Conception de sous-types de projets](../../extensibility/internals/project-subtypes-design.md)

  Décrit le concept de sous-types de projet.

- [Séquence d’initialisation des sous-types de projets](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Décrit la séquence d’initialisation de sous-type de projet de programmation par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.

- [Propriétés et méthodes étendues par les sous-types de projets](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Fournit des descriptions détaillées des fonctionnalités et des méthodes les plus fréquemment étendues à l’aide de sous-types de projet.

- [Données persistantes dans le fichier projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Décrit comment rendre des données persistantes dans un fichier projet et comment utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pour gérer les données dans le fichier projet à travers les niveaux d’agrégation de sous-type de projet.

- [Interface utilisateur des propriétés du projet](../../extensibility/internals/project-property-user-interface.md)

  Décrit comment les sous-types de projet peuvent modifier la boîte de dialogue **pages de propriétés** du projet.

- [Extension du modèle d’objet du projet de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Fournit des informations sur la façon dont les sous-types de projet peuvent utiliser des extendeurs Automation pour étendre le modèle objet Automation.

- [Contribution à la boîte de dialogue Ajouter un élément](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  Décrit comment ajouter des éléments à la boîte de dialogue **Ajouter un nouvel élément** .

- [Enregistrement de données dans les fichiers de projet](../../extensibility/saving-data-in-project-files.md)

  Explique comment un sous-type de projet peut enregistrer et récupérer des données spécifiques au sous-type dans le fichier projet à l’aide de Managed package Framework (MPF).

- [Gestion de déploiement spécialisé](../../extensibility/internals/handling-specialized-deployment.md)

  Explique comment les sous-types de projet peuvent fournir un comportement de déploiement spécialisé en implémentant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface.

- [Ajout et suppression de pages de propriétés](../../extensibility/adding-and-removing-property-pages.md)

  Décrit l’ajout et la suppression de pages de propriétés dans le concepteur de projets.

## <a name="related-sections"></a>Sections connexes

- [Types de projets](../../extensibility/internals/project-types.md)

  Fournit des liens vers des rubriques détaillant les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets.
