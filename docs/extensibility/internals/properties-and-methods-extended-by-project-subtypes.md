---
title: Propriétés et méthodes étendues par les sous-types de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f5f67ac70b7ca6d5151a9115f20be88f6984d52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725346"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propriétés et méthodes étendues par les sous-types de projets
Un sous-type de projet a beaucoup de puissance pour influencer le comportement du projet, car il est construit comme un agrégateur d’un projet de base. Cette section résume certaines des fonctionnalités qui peuvent être améliorées ou modifiées par les sous-types de projet.

## <a name="features-gained-by-aggregation"></a>Fonctionnalités acquises par l’agrégation
 Le tableau suivant résume un grand nombre des méthodes que l’agrégation permet aux sous-types de projet d’être substituées dans les projets de base.

|Méthodes substituées par l’agrégation|Sous-type de projet|
|---------------------------------------|---------------------|
|À partir de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Permet à un sous-type de projet de<br /><br /> -Modifier la légende et l’icône du nœud de projet.<br />-Remplace complètement l’objet de `Browse` de projet.<br />-Contrôler si le projet peut être renommé.<br />-Contrôle de l’ordre de tri.<br />-Contrôle le contexte utilisateur pour l’aide dynamique.|
|À partir de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permet à un sous-type de projet de contrôler les services contextuels fournis aux concepteurs et aux éditeurs.|
|À partir de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Permet à un sous-type de projet de<br /><br /> -Participez au routage des commandes pour les commandes de projet.<br />-Ajouter, supprimer ou désactiver les commandes ambiantes de projet et Explorateur de solutions les commandes actives.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permet au sous-type de projet de filtrer ce que l’utilisateur voit dans la boîte de dialogue **Ajouter un nouvel élément** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Permet à un sous-type de projet de<br /><br /> -Déterminer le générateur par défaut en fonction d’une extension de fichier.<br />-Mappez un nom de générateur lisible à un objet COM.|

## <a name="properties-used-by-project-subtypes"></a>Propriétés utilisées par les sous-types de projet
 L’environnement et le système de projet de base peuvent utiliser les propriétés de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> et <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> énumérations détaillées dans le tableau suivant pour permettre à un sous-type de projet de contrôler différentes fonctionnalités du système de projet.

|Propriété VSHPROPID|Sous-type de projet|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Permet à un sous-type de projet de contrôler le contenu de la boîte de dialogue **Ajouter un élément** . Le sous-type de projet peut fournir une nouvelle spécification de répertoires de modèles, ajouter de nouveaux genres d’éléments, supprimer des éléments existants et réorganiser un sous-ensemble des éléments dans la boîte de dialogue **Ajouter un élément** du projet de base.|
|`PropertyPagesCLSIDList`|Permet à un sous-type de projet d’ajouter ou de supprimer des pages de propriétés indépendantes de la configuration.|
|`CfgPropertyPagesCLSIDList`|Permet à un sous-type de projet d’ajouter ou de supprimer des pages de propriétés dépendantes de la configuration.|
|`ExtObjectCATID`|Permet à un sous-type de projet de fournir un extendeur Automation pour les objets de projet ou d’élément de projet en connaissant le CATID de l’extendeur. Par exemple, un sous-type de projet peut fournir un objet `Project.Extender("<subtype>")` personnalisé.|
|`BrowseObjectCATID`|Permet à un sous-type de projet de fournir un extendeur Automation pour l’objet `Browse` en connaissant le CATID de l’extendeur. Par exemple, un sous-type de projet peut ajouter des propriétés supplémentaires à la collection <xref:EnvDTE.Project.Properties%2A>.|
|`CfgBrowseObjectCATID`|Permet à un sous-type de projet de fournir un extendeur Automation pour l’objet de recherche de configuration de projet. Par exemple, un sous-type de projet peut ajouter des propriétés supplémentaires à la collection <xref:EnvDTE.Configuration.Properties%2A>.|
|`CfgExtObjectCATID`|Permet à un sous-type de projet de fournir un extendeur Automation pour l’objet de configuration.|
|`DefaultPlatformName`|Permet à un sous-type de projet de déterminer le nom de la plateforme pour les objets de configuration du projet.|

 Le projet de base fournit une implémentation par défaut des propriétés ci-dessus. Le projet de base les obtient en appelant `QueryInterface` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> sur le sous-type de projet le plus à l’extérieur, ce qui permet au sous-type de projet de substituer l’implémentation des propriétés.

## <a name="see-also"></a>Voir aussi
- [Conception de sous-types de projets](../../extensibility/internals/project-subtypes-design.md)