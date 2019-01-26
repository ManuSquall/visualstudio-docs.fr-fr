---
title: Les sous-types de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c2e5151131efdab36a3c9e5cf646b1ca9bf94b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922715"
---
# <a name="project-subtypes"></a>Sous-types de projets
Les sous-types de projet vous permettent de personnaliser ou de spécifier le comportement des systèmes de projet de la version [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Personnalisations incluent l’enregistrement des données supplémentaires dans le fichier projet, en ajoutant ou en filtrant les éléments dans le **ajouter un nouvel élément** boîte de dialogue, contrôler comment les assemblys sont débogués et déployés et en étendant le projet **propriété Pages** boîte de dialogue. Les VSPackages implémenter des sous-types de projet à l’aide d’agrégation COM.  
  
> [!NOTE]
>  Le système de projet Visual C++ ne prend pas en charge les sous-types de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lui-même utilise des sous-types de projet pour implémenter des projets Smart Device et de SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Conception de sous-types de projets](../../extensibility/internals/project-subtypes-design.md)  
 Décrit le concept de sous-types de projet.  
  
 [Séquence d’initialisation des sous-types de projets](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Décrit la séquence de l’initialisation de sous-type de projet par programmation par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.  
  
 [Propriétés et méthodes étendues par les sous-types de projets](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Fournit des descriptions détaillées des fonctions et méthodes étendues plus fréquemment à l’aide de sous-types de projet.  
  
 [Données persistantes dans le fichier projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Décrit comment conserver les données dans un fichier projet et comment utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pour conserver les données dans le fichier projet entre les niveaux de d’agrégation de sous-type de projet.  
  
 [Interface utilisateur des propriétés du projet](../../extensibility/internals/project-property-user-interface.md)  
 Décrit comment les sous-types de projet peuvent modifier le projet **Pages de propriétés** boîte de dialogue.  
  
 [Extension du modèle d’objet du projet de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Fournit des informations sur l’utilisation des sous-types de projet extendeurs Automation pour étendre le modèle objet automation.  
  
 [Contribution à la boîte de dialogue Ajouter un élément](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Décrit comment ajouter des éléments à la **ajouter un nouvel élément** boîte de dialogue.  
  
 [Enregistrement de données dans les fichiers de projet](../../extensibility/saving-data-in-project-files.md)  
 Explique comment un sous-type de projet peut enregistrer et récupérer des données spécifiques au sous-type dans le fichier projet à l’aide de Managed Package Framework (MPF).  
  
 [Gestion de déploiement spécialisé](../../extensibility/internals/handling-specialized-deployment.md)  
 Explique comment les sous-types de projet peuvent fournir le comportement de déploiement spécialisé en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface.  
  
 [Ajout et suppression de pages de propriétés](../../extensibility/adding-and-removing-property-pages.md)  
 Décrit l’ajout et suppression des pages de propriétés dans le Concepteur de projets.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques détaillant [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets.