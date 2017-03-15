---
title: "Grâce à l’automatisation pour les VSPackages | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 15
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ca3700d1e26ccd4be1054463e9426b364ba17301
ms.lasthandoff: 02/22/2017

---
# <a name="providing-automation-for-vspackages"></a>Grâce à l’automatisation pour les packages VS
Il existe deux façons de fournir l’automatisation pour vos packages VS : mise en œuvre des objets VSPackage spécifiques et en implémentant des objets automation standard. En général, elles sont utilisées ensemble pour étendre le modèle automation de l’environnement.  
  
## <a name="vspackage-specific-objects"></a>Objets VSPackage spécifiques  
 Certains endroits dans le modèle automation vous demandent de fournir des objets automation qui sont uniques à votre package VS. Par exemple, des projets nécessitent des objets distincts qui fournit uniquement votre VSPackage. Les noms de ces objets sont entrés dans le Registre et obtenues via des appels à l’environnement `DTE` objet.  
  
 Objets VSPackage spécifiques peuvent également être obtenues lorsqu’un client automation utilise l’objet fourni par la propriété de l’objet d’un objet standard. Par exemple, la norme `Window` objet a un `Object` propriété, couramment appelée le `Windows.Object` propriété. Lorsque les consommateurs appeler le `Window.Object` dans une fenêtre est implémentée dans votre VSPackage, vous passez un objet automation spécifique de votre propre conception.  
  
#### <a name="projects"></a>Projets  
 Les VSPackages peuvent étendre le modèle automation pour les nouveaux types de projet via leurs propres objets VSPackage spécifiques. Le principal objectif de fournir de nouveaux objets automation pour votre VSPackage est de différencier votre projet unique des objets d’un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>ou un <xref:VSLangProj80.VSProject2>objet.</xref:VSLangProj80.VSProject2> </xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> Cette distinction est utile lorsque vous souhaitez fournir un moyen d’isoler ou itérer au sein de votre type de projet indépendamment des autres types de projet doivent, ils apparaissent côte à côte dans une solution. Pour plus d’informations, consultez [exposer des objets de projet](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Événements  
 L’architecture des événements de l’environnement offre un autre emplacement, vous pouvez ajouter vos propres objets VSPackage spécifiques. Par exemple, en créant vos propres objets événement unique, vous pouvez étendre le modèle d’événement de l’environnement pour les projets. Vous souhaiterez peut-être fournir vos propres événements lorsqu’un nouvel élément est ajouté à votre propre type de projet. Pour plus d’informations, consultez [exposer des événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Objets fenêtres  
 Windows peut retourner un objet d’automation VSPackage spécifiques à l’environnement lorsqu’elle est appelée. Vous implémentez un objet dérivé de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject>ou `IDispatch` qui remet dans Propriétés, extension de l’objet de fenêtre dans laquelle il est placé.</xref:EnvDTE.IExtensibleObject> </xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> Par exemple, vous pouvez utiliser cette approche pour fournir l’automatisation d’un contrôle que doit se trouver dans un frame de fenêtre. La sémantique de cet objet et d’autres objets qu’il peut étendre appartiennent à la conception. Pour plus d’informations, consultez [Comment : fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Pages d’options dans le menu Outils  
 Vous pouvez créer des pages pour étendre les outils, le modèle d’automatisation Options via l’implémentation de pages et ajout des informations dans le Registre pour créer vos propres options. Vos pages peuvent ensuite être appelées via le modèle objet d’environnement telles que toutes les autres pages d’options. Si la conception de la fonctionnalité que vous ajoutez à l’environnement via les VSPackages requiert que les pages d’options, vous devez ajouter la prise en charge automation. Pour plus d’informations, consultez [prise en charge d’Automation pour les Pages d’Options](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Objets Automation standard  
 Pour étendre l’automatisation pour les projets, vous implémentez également des objets automation standard (dérivée de `IDispatch`) qui se trouvent à côté des autres objets du projet et implémenter les méthodes et propriétés standard. Les objets du projet sont insérées dans la hiérarchie de solution tel que des exemples d’objets standards `Projects`, `Project`, `ProjectItem`, et `ProjectItems`. Chaque nouveau type de projet doit implémenter ces objets (et éventuellement d’autres en fonction de la sémantique de votre projet).  
  
 Dans un sens, ces objets fournissent l’avantage des objets de projet VSPackage spécifiques opposé. Les objets automation standard permettent à votre projet à utiliser dans une méthode généralisée comme n’importe quel autre projet prenant en charge les mêmes objets. Par conséquent, un complément qui est écrit sur Général `Project` et `ProjectItem` objets peuvent fonctionner dans des projets de tout type. Pour plus d’informations, consultez [projet de modélisation](../../extensibility/internals/project-modeling.md).
