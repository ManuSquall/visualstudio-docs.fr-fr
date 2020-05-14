---
title: Propriétés et méthodes étendues par les sous-types de projets Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706196"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propriétés et méthodes étendues par les sous-types de projets
Un sous-type de projet a beaucoup de pouvoir d’influencer le comportement du projet parce qu’il est construit comme un agrégateur d’un projet de base. Cette section résume certaines des fonctionnalités qui peuvent être améliorées ou modifiées par des sous-types de projet.

## <a name="features-gained-by-aggregation"></a>Caractéristiques acquises par Agrégation
 Le tableau suivant résume bon nombre des méthodes selon lesquelles l’agrégation permet aux sous-types de projets de remplacer les projets de base.

|Méthodes annulées par l’agrégation|Projet Subtype|
|---------------------------------------|---------------------|
|De <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Permet à un sous-type de projet de<br /><br /> - Changer de légende et d’icône du nœud de projet.<br />- Passer complètement `Browse` outre l’objet du projet.<br />- Contrôler si le projet peut être renommé.<br />- Commande de tri de contrôle.<br />- Contrôler le contexte utilisateur pour une aide dynamique.|
|De <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permet à un sous-type de projet de contrôler les services contextuels fournis aux concepteurs et aux éditeurs.|
|De <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Permet à un sous-type de projet de<br /><br /> - Participez au tracé de commande pour les commandes de projet.<br />- Ajouter, supprimer ou désactiver les commandes ambiantes du projet et les commandes actives Solution Explorer.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permet au sous-type de projet de filtrer ce que l’utilisateur voit dans la boîte de dialogue **Add New Item.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Permet à un sous-type de projet de<br /><br /> - Déterminer le générateur par défaut donné une extension de fichier.<br />- Carte d’un nom de générateur lisible humain à un objet COM.|

## <a name="properties-used-by-project-subtypes"></a>Propriétés utilisées par les sous-types de projet
 Le système de projet d’environnement <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> et de base peut utiliser les propriétés et les recensements détaillés dans le tableau suivant pour permettre à un sous-type de projet de contrôler diverses caractéristiques du système de projet.

|Propriété VSHPROPID|Projet Subtype|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Permet à un sous-type de projet de contrôler le contenu de la boîte de dialogue **Add Item.** Le sous-type de projet peut fournir une nouvelle spécification des répertoires de modèles, ajouter de nouveaux types d’éléments, supprimer les éléments existants et réorganiser un sous-ensemble des éléments dans la boîte de dialogue **Add Item** du projet de base.|
|`PropertyPagesCLSIDList`|Permet à un sous-type de projet d’ajouter ou de supprimer des pages de propriété indépendantes de configuration.|
|`CfgPropertyPagesCLSIDList`|Permet à un sous-type de projet d’ajouter ou de supprimer les pages de propriété dépendantes de la configuration.|
|`ExtObjectCATID`|Permet à un sous-type de projet de fournir un prolongateur d’automatisation pour le projet ou les objets d’objets d’objets d’objets d’objets d’objets d’objets d’élément de projet en connaissant l’Extension CATID. Par exemple, un sous-type de `Project.Extender("<subtype>")` projet peut fournir un objet personnalisé.|
|`BrowseObjectCATID`|Permet à un sous-type de projet `Browse` de fournir un prolongateur d’automatisation pour l’objet en connaissant l’Extension CATID. Par exemple, un sous-type de projet <xref:EnvDTE.Project.Properties%2A> peut ajouter des propriétés supplémentaires à la collection.|
|`CfgBrowseObjectCATID`|Permet à un sous-type de projet de fournir un prolongateur d’automatisation pour l’objet de navigation de configuration du projet. Par exemple, un sous-type de projet <xref:EnvDTE.Configuration.Properties%2A> peut ajouter des propriétés supplémentaires à la collection.|
|`CfgExtObjectCATID`|Permet à un sous-type de projet de fournir un prolongateur d’automatisation pour l’objet de configuration.|
|`DefaultPlatformName`|Permet à un sous-type de projet de déterminer le nom de la plate-forme pour les objets de configuration du projet.|

 Le projet de base fournit une mise en œuvre par défaut des propriétés ci-dessus. Le projet de base `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> les obtient en appelant sur le sous-type de projet le plus externe, permettant ainsi au sous-type de projet de passer outre à la mise en œuvre des propriétés.

## <a name="see-also"></a>Voir aussi
- [Conception de sous-types de projets](../../extensibility/internals/project-subtypes-design.md)
