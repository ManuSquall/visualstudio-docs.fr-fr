---
title: "Sous-types de projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets (Visual Studio SDK), sous-types"
  - "sous-types de projets (Visual Studio SDK)"
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Sous-types de projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les sous\-types de projet vous permettent de personnaliser ou touche le comportement des systèmes de projet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Personnalisations incluent l'enregistrement de données supplémentaires dans le fichier projet, en ajoutant ou en filtrant les éléments dans le **Ajouter un nouvel élément** boîte de dialogue, contrôler comment les assemblys sont de débogage et le déploiement et l'extension du projet **Pages de propriétés** boîte de dialogue. Les VSPackages implémenter des sous\-types de projets à l'aide de regroupements COM..  
  
> [!NOTE]
>  Le système de projet Visual C\+\+ ne prend pas en charge les sous\-types de projets.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lui\-même utilise des sous\-types de projets pour implémenter les projets Smart Device et de SQL Server.  
  
## Dans cette section  
 [Conception des sous\-types de projet](../../extensibility/internals/project-subtypes-design.md)  
 Décrit le concept des sous\-types de projets.  
  
 [Séquence d'initialisation des sous\-types de projets](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Décrit la séquence d'initialisation sous\-type projet par programmation par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.  
  
 [Propriétés et méthodes étendus par les sous\-types de projets](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Fournit une description détaillée des fonctionnalités et des méthodes plus étendus à l'aide des sous\-types de projets.  
  
 [Données persistantes dans le fichier projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Décrit comment rendre persistantes des données dans un fichier de projet et l'utilisation de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pour conserver les données dans le fichier projet dans les niveaux d'agrégation du sous\-type projet.  
  
 [Interface utilisateur de propriétés du projet](../../extensibility/internals/project-property-user-interface.md)  
 Décrit comment les sous\-types de projets peuvent modifier le projet **Pages de propriétés** boîte de dialogue.  
  
 [Extension du modèle d'objet du projet de Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Fournit des informations sur l'utilisation des sous\-types de projet extendeurs Automation pour étendre le modèle objet automation.  
  
 [Faisant partie de la boîte de dialogue Nouvel élément Ajouter](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Décrit comment ajouter des éléments à la **Ajouter un nouvel élément** boîte de dialogue.  
  
 [Enregistrer les données dans les fichiers projet](../../extensibility/saving-data-in-project-files.md)  
 Explique comment un sous\-type de projet permettre enregistrer et récupérer des données de sous\-type dans le fichier projet à l'aide de Managed Package Framework \(MPF\).  
  
 [Gestion spécialisée de déploiement](../../extensibility/internals/handling-specialized-deployment.md)  
 Explique comment sous\-types de projets peuvent fournir le comportement de déploiement spécialisées en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface.  
  
 [Ajout et suppression de Pages de propriétés](../../extensibility/adding-and-removing-property-pages.md)  
 Décrit l'ajout et la suppression des pages de propriétés dans le Concepteur de projets.  
  
## Rubriques connexes  
 [Types de projet](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques décrivant [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets.