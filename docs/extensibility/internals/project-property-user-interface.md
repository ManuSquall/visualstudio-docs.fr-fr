---
title: Interface utilisateur de propriété de projet (en anglais) Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706394"
---
# <a name="project-property-user-interface"></a>Interface utilisateur des propriétés du projet

Un sous-type de projet peut utiliser les éléments de la boîte de dialogue **des Pages de propriété** du projet au fur et à mesure qu’ils sont fournis par le projet de base, masquer ou faire des contrôles de lecture seulement et des pages entières fournies, ou ajouter des pages de sous-type de projet à la boîte de dialogue des Pages de **propriété.**

## <a name="extending-the-project-property-dialog-box"></a>Extension de la boîte de dialogue immobilière du projet

Un sous-type de projet implémente les extenseurs d’automatisation et la configuration du projet parcourent les objets. Ces extenseurs implémentent l’interface <xref:EnvDTE.IFilterProperties> pour rendre certaines propriétés cachées ou lues uniquement. La boîte de dialogue **Property Pages** du projet de base, mise en œuvre par le projet de base, honore le filtrage effectué par les Extensions d’Automatisation.

Le processus d’extension d’une boîte de dialogue **project Property** est décrit ci-dessous :

- Le projet de base récupère les extenseurs du <xref:EnvDTE80.IInternalExtenderProvider> sous-type du projet en implémentant l’interface. La navigation, l’automatisation du projet et la configuration du projet parcourent les objets du projet de base implémentent toutes cette interface.

- La mise <xref:EnvDTE80.IInternalExtenderProvider> en œuvre de l’objet de <xref:EnvDTE80.IInternalExtenderProvider> navigation du projet et de l’objet d’automatisation du projet déléguer à la mise en œuvre de l’agrégateur de sous-type de projet (c’est-à-dire qu’ils `QueryInterface` sont destinés <xref:EnvDTE80.IInternalExtenderProvider> à l’objet du <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projet).

- L’objet de navigation de <xref:EnvDTE80.IInternalExtenderProvider> configuration du projet de base implémente également directement le fil dans l’extension d’automatisation de l’objet de configuration de sous-type de projet. Sa mise en <xref:EnvDTE80.IInternalExtenderProvider> œuvre délidait à l’interface mise en œuvre par l’agrégateur de sous-types du projet.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implémenté par la configuration <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> du projet parcourir l’objet, renvoie l’objet.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, également implémenté par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> configuration du projet parcourir l’objet, renvoie l’objet.

- Un sous-type de projet peut déterminer les CATID appropriés pour les différents objets extensibles du projet de base au moment de la course en récupérant les valeurs suivantes <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> :

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Pour déterminer les CATID pour la portée du projet, le sous-type de projet récupère les propriétés ci-dessus pour [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) de `VSITEMID typedef`la . Un sous-type de projet peut également vouloir contrôler les pages de boîte de dialogue **des Pages de propriété** affichées pour le projet, à la fois dépendante de la configuration et indépendante de configuration. Certains sous-types de projet peuvent avoir besoin de supprimer les pages intégrées et d’ajouter des pages spécifiques de sous-type de projet. Pour ce faire, le projet client <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> géré appelle la méthode pour les propriétés suivantes :

- `VSHPROPID_PropertyPagesCLSIDList`— une liste semi-gardiste de CLSID de pages de propriété indépendantes de configuration.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`une liste semi-gardiste des CLSID des pages de propriété dépendantes de la configuration.

Étant donné que le sous-type de projet regroupe l’objet, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> il peut remplacer la définition de ces propriétés pour contrôler les boîtes de dialogue des Pages de **propriété** qui sont affichées. Le sous-type de projet peut récupérer ces propriétés du projet de base interne, puis ajouter ou enlever les CLSID au besoin.

Les nouvelles pages de propriété ajoutées par un sous-type de projet sont remises à un objet de navigation de configuration de projet à partir de la mise en œuvre du projet de base. Cet objet de navigation de configuration de projet prend en charge Automation Extenders. Pour plus d’informations sur AutomationExtenders, voir [Implementing and Using Automation Extenders](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Les pages de propriété mises en <xref:EnvDTE.Project.Extender%2A> œuvre par l’appel de sous-type de projet pour récupérer leur propre configuration de sous-type de projet parcourent l’objet qui étend l’objet de navigation de configuration du projet de base.

## <a name="see-also"></a>Voir aussi

- <xref:EnvDTE.IFilterProperties>
- [Pages de propriété Dialog Box](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
