---
title: Propriétés et méthodes étendues par les sous-types de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b944d493e8c7668d331a2db12302cea709df239
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628492"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propriétés et méthodes étendues par les sous-types de projets
Un sous-type de projet a beaucoup de puissance pour influencer le comportement du projet, car il est construit comme une agrégation d’un projet de base. Cette section présente certaines des fonctionnalités qui peuvent être améliorées ou modifiées par les sous-types de projet.

## <a name="features-gained-by-aggregation"></a>Fonctionnalités offerts par l’agrégation
 Le tableau suivant résume la plupart des méthodes d’agrégation permet des sous-types de projet remplacer dans les projets de base.

|Méthodes de substitution par agrégation|Sous-type de projet|
|---------------------------------------|---------------------|
|À partir de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Permet à un sous-type de projet<br /><br /> -Modifier la légende et l’icône du nœud de projet.<br />-Substituent à projet `Browse` objet.<br />-Contrôle si le projet peut être renommé.<br />-Ordre de tri control.<br />-Contexte d’utilisateur contrôle de l’aide dynamique.|
|À partir de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permet à un sous-type de projet contrôler quels services contextuels sont fournis aux concepteurs et aux éditeurs.|
|À partir de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Permet à un sous-type de projet<br /><br /> -Participer du routage des commandes pour les commandes de projet.<br />-Ajouter, supprimer ou désactiver les commandes ambiante de projet et les commandes actives de l’Explorateur de solutions.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permet au sous-type de projet filtrer ce que l’utilisateur voit dans le **ajouter un nouvel élément** boîte de dialogue.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Permet à un sous-type de projet<br /><br /> -Déterminer le générateur par défaut une extension de fichier spécifiée.<br />-Mapper un nom de générateur lisible humaine à un objet COM.|

## <a name="properties-used-by-project-subtypes"></a>Propriétés utilisées par les sous-types de projet
 Le système de projet de base et d’environnement peut utiliser les propriétés à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> et <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> énumérations décrites dans le tableau suivant pour activer un sous-type de projet contrôler les différentes fonctionnalités du système de projet.

|Propriété VSHPROPID|Sous-type de projet|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Permet à un sous-type de projet contrôler le contenu de la **ajouter un élément** boîte de dialogue. Le sous-type de projet peut fournir une nouvelle spécification de répertoires de modèle, ajouter de nouveaux types d’éléments, supprimer des éléments existants et réorganiser un sous-ensemble des éléments dans le projet de base **ajouter un élément** boîte de dialogue.|
|`PropertyPagesCLSIDList`|Permet à un sous-type de projet Ajouter ou supprimer des pages de propriétés indépendantes de la configuration.|
|`CfgPropertyPagesCLSIDList`|Permet à un sous-type de projet Ajouter ou supprimer des pages de propriétés dépendantes de la configuration.|
|`ExtObjectCATID`|Permet à un sous-type de projet fournir un extendeur Automation pour le projet ou le projet d’objets d’élément en connaissant le CATID d’extendeur. Par exemple, un sous-type de projet peut fournir un personnalisé `Project.Extender("<subtype>")` objet.|
|`BrowseObjectCATID`|Permet à un sous-type de projet fournir un extendeur Automation pour le `Browse` objet en connaissant le CATID d’extendeur. Par exemple, un sous-type de projet peut ajouter des propriétés supplémentaires à la <xref:EnvDTE.Project.Properties%2A> collection.|
|`CfgBrowseObjectCATID`|Permet à un sous-type de projet fournir un extendeur Automation pour l’objet de recherche de configuration de projet. Par exemple, un sous-type de projet peut ajouter des propriétés supplémentaires à la <xref:EnvDTE.Configuration.Properties%2A> collection.|
|`CfgExtObjectCATID`|Permet à un sous-type de projet fournir un extendeur Automation de l’objet de configuration.|
|`DefaultPlatformName`|Permet à un sous-type de projet déterminer le nom de la plateforme pour les objets de configuration du projet.|

 Le projet de base fournit une implémentation par défaut des propriétés ci-dessus. Le projet de base obtient en appelant `QueryInterface` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> sur le sous-type de projet extérieur, ce qui permet au sous-type de projet de substituer l’implémentation des propriétés.

## <a name="see-also"></a>Voir aussi
- [Conception de sous-types de projets](../../extensibility/internals/project-subtypes-design.md)