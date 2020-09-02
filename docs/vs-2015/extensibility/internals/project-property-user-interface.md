---
title: Interface utilisateur de la propriété de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31840c40f2a494ffd32f5241e2770938138877e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704097"
---
# <a name="project-property-user-interface"></a>Interface utilisateur des propriétés du projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sous-type de projet peut utiliser les éléments de la boîte de dialogue **pages de propriétés** du projet tels qu’ils sont fournis par le projet de base, masquer ou rendre les contrôles en lecture seule et les pages entières fournis, ou ajouter des pages spécifiques au sous-type de projet dans la boîte de dialogue **pages de propriétés** .  
  
## <a name="extending-the-project-property-dialog-box"></a>Extension de la boîte de dialogue Propriétés du projet  
 Un sous-type de projet implémente des extendeurs Automation et des objets de recherche de configuration de projet. Ces extendeurs implémentent l' <xref:EnvDTE.IFilterProperties> interface pour rendre des propriétés spécifiques masquées ou en lecture seule. La boîte de dialogue **pages de propriétés** du projet de base, implémentée par le projet de base, honore le filtrage effectué par les extendeurs Automation.  
  
 Le processus d’extension d’une boîte de dialogue de **Propriétés de projet** est présenté ci-dessous :  
  
- Le projet de base récupère les extendeurs à partir du sous-type de projet en implémentant l' <xref:EnvDTE80.IInternalExtenderProvider> interface. Les objets parcourir, automatisation de projet et parcourir la configuration de projet du projet de base implémentent tous cette interface.  
  
- L’implémentation de <xref:EnvDTE80.IInternalExtenderProvider> pour l’objet de recherche de projet et l’objet Automation de projet délèguent à l' <xref:EnvDTE80.IInternalExtenderProvider> implémentation de l’agrégation de sous-type de projet (autrement dit, `QueryInterface` pour l’objet de <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projet).  
  
- L’objet de navigation de la configuration de projet de base implémente également <xref:EnvDTE80.IInternalExtenderProvider> pour connecter directement l’extendeur Automation à partir de l’objet de configuration de sous-type de projet. Son implémentation délègue à l' <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée par l’agrégateur de sous-type de projet.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implémenté par l’objet parcourir de la configuration de projet, retourne l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, également implémenté par l’objet parcourir de la configuration de projet, retourne l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objet.  
  
- Un sous-type de projet peut déterminer les CATID appropriés pour les différents objets extensibles du projet de base au moment de l’exécution en extrayant les <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valeurs suivantes :  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  Pour déterminer les CATID de la portée du projet, le sous-type de projet récupère les propriétés ci-dessus pour <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>  à partir de `VSITEMID``typedef` . Un sous-type de projet peut également contrôler les pages de la boîte de dialogue **pages de propriétés** qui s’affichent pour le projet, à la fois dépendant de la configuration et configuration indépendante. Certains sous-types de projet doivent peut-être supprimer des pages intégrées et ajouter des pages spécifiques de sous-type de projet. Pour ce faire, le projet client managé appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> méthode pour les propriétés suivantes :  
  
- `VSHPROPID_PropertyPagesCLSIDList` : liste délimitée par des points-virgules des CLSID des pages de propriétés indépendantes de la configuration.  
  
- `VSHPROPID_CfgPropertyPagesCLSIDList —` liste délimitée par des points-virgules des CLSID des pages de propriétés dépendantes de la configuration.  
  
  Étant donné que le sous-type de projet agrège l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet, il peut remplacer la définition de ces propriétés pour contrôler les boîtes de dialogue des **pages de propriétés** qui sont affichées. Le sous-type de projet peut récupérer ces propriétés à partir du projet de base interne, puis ajouter ou supprimer des CLSID selon les besoins.  
  
  Les nouvelles pages de propriétés ajoutées par un sous-type de projet sont transmises à un objet de recherche de configuration de projet à partir de l’implémentation de projet de base. Cet objet de recherche de configuration de projet prend en charge les extendeurs Automation. Pour plus d’informations sur AutomationExtenders, consultez [implémentation et utilisation d’extendeurs Automation](https://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356). Les pages de propriétés implémentées par le sous-type de projet appellent <xref:EnvDTE.Project.Extender%2A> pour récupérer leur propre objet de recherche de configuration de sous-type de projet qui étend l’objet de recherche de configuration du projet de base.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:EnvDTE.IFilterProperties>   
 [Pages de propriétés (boîte de dialogue)](https://msdn.microsoft.com/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
