---
title: "Extension du modèle d’objet du projet de Base | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 44bb1eebecbec036572a9bb8857c87db8e4e4817
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-object-model-of-the-base-project"></a>Extension du modèle d’objet du projet de Base
Un sous-type de projet peut-être étendre le modèle d’objet automation de projet de base aux emplacements suivants :  
  
-   Project.Extender («\<ProjectSubtypeName > »)-Cela permet un sous-type de projet permet d’offrir un objet avec des méthodes personnalisées à partir de la <xref:EnvDTE.Project>. Un sous-type de projet peut utiliser des extendeurs Automation pour exposer le `Project` objet. Le <xref:EnvDTE80.IInternalExtenderProvider>interface implémentée dans l’agrégation de sous-type du projet principal doit proposer son objet pour le `VSHPROPID_ExtObjectCATID` à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondant à un `itemid` valeur VSITEMID_ROOT, à partir de `VSITEMID`) CATID.  
  
-   ProjectItem.Extender («\<ProjectSubtypeName > »)-Cela permet un sous-type de projet permet d’offrir un objet avec des méthodes personnalisées provenant d’un <xref:EnvDTE.ProjectItem> objet au sein du projet. Un sous-type de projet peut utiliser des extendeurs Automation pour exposer cet objet. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée dans l’agrégation de sous-type du projet principal doit offrir son objet pour le `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondant à un souhaitée `VSITEMID`) CATID.  
  
-   Project.Properties - cette collection expose les propriétés indépendantes de la configuration de la `Project` objet. Pour plus d’informations sur les propriétés de projet, consultez <xref:EnvDTE.Project.Properties%2A>. Un sous-type de projet permettre utiliser extendeurs Automation pour ajouter ses propriétés à cette collection. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée dans l’agrégation de sous-type du projet principal doit offrir son objet pour le `VSHPROPID_BrowseObjectCATID` de VSHPROPID2 (correspondant à un `itemid` valeur VSITEMID_ROOT, à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties - cette collection expose les propriétés dépendantes de la configuration du projet pour une configuration particulière (par exemple, Debug). Pour plus d’informations, consultez <xref:EnvDTE.Configuration>. Un sous-type de projet permettre utiliser extendeurs Automation pour ajouter ses propriétés à cette collection. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée dans l’agrégation de sous-type de projet principal offre son objet pour le CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondant à un `itemid` valeur <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>). Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interface est utilisée pour distinguer un objet de recherche de configuration d’un autre.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>