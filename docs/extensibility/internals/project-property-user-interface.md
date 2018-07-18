---
title: Interface utilisateur des propriétés de projet | Documents Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 788107666f8103a77753b93fa7c1febc73f9b97f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132425"
---
# <a name="project-property-user-interface"></a>Interface d’utilisateur de propriétés de projet
Un sous-type de projet permettre utiliser les éléments dans le projet **Pages de propriétés** boîte de dialogue comme ils sont fournis par le projet de base, masquer rendre des contrôles en lecture seule et des pages entières fournie ou ajouter des pages spécifiques au sous-type de projet à la **Pages de propriétés** boîte de dialogue.

## <a name="extending-the-project-property-dialog-box"></a>Extension de la boîte de dialogue des propriétés de projet
 Un sous-type de projet implémente extendeurs automation et les objets de parcourir de configuration de projet. Ces extensions implémentent le <xref:EnvDTE.IFilterProperties> interface pour rendre des propriétés en lecture seule ou masqué. Le **Pages de propriétés** boîte de dialogue du projet de base, implémenté par le projet de base, respecte le filtrage effectuées par les extendeurs Automation.

 Le processus d’extension un **propriété du projet** boîte de dialogue est décrit ci-dessous :

-   Le projet de base extrait les extendeurs à partir du sous-type de projet en implémentant le <xref:EnvDTE80.IInternalExtenderProvider> interface. Le parcourir, d’automatisation de projet et des objets de parcourir de configuration de projet du projet de base tous les implémentent cette interface.

-   L’implémentation de <xref:EnvDTE80.IInternalExtenderProvider> pour l’objet projet et l’objet automation de projet déléguer à la <xref:EnvDTE80.IInternalExtenderProvider> implémentation de l’agrégation de sous-type de projet (autrement dit, ils `QueryInterface` pour <xref:EnvDTE80.IInternalExtenderProvider> sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet de projet).

-   L’objet configuration projet de base implémente également <xref:EnvDTE80.IInternalExtenderProvider> associer directement dans l’extendeur Automation à partir de l’objet de configuration de sous-type de projet. Son implémentation délègue à la <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée par l’agrégation de sous-type de projet.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implémentée par l’objet de parcourir des configuration de projet, retourne le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, également implémentée par l’objet de parcourir des configuration de projet, renvoie la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objet.

-   Un sous-type de projet peut déterminer le CATID approprié pour les divers objets extensibles du projet de base lors de l’exécution en récupérant les éléments suivants <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valeurs :

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

Pour déterminer le CATID d’extendeurs pour la portée du projet, le sous-type de projet récupère les propriétés ci-dessus pour [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) à partir de la `VSITEMID typedef`. Un sous-type de projet peut également contrôler les **Pages de propriétés** pages des boîtes de dialogue sont affichés pour le projet, configuration dépendante et indépendantes de la configuration. Certains sous-types de projet devrez peut-être supprimer les pages intégrés et ajoutez des pages spécifiques de sous-type de projet. Pour activer cette option, les appels de projet client géré le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> méthode pour les propriétés suivantes :

-   `VSHPROPID_PropertyPagesCLSIDList` : une liste délimitée par des points-virgules des CLSID des pages de propriétés de configuration indépendant.

-   `VSHPROPID_CfgPropertyPagesCLSIDList —` une liste délimitée par des points-virgules de CLSID des pages de propriétés de dépend de la configuration.

Étant donné que le projet de sous-type agrégats le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de l’objet, il peut remplacer la définition de ces propriétés pour contrôler ce qui **Pages de propriétés** boîtes de dialogue sont affichés. Le sous-type de projet permettre récupérer ces propriétés à partir du projet de base interne et puis ajoutez ou supprimez des CLSID selon les besoins.

Nouvelles pages de propriétés ajoutées par un sous-type de projet sont remis à un objet de parcourir de configuration de projet à partir de l’implémentation d’un projet de base. Cet objet de parcourir de configuration de projet prend en charge les extendeurs Automation. Pour plus d’informations sur AutomationExtenders, consultez [implémentation et à l’aide des extendeurs Automation](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Les pages de propriétés implémentées par l’appel de sous-type de projet <xref:EnvDTE.Project.Extender%2A> pour récupérer leur propre projet sous-type configuration objet qui étend l’objet du projet de base de configuration.

## <a name="see-also"></a>Voir aussi

- <xref:EnvDTE.IFilterProperties>
- [Boîte de dialogue Pages de propriétés](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)