---
title: Élargir le modèle d’objet du projet de base (fr) Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708395"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Étendre le modèle objet du projet de base

Un sous-type de projet peut étendre le modèle d’objet d’automatisation du projet de base dans les endroits suivants :

- Project.Extender ("\<ProjectSubtypeName>"): Cela permet à un sous-type de projet <xref:EnvDTE.Project> d’offrir un objet avec des méthodes personnalisées de l’objet. Un sous-type de projet peut utiliser `Project` Automation Extenders pour exposer l’objet. <xref:EnvDTE80.IInternalExtenderProvider> L’interface mise en œuvre sur l’agrégateur principal `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> de sous-type de projet devrait offrir son objet pour le de (correspondant à une `itemid` valeur de [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender ("\<ProjectSubtypeName>"): Cela permet à un sous-type de projet <xref:EnvDTE.ProjectItem> d’offrir un objet avec des méthodes personnalisées à partir d’un objet particulier dans le projet. Un sous-type de projet peut utiliser des extensions d’automatisation pour exposer cet objet. L’interface <xref:EnvDTE80.IInternalExtenderProvider> mise en œuvre sur l’agrégateur principal `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> sous-type <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>de projet doit offrir son objet pour le CATID (correspondant à un souhaité).

- Project.Properties: Cette collection expose les propriétés `Project` de l’objet en configuration indépendantes. Pour plus d’informations sur les propriétés `Project`, consultez <xref:EnvDTE.Project.Properties%2A>. Un sous-type de projet peut utiliser Automation Extenders pour ajouter ses propriétés à cette collection. L’interface <xref:EnvDTE80.IInternalExtenderProvider> mise en œuvre sur l’agrégateur principal `VSHPROPID_BrowseObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> sous-type `itemid` de projet doit offrir son objet pour le de (correspondant à une valeur de [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Cette collection expose les propriétés dépendantes de la configuration du projet pour une configuration particulière (par exemple, Debug). Pour plus d’informations, consultez <xref:EnvDTE.Configuration>. Un sous-type de projet peut utiliser Automation Extenders pour ajouter ses propriétés à cette collection. L’interface <xref:EnvDTE80.IInternalExtenderProvider> mise en œuvre sur l’agrégateur principal `VSHPROPID_CfgBrowseObjectCATID` de sous-type de projet offre son objet pour le CATID (correspondant à une `itemid` valeur de [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> est utilisée pour distinguer un objet de navigation de configuration d’un autre.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
