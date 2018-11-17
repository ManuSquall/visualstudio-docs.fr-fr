---
title: Extension du modèle objet du projet de Base | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db8ec193b49b7b72e922d2e4f715061d78be37ad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783277"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Extension du modèle d’objet du projet de base
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sous-type de projet peut-être étendre le modèle d’objet automation de projet de base aux emplacements suivants :  
  
-   Project.Extender («\<ProjectSubtypeName > ») : Cela permet un sous-type de projet offrir un objet avec des méthodes personnalisées à partir de la <xref:EnvDTE.Project>. Un sous-type de projet permettre utiliser des extendeurs Automation pour exposer le `Project` objet. Le <xref:EnvDTE80.IInternalExtenderProvider>interface implémentée sur l’agrégation de sous-type de projet principal doit offrir son objet pour le `VSHPROPID_ExtObjectCATID` à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondant à un `itemid` valeur VSITEMID_ROOT, à partir de `VSITEMID`) CATID.  
  
-   ProjectItem.Extender («\<ProjectSubtypeName > ») : Cela permet un sous-type de projet offrir un objet avec des méthodes personnalisées à partir d’un particulier <xref:EnvDTE.ProjectItem> objet au sein du projet. Un sous-type de projet permettre utiliser des extendeurs Automation pour exposer cet objet. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal doit offrir son objet pour le `VSHPROPID_ExtObjectCATID` à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondant à un souhaitée `VSITEMID`) CATID.  
  
-   Project.Properties – cette collection expose les propriétés indépendantes de la configuration de la `Project` objet. Pour plus d’informations sur les propriétés du projet, consultez <xref:EnvDTE.Project.Properties%2A>. Un sous-type de projet pouvez utiliser des extendeurs Automation pour ajouter ses propriétés à cette collection. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal doit offrir son objet pour le `VSHPROPID_BrowseObjectCATID` à partir de VSHPROPID2 (correspondant à un `itemid` valeur VSITEMID_ROOT, à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties – cette collection expose les propriétés dépendantes de la configuration du projet pour une configuration particulière (par exemple, le débogage). Pour plus d’informations, consultez <xref:EnvDTE.Configuration>. Un sous-type de projet pouvez utiliser des extendeurs Automation pour ajouter ses propriétés à cette collection. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal offre son objet pour le CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondant à un `itemid` valeur <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>). Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interface est utilisée pour distinguer un objet de recherche de configuration d’un autre.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>

