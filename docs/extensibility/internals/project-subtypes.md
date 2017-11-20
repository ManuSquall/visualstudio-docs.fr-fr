---
title: Les sous-types de projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84d2700e1dfb5d66fb2df6376db9e0ce5352ad4e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="project-subtypes"></a>Sous-types de projet
Les sous-types de projet vous permettent de personnaliser ou version le comportement des systèmes de projet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Personnalisations incluent l’enregistrement de données supplémentaires dans le fichier projet, en ajoutant ou en filtrant les éléments dans le **ajouter un nouvel élément** boîte de dialogue contrôle de la façon dont les assemblys sont de débogage et déployés et l’extension du projet **propriété Pages** boîte de dialogue. Les VSPackages implémenter des sous-types de projet à l’aide de regroupements COM..  
  
> [!NOTE]
>  Le système de projet Visual C++ ne prend pas en charge les sous-types de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]lui-même utilise des sous-types de projet pour implémenter les projets Smart Device et de SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Conception de sous-types de projets](../../extensibility/internals/project-subtypes-design.md)  
 Décrit le concept de sous-types de projet.  
  
 [Séquence d’initialisation des sous-types de projets](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Décrit la séquence de l’initialisation de sous-type de projet par programmation par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.  
  
 [Propriétés et méthodes étendues par les sous-types de projets](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Fournit des descriptions détaillées des fonctions et méthodes fréquemment étendus à l’aide de sous-types de projet.  
  
 [Données persistantes dans le fichier projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Décrit comment rendre persistantes des données dans un fichier projet et comment utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pour conserver les données dans le fichier projet entre les niveaux d’agrégation de sous-type projet.  
  
 [Interface utilisateur des propriétés du projet](../../extensibility/internals/project-property-user-interface.md)  
 Décrit comment les sous-types de projet peuvent modifier le projet **Pages de propriétés** boîte de dialogue.  
  
 [Extension du modèle d’objet du projet de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Fournit des informations sur l’utilisation des sous-types de projet extendeurs Automation pour étendre le modèle objet automation.  
  
 [Contribution à la boîte de dialogue Ajouter un élément](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Décrit comment ajouter des éléments à la **ajouter un nouvel élément** boîte de dialogue.  
  
 [Enregistrement de données dans les fichiers de projet](../../extensibility/saving-data-in-project-files.md)  
 Explique comment un sous-type de projet peut enregistrer et récupérer des données spécifiques au sous-type dans le fichier projet à l’aide de Managed Package Framework (MPF).  
  
 [Gestion de déploiement spécialisé](../../extensibility/internals/handling-specialized-deployment.md)  
 Explique comment les sous-types de projet peuvent fournir le comportement de déploiement spécialisées en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface.  
  
 [Ajout et suppression de pages de propriétés](../../extensibility/adding-and-removing-property-pages.md)  
 Décrit l’ajout et suppression de pages de propriétés dans le Concepteur de projets.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques détaillant [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets.