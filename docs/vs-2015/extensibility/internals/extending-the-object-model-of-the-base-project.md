---
title: Extension du modèle objet du projet de base | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187166"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Extension du modèle d’objet du projet de base
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sous-type de projet peut étendre le modèle objet Automation du projet de base aux emplacements suivants :  
  
- Project. Extender (" \<ProjectSubtypeName> ") : permet à un sous-type de projet d’offrir un objet avec des méthodes personnalisées à partir de <xref:EnvDTE.Project> . Un sous-type de projet peut utiliser des extendeurs Automation pour exposer l' `Project` objet. L' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégation de sous-type de projet principal doit proposer son objet pour le `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondant à une `itemid` valeur de VSITEMID_ROOT, de `VSITEMID` ) CATID.  
  
- ProjectItem. extendeur (" \<ProjectSubtypeName> ") : permet à un sous-type de projet d’offrir un objet avec des méthodes personnalisées à partir d’un <xref:EnvDTE.ProjectItem> objet particulier dans le projet. Un sous-type de projet peut utiliser des extendeurs Automation pour exposer cet objet. L' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégateur de sous-type de projet principal doit proposer son objet pour le `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondant au `VSITEMID` CATID souhaité).  
  
- Project. Properties : cette collection expose les propriétés indépendantes de la configuration de l' `Project` objet. Pour plus d’informations sur les propriétés de projet, consultez <xref:EnvDTE.Project.Properties%2A> . Un sous-type de projet peut utiliser des extendeurs Automation pour ajouter ses propriétés à cette collection. L' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégateur de sous-type de projet principal doit proposer son objet pour le `VSHPROPID_BrowseObjectCATID` à partir de VSHPROPID2 (correspondant à une `itemid` valeur de VSITEMID_ROOT, de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ) CATID.  
  
- Configuration. Properties : cette collection expose les propriétés dépendantes de la configuration du projet pour une configuration particulière (par exemple, Debug). Pour plus d’informations, consultez <xref:EnvDTE.Configuration>. Un sous-type de projet peut utiliser des extendeurs Automation pour ajouter ses propriétés à cette collection. L' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée sur l’agrégateur de sous-type de projet principal offre son objet pour le CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondant à une `itemid` valeur de <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ). L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interface est utilisée pour distinguer un objet de navigation de configuration d’un autre.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
