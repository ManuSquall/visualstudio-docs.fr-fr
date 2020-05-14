---
title: Sous-types de projets Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706413"
---
# <a name="project-subtypes"></a>Sous-types de projets
Les sous-types de projet vous permettent de personnaliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ou de parfumer le comportement des systèmes de projet de . Les personnalisations comprennent l’enregistrement de données supplémentaires dans le fichier du projet, l’ajout ou le filtrage des éléments dans la boîte de dialogue **Add New Item,** le contrôle de la façon dont les assemblages sont déboutés et déployés, et l’extension de la boîte de dialogue du projet **Pages de propriété.** VSPackages implémente des sous-types de projets à l’aide de l’agrégation COM.

> [!NOTE]
> Le système de projet Visual CMD ne prend pas en charge les sous-types de projets. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilise lui-même des sous-types de projets pour implémenter des projets SQL Server et Smart Device.

## <a name="in-this-section"></a>Dans cette section
- [Conception de sous-types de projets](../../extensibility/internals/project-subtypes-design.md)

 Décrit le concept de sous-types de projets.

- [Séquence d’initialisation des sous-types de projets](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Décrit la séquence programmatique de sous-type d’initialisation par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.

- [Propriétés et méthodes étendues par les sous-types de projets](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Fournit des descriptions détaillées des caractéristiques et des méthodes les plus fréquemment étendues en utilisant des sous-types de projet.

- [Données persistantes dans le fichier projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Décrit comment conserver les données dans un <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> fichier de projet et comment utiliser les données dans le fichier du projet à travers les niveaux d’agrégation de sous-types du projet.

- [Interface utilisateur des propriétés du projet](../../extensibility/internals/project-property-user-interface.md)

 Décrit comment les sous-types de projet peuvent modifier la boîte de dialogue **des Pages de propriété** du projet.

- [Extension du modèle d’objet du projet de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Fournit des informations sur la façon dont les sous-types de projet peuvent utiliser Automation Extenders pour étendre le modèle d’objet d’automatisation.

- [Contribution à la boîte de dialogue Ajouter un élément](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Décrit comment ajouter des éléments à la boîte de dialogue **Add New Item.**

- [Enregistrement de données dans les fichiers de projet](../../extensibility/saving-data-in-project-files.md)

 Explique comment un sous-type de projet peut enregistrer et récupérer des données spécifiques au sous-type dans le fichier du projet en utilisant le cadre de paquet géré (MPF).

- [Gestion de déploiement spécialisé](../../extensibility/internals/handling-specialized-deployment.md)

 Explique comment les sous-types de projet peuvent <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> fournir un comportement de déploiement spécialisé en implémentant l’interface.

- [Ajout et suppression de pages de propriétés](../../extensibility/adding-and-removing-property-pages.md)

 Décrit l’ajout et la suppression des pages de propriété dans Project Designer.

## <a name="related-sections"></a>Sections connexes
- [Types de projets](../../extensibility/internals/project-types.md)

 Fournit des liens [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vers des sujets détaillant les projets.
