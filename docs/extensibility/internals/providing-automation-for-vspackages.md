---
title: Grâce à l’automatisation de VSPackages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5f3393443e41c9bd99a8890b53bedae006d7a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131570"
---
# <a name="providing-automation-for-vspackages"></a>Grâce à l’automatisation de VSPackages
Il existe deux façons de fournir l’automatisation vos VSPackages : mise en œuvre des objets spécifiques au VSPackage et en implémentant des objets automation standard. En règle générale, ils sont utilisés ensemble pour étendre le modèle automation de l’environnement.  
  
## <a name="vspackage-specific-objects"></a>Objets VSPackage spécifiques  
 Certains endroits dans le modèle automation, vous devez fournir des objets automation qui sont uniques à votre VSPackage. Par exemple, les nouveaux projets nécessitent des objets distincts qui uniquement votre VSPackage fournit. Les noms de ces objets sont entrés dans le Registre et obtenues via des appels de l’environnement `DTE` objet.  
  
 Objets VSPackage spécifiques peuvent également être obtenues quand un consommateur automation utilise l’objet fourni via la propriété de l’objet d’un objet standard. Par exemple, la norme `Window` objet a un `Object` propriété, communément appelée le `Windows.Object` propriété. Lorsque les consommateurs appeler le `Window.Object` sur une fenêtre est implémentée dans votre package Visual Studio, vous passez un objet automation spécifique de votre propre conception.  
  
#### <a name="projects"></a>Projets  
 VSPackages peuvent étendre le modèle automation pour les nouveaux types de projet via leurs propres objets VSPackage spécifiques. Le principal objectif de fournir de nouveaux objets automation pour votre VSPackage est différencier votre projet unique des objets d’un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> ou un <xref:VSLangProj80.VSProject2> objet. Cette distinction est utile lorsque vous souhaitez fournir un moyen d’isoler ou itérer au sein de votre type de projet indépendamment des autres types de projet doivent, ils apparaissent côte à côte dans une solution. Pour plus d’informations, consultez [exposer des objets du projet](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Événements  
 L’architecture des événements de l’environnement offre un autre emplacement, vous pouvez ajouter vos propres objets VSPackage spécifiques. Par exemple, en créant vos propres objets événement unique, vous pouvez étendre le modèle d’événement de l’environnement pour les projets. Vous souhaiterez peut-être fournir vos propres événements lorsqu’un nouvel élément est ajouté à votre propre type de projet. Pour plus d’informations, consultez [exposant les événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Objets fenêtres  
 Windows peut retourner un objet automation de VSPackage spécifiques à l’environnement lorsqu’elle est appelée. Vous implémentez un objet qui est dérivé de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> ou `IDispatch` qui remet dans Propriétés, extension de l’objet de fenêtre dans laquelle il est placé. Par exemple, vous pouvez utiliser cette approche pour fournir l’automatisation pour un contrôle placé dans un frame de fenêtre. La sémantique de cet objet et les autres objets qu’il peut augmenter l’est pour concevoir le vôtre. Pour plus d’informations, consultez [Comment : fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Pages d’options dans le menu Outils  
 Vous pouvez créer des pages pour étendre les outils, le modèle automation de Options via l’implémentation des pages et en ajoutant des informations au Registre afin de créer vos propres options. Vos pages peuvent ensuite être appelées par le biais du modèle objet d’environnement telles que toutes les autres pages d’options. Si la conception de la fonctionnalité que vous ajoutez à l’environnement via les VSPackages exige que les pages d’options, vous devez ajouter la prise en charge automation. Pour plus d’informations, consultez [prise en charge d’Automation pour les Pages d’Options](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Objets Automation standard  
 Pour étendre l’automatisation pour les projets, vous implémentez également des objets automation standard (dérivée de `IDispatch`) qui se trouvent à côté des autres objets du projet et implémenter les méthodes et propriétés standard. Les objets du projet sont insérées dans la hiérarchie de la solution, tels que des exemples d’objets standards `Projects`, `Project`, `ProjectItem`, et `ProjectItems`. Chaque nouveau type de projet doit implémenter ces objets (et éventuellement d’autres en fonction de la sémantique de votre projet).  
  
 Dans un sens, ces objets fournissent l’opposé avantage des objets de projet VSPackage spécifiques. Les objets automation standard permettent à votre projet à utiliser dans une méthode généralisée comme n’importe quel autre projet prenant en charge les mêmes objets. Par conséquent, un complément qui est écrit sur Général `Project` et `ProjectItem` objets peuvent fonctionner sur des projets de tout type. Pour plus d’informations, consultez [projet de modélisation](../../extensibility/internals/project-modeling.md).