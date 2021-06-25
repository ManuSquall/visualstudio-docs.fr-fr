---
title: Extension du modèle objet du projet de base | Microsoft Docs
description: Découvrez comment étendre le modèle objet Automation du projet de base dans Visual Studio à l’aide d’un sous-type de projet.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175571b374c6a54999b212b316301f3f775891ff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899340"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Étendre le modèle objet du projet de base

Un sous-type de projet peut étendre le modèle objet Automation du projet de base aux emplacements suivants :

- Project. extendeur (" \<ProjectSubtypeName> ") : permet à un sous-type de projet d’offrir un objet avec des méthodes personnalisées à partir de l' <xref:EnvDTE.Project> objet. Un sous-type de projet peut utiliser des extendeurs Automation pour exposer l' `Project` objet. L' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal doit proposer son objet pour le `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondant à une `itemid` valeur de [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. extendeur (" \<ProjectSubtypeName> ") : permet à un sous-type de projet d’offrir un objet avec des méthodes personnalisées à partir d’un <xref:EnvDTE.ProjectItem> objet particulier dans le projet. Un sous-type de projet peut utiliser des extendeurs Automation pour exposer cet objet. L' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégateur de sous-type de projet principal doit proposer son objet pour le `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondant au <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> CATID souhaité).

- Project. Properties : cette collection expose les propriétés indépendantes de la configuration de l' `Project` objet. Pour plus d’informations sur les propriétés `Project`, consultez <xref:EnvDTE.Project.Properties%2A>. Un sous-type de projet peut utiliser des extendeurs Automation pour ajouter ses propriétés à cette collection. L' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégateur de sous-type de projet principal doit proposer son objet pour le `VSHPROPID_BrowseObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondant à une `itemid` valeur de [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration. Properties : cette collection expose les propriétés dépendantes de la configuration du projet pour une configuration particulière (par exemple, Debug). Pour plus d’informations, consultez <xref:EnvDTE.Configuration>. Un sous-type de projet peut utiliser des extendeurs Automation pour ajouter ses propriétés à cette collection. L' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégateur de sous-type de projet principal offre son objet pour le CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondant à une `itemid` valeur de [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interface est utilisée pour distinguer un objet de navigation de configuration d’un autre.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
