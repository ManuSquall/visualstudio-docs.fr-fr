---
title: Extension du modèle objet du projet de Base | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e746ce8bf6d109d4cd1d96c531f30106f20d9c07
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882466"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Étendre le modèle d’objet du projet de base

Un sous-type de projet peut-être étendre le modèle d’objet automation de projet de base aux emplacements suivants :

-   Project.Extender («\<ProjectSubtypeName > ») : Cela permet un sous-type de projet offrir un objet avec des méthodes personnalisées à partir de la <xref:EnvDTE.Project> objet. Un sous-type de projet permettre utiliser des extendeurs Automation pour exposer le `Project` objet. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal doit offrir son objet pour le `VSHPROPID_ExtObjectCATID` à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondant à un `itemid` valeur [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender («\<ProjectSubtypeName > ») : Cela permet un sous-type de projet offrir un objet avec des méthodes personnalisées à partir d’un particulier <xref:EnvDTE.ProjectItem> objet au sein du projet. Un sous-type de projet permettre utiliser des extendeurs automation pour exposer cet objet. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal doit offrir son objet pour le `VSHPROPID_ExtObjectCATID` à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondant à un souhaitée <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties : Cette collection expose les propriétés indépendantes de la configuration de la `Project` objet. Pour plus d’informations sur les propriétés `Project`, consultez <xref:EnvDTE.Project.Properties%2A>. Un sous-type de projet pouvez utiliser des extendeurs Automation pour ajouter ses propriétés à cette collection. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal doit offrir son objet pour le `VSHPROPID_BrowseObjectCATID` à partir de VSHPROPID2 (correspondant à un `itemid` valeur [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties : Cette collection expose les propriétés dépendantes de la configuration du projet pour une configuration particulière (par exemple, le débogage). Pour plus d'informations, consultez <xref:EnvDTE.Configuration>. Un sous-type de projet pouvez utiliser des extendeurs Automation pour ajouter ses propriétés à cette collection. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal offre son objet pour le CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondant à un `itemid` valeur [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interface est utilisée pour distinguer un objet de recherche de configuration d’un autre.

## <a name="see-also"></a>Voir aussi

<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>