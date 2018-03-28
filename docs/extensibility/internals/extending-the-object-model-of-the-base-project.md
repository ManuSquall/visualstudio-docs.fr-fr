---
title: Extension du modèle d’objet du projet de Base | Documents Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a0fdda35744aaddf8789818afd1f938897470147
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="extending-the-object-model-of-the-base-project"></a>Extension du modèle d’objet du projet de Base

Un sous-type de projet peut-être étendre le modèle d’objet automation de projet de base aux emplacements suivants :

-   Project.Extender («\<ProjectSubtypeName > »)-Cela permet un sous-type de projet permet d’offrir un objet avec des méthodes personnalisées à partir de la <xref:EnvDTE.Project>. Un sous-type de projet peut utiliser des extendeurs Automation pour exposer le `Project` objet. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée dans l’agrégation de sous-type du projet principal doit proposer son objet pour le `VSHPROPID_ExtObjectCATID` à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondant à un `itemid` valeur [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender («\<ProjectSubtypeName > »)-Cela permet un sous-type de projet permet d’offrir un objet avec des méthodes personnalisées provenant d’un <xref:EnvDTE.ProjectItem> objet au sein du projet. Un sous-type de projet peut utiliser des extendeurs Automation pour exposer cet objet. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée dans l’agrégation de sous-type du projet principal doit offrir son objet pour le `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondant à un souhaitée <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties - cette collection expose les propriétés indépendantes de la configuration de la `Project` objet. Pour plus d’informations sur les propriétés de projet, consultez <xref:EnvDTE.Project.Properties%2A>. Un sous-type de projet permettre utiliser extendeurs Automation pour ajouter ses propriétés à cette collection. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée dans l’agrégation de sous-type du projet principal doit offrir son objet pour le `VSHPROPID_BrowseObjectCATID` de VSHPROPID2 (correspondant à un `itemid` valeur [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), à partir de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties - cette collection expose les propriétés dépendantes de la configuration du projet pour une configuration particulière (par exemple, Debug). Pour plus d'informations, consultez <xref:EnvDTE.Configuration>. Un sous-type de projet permettre utiliser extendeurs Automation pour ajouter ses propriétés à cette collection. Le <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée dans l’agrégation de sous-type de projet principal offre son objet pour le CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondant à un `itemid` valeur [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interface est utilisée pour distinguer un objet de recherche de configuration d’un autre.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>