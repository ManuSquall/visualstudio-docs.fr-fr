---
title: "Interface utilisateur des propriétés de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>Interface utilisateur de propriétés du projet
Un sous-type de projet permettre utiliser les éléments dans le projet **Pages de propriétés** boîte de dialogue tels qu’ils sont fournis par le projet de base, masquer ou rendre les contrôles en lecture seule et des pages entières fourni ou ajoutez des pages sous-type de projet pour le **Pages de propriétés** boîte de dialogue.  
  
## <a name="extending-the-project-property-dialog-box"></a>Extension de la boîte de dialogue des propriétés de projet  
 Un sous-type de projet implémente des objets de parcourir de configuration de projet et des extendeurs automation. Ces extensions implémentent le <xref:EnvDTE.IFilterProperties>interface pour rendre certaines propriétés en lecture seule ou masqué.</xref:EnvDTE.IFilterProperties> Le **Pages de propriétés** boîte de dialogue du projet de base, implémenté par le projet de base, respecte le filtrage effectuées par les extendeurs Automation.  
  
 Le processus d’extension un **propriété du projet** boîte de dialogue est décrite ci-dessous :  
  
-   Le projet de base extrait les extendeurs à partir du sous-type de projet en implémentant le <xref:EnvDTE80.IInternalExtenderProvider>interface.</xref:EnvDTE80.IInternalExtenderProvider> Parcourir, automation de projet, les objets de parcourir de configuration de projet du projet base toutes les implémentent cette interface.  
  
-   L’implémentation de <xref:EnvDTE80.IInternalExtenderProvider>pour l’objet projet et l’objet d’automation de projet déléguer à la <xref:EnvDTE80.IInternalExtenderProvider>implémentation de l’agrégation de sous-type de projet (autrement dit, ils `QueryInterface` pour <xref:EnvDTE80.IInternalExtenderProvider>sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objet project).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   L’objet configuration projet de base implémente également <xref:EnvDTE80.IInternalExtenderProvider>afin d’associer directement dans l’extendeur Automation à partir de l’objet de configuration de projet sous-type.</xref:EnvDTE80.IInternalExtenderProvider> Son implémentation délègue à la <xref:EnvDTE80.IInternalExtenderProvider>interface implémentée par l’agrégation de sous-type de projet.</xref:EnvDTE80.IInternalExtenderProvider>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implémentée par l’objet Parcourir configuration project, retourne le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objet.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, également implémentée par l’objet Parcourir configuration project, retourne le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>objet.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   Un sous-type de projet peut déterminer le CATID approprié pour les divers objets extensibles du projet de base lors de l’exécution en récupérant suit <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>valeurs :</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Pour déterminer le CATID pour l’étendue du projet, le sous-type de projet extrait les propriétés ci-dessus pour <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>à partir de la `VSITEMID``typedef`.</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> Un sous-type de projet peut également contrôler les **Pages de propriétés** pages de boîte de dialogue sont affichent pour le projet, configuration dépendante et indépendantes de la configuration. Certains sous-types de projets peut-être supprimer les pages intégrées et ajouter des pages spécifiques de sous-type de projet. Pour activer cette option, le projet de client géré appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>méthode pour les propriétés suivantes :</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`: une liste délimitée par des points-virgules des CLSID des pages de propriétés de configuration indépendants.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`liste délimitée par des points-virgules des CLSID des pages de propriétés de dépend de la configuration.  
  
 Étant donné que le projet de sous-type agrégats le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>de l’objet, il peut remplacer la définition de ces propriétés permettant de contrôler **Pages de propriétés** boîtes de dialogue sont affichées.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Le sous-type de projet permettre extraire ces propriétés à partir du projet de base interne et puis ajoutez ou supprimez des CLSID en fonction des besoins.  
  
 Nouvelles pages de propriétés ajoutées par un sous-type de projet sont transmis à un objet de parcourir de configuration de projet à partir de l’implémentation d’un projet de base. Cet objet de parcourir de configuration de projet prend en charge les extendeurs Automation. Pour plus d’informations sur AutomationExtenders, consultez [implémentation et utilisation des extendeurs Automation](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Les pages de propriétés implémentées par l’appel de sous-type de projet <xref:EnvDTE.Project.Extender%2A>pour récupérer leur propres objet Parcourir configuration sous-type projet qui étend l’objet configuration du projet de base.</xref:EnvDTE.Project.Extender%2A>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [Boîte de dialogue Pages de propriétés](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
