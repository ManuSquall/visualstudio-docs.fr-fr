---
title: Interface utilisateur de la propriété de projet | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a83e5c9fb633322da536e62f1ba03484b965b162
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252357"
---
# <a name="project-property-user-interface"></a>Interface utilisateur des propriétés du projet

Un sous-type de projet peut utiliser les éléments de la boîte de dialogue **pages de propriétés** du projet tels qu’ils sont fournis par le projet de base, masquer ou rendre les contrôles en lecture seule et les pages entières fournis, ou ajouter des pages spécifiques au sous-type de projet dans la boîte de dialogue **pages de propriétés** . boîte.

## <a name="extending-the-project-property-dialog-box"></a>Extension de la boîte de dialogue Propriétés du projet

Un sous-type de projet implémente des extendeurs Automation et des objets de recherche de configuration de projet. Ces extendeurs implémentent <xref:EnvDTE.IFilterProperties> l’interface pour rendre des propriétés spécifiques masquées ou en lecture seule. La boîte de dialogue **pages de propriétés** du projet de base, implémentée par le projet de base, honore le filtrage effectué par les extendeurs Automation.

Le processus d’extension d’une boîte de dialogue de **Propriétés de projet** est présenté ci-dessous :

- Le projet de base récupère les extendeurs à partir du sous-type de projet <xref:EnvDTE80.IInternalExtenderProvider> en implémentant l’interface. Les objets parcourir, automatisation de projet et parcourir la configuration de projet du projet de base implémentent tous cette interface.

- L’implémentation de <xref:EnvDTE80.IInternalExtenderProvider> pour l’objet de recherche de projet et l’objet Automation de projet <xref:EnvDTE80.IInternalExtenderProvider> délèguent à l’implémentation de l’agrégation de sous-type `QueryInterface` de <xref:EnvDTE80.IInternalExtenderProvider> projet ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> autrement dit, pour sur le objet de projet).

- L’objet de navigation de la configuration <xref:EnvDTE80.IInternalExtenderProvider> de projet de base implémente également pour connecter directement l’extendeur Automation à partir de l’objet de configuration de sous-type de projet. Son implémentation délègue à <xref:EnvDTE80.IInternalExtenderProvider> l’interface implémentée par l’agrégateur de sous-type de projet.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implémenté par l’objet parcourir de la configuration de projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , retourne l’objet.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, également implémenté par l’objet parcourir de la configuration de projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> , retourne l’objet.

- Un sous-type de projet peut déterminer les CATID appropriés pour les différents objets extensibles du projet de base au moment de l’exécution en extrayant <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> les valeurs suivantes :

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Pour déterminer les CATID de la portée du projet, le sous-type de projet récupère les propriétés ci-dessus pour [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) à partir `VSITEMID typedef`du. Un sous-type de projet peut également contrôler les pages de la boîte de dialogue **pages de propriétés** qui s’affichent pour le projet, à la fois dépendant de la configuration et configuration indépendante. Certains sous-types de projet doivent peut-être supprimer des pages intégrées et ajouter des pages spécifiques de sous-type de projet. Pour ce faire, le projet client managé appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> méthode pour les propriétés suivantes :

- `VSHPROPID_PropertyPagesCLSIDList`: liste délimitée par des points-virgules des CLSID des pages de propriétés indépendantes de la configuration.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`liste délimitée par des points-virgules des CLSID des pages de propriétés dépendantes de la configuration.

Étant donné que le sous-type de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projet agrège l’objet, il peut remplacer la définition de ces propriétés pour contrôler les boîtes de dialogue des **pages de propriétés** qui sont affichées. Le sous-type de projet peut récupérer ces propriétés à partir du projet de base interne, puis ajouter ou supprimer des CLSID selon les besoins.

Les nouvelles pages de propriétés ajoutées par un sous-type de projet sont transmises à un objet de recherche de configuration de projet à partir de l’implémentation de projet de base. Cet objet de recherche de configuration de projet prend en charge les extendeurs Automation. Pour plus d’informations sur AutomationExtenders, consultez [implémentation et utilisation d’extendeurs Automation](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Les pages de propriétés implémentées par le sous- <xref:EnvDTE.Project.Extender%2A> type de projet appellent pour récupérer leur propre objet de recherche de configuration de sous-type de projet qui étend l’objet de recherche de configuration du projet de base.

## <a name="see-also"></a>Voir aussi

- <xref:EnvDTE.IFilterProperties>
- [Pages de propriétés (boîte de dialogue)](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
