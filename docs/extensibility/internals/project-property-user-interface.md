---
title: Interface utilisateur des propriétés de projet | Microsoft Docs
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
ms.openlocfilehash: 4fdaeb87966f051c134d7c2d2354c0f5a3e725da
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495854"
---
# <a name="project-property-user-interface"></a>Interface utilisateur des propriétés du projet
Un sous-type de projet permettre utiliser les éléments dans le projet **Pages de propriétés** boîte de dialogue comme ils sont fournis par le projet de base, masquer ou rendre les contrôles en lecture seule et des pages entières tel que fourni ou ajouter des pages spécifiques au sous-type de projet à la **Pages de propriétés** boîte de dialogue.

## <a name="extending-the-project-property-dialog-box"></a>Extension de la boîte de dialogue des propriétés de projet
 Un sous-type de projet implémente les objets de parcourir de configuration de projet et des extendeurs automation. Ces extensions implémentent le <xref:EnvDTE.IFilterProperties> interface pour rendre des propriétés particulières masqué ou en lecture seule. Le **Pages de propriétés** boîte de dialogue du projet de base, implémenté par le projet de base, respecte le filtrage effectué par les extendeurs Automation.

 Le processus d’extension un **propriété du projet** boîte de dialogue est décrites ci-dessous :

-   Le projet de base extrait les extendeurs à partir du sous-type de projet en implémentant le <xref:EnvDTE80.IInternalExtenderProvider> interface. Parcourir, automation de projet, les objets de parcourir de configuration de projet du projet de base toutes les implémentent cette interface.

-   L’implémentation de <xref:EnvDTE80.IInternalExtenderProvider> pour l’objet de recherche de projet et de l’objet d’automation de projet déléguée à la <xref:EnvDTE80.IInternalExtenderProvider> implémentation de l’agrégateur de sous-type de projet (autrement dit, ils `QueryInterface` pour <xref:EnvDTE80.IInternalExtenderProvider> sur le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet de projet).

-   L’objet de recherche de configuration de projet de base implémente également <xref:EnvDTE80.IInternalExtenderProvider> afin d’associer directement dans l’extendeur d’Automation à partir de l’objet de configuration de sous-type de projet. Son implémentation délègue à la <xref:EnvDTE80.IInternalExtenderProvider> interface implémentée par l’agrégation de sous-type de projet.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implémentée par l’objet de recherche de configuration projet, retourne le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, également implémentée par l’objet de recherche de configuration projet, retourne le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objet.

-   Un sous-type de projet peut déterminer le CATID approprié pour les divers objets extensibles du projet de base lors de l’exécution en récupérant les éléments suivants <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valeurs :

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

Pour déterminer le CATID de la portée du projet, le sous-type de projet récupère les propriétés ci-dessus pour [VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) à partir de la `VSITEMID typedef`. Un sous-type de projet peut également contrôler les **Pages de propriétés** pages des boîtes de dialogue sont affichées pour le projet, configuration dépendante et indépendantes de la configuration. Certains sous-types de projet peut-être supprimer les pages intégrées et ajouter des pages spécifiques de sous-type de projet. Pour permettre cela, le projet de client managé appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> méthode pour les propriétés suivantes :

-   `VSHPROPID_PropertyPagesCLSIDList` : une liste délimitée par des points-virgules des CLSID des pages de propriétés indépendantes de la configuration.

-   `VSHPROPID_CfgPropertyPagesCLSIDList —` une liste délimitée par des points-virgules des CLSID des pages de propriétés dépendantes de la configuration.

Étant donné que les agrégats de sous-type de projet la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de l’objet, il peut remplacer la définition de ces propriétés permettant de contrôler **Pages de propriétés** boîtes de dialogue sont affichées. Le sous-type de projet permettre extraire ces propriétés à partir du projet de base interne et puis ajoutez ou supprimez des CLSID en fonction des besoins.

Nouvelles pages de propriétés ajoutées par un sous-type de projet sont transmis à un objet de recherche de configuration de projet à partir de l’implémentation de projet de base. Cet objet de recherche de configuration de projet prend en charge des extendeurs Automation. Pour plus d’informations sur AutomationExtenders, consultez [implémentation et à l’aide des extendeurs Automation](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Les pages de propriétés implémentées par l’appel de sous-type de projet <xref:EnvDTE.Project.Extender%2A> pour récupérer leur propre objet de recherche de projet sous-type configuration qui étend l’objet de recherche de configuration du projet de base.

## <a name="see-also"></a>Voir aussi

- <xref:EnvDTE.IFilterProperties>
- [Boîte de dialogue Pages de propriétés](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))