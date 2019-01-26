---
title: Fourniture de l’automatisation pour VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50d707c42196d727a35ca7c9d9cef250c60f7d5b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018070"
---
# <a name="providing-automation-for-vspackages"></a>Fourniture de l’automatisation pour VSPackages
Il existe deux façons de fournir l’automatisation pour vos VSPackages : en implémentant des objets VSPackage spécifiques et en implémentant des objets automation standard. En règle générale, ils sont utilisés ensemble pour étendre le modèle automation de l’environnement.  
  
## <a name="vspackage-specific-objects"></a>Objets VSPackage spécifiques  
 Certains endroits dans le modèle automation vous obligent à fournir des objets automation qui sont uniques à votre VSPackage. Par exemple, les nouveaux projets nécessitent des objets distincts qui fournit uniquement votre VSPackage. Les noms de ces objets sont entrés dans le Registre et obtenus via des appels à l’environnement `DTE` objet.  
  
 Objets spécifiques à VSPackage peuvent également être obtenus lorsqu’un utilisateur d’automation utilise l’objet fourni via la propriété de l’objet d’un objet standard. Par exemple, la norme `Window` objet possède un `Object` propriété, couramment appelée le `Windows.Object` propriété. Lorsque les consommateurs appeler le `Window.Object` sur une fenêtre est implémentée dans votre VSPackage, vous transmettez un objet automation spécifique de votre propre conception.  
  
#### <a name="projects"></a>Projets  
 Les VSPackages peuvent étendre le modèle automation pour les nouveaux types de projet via leurs propres objets VSPackage spécifique. L’objectif principal de fournir de nouveaux objets automation pour votre VSPackage consiste à différencier votre projet unique des objets à partir d’un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> ou un <xref:VSLangProj80.VSProject2> objet. Cette distinction est pratique lorsque vous souhaitez fournir un moyen unique ou effectuer une itération de votre type de projet en dehors d’autres types de projets, doivent, ils apparaissent côte à côte dans une solution. Pour plus d’informations, consultez [exposer des objets de projet](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Événements  
 L’architecture des événements de l’environnement offre un autre emplacement, vous pouvez ajouter vos propres objets VSPackage spécifique. Par exemple, en créant vos propres objets événement unique, vous pouvez étendre le modèle d’événement de l’environnement pour les projets. Vous souhaiterez peut-être fournir vos propres événements lorsqu’un nouvel élément est ajouté à votre propre type de projet. Pour plus d’informations, consultez [exposer des événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Objets fenêtres  
 Windows peut transmettre un objet d’automation de VSPackage spécifique à l’environnement lorsqu’elle est appelée. Vous implémentez un objet qui est dérivé de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> ou `IDispatch` qui transmet dans Propriétés, extension de l’objet de fenêtre dans laquelle il est placé. Par exemple, vous pouvez utiliser cette approche pour fournir l’automatisation pour un contrôle que doit se trouver dans un frame de fenêtre. La sémantique de cet objet et tous les objets qu’il peut étendre est à votre disposition pour concevoir. Pour plus d'informations, voir [Procédure : Fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Pages d’options dans le menu Outils  
 Vous pouvez créer des pages pour étendre les outils, le modèle automation de Options via l’implémentation de pages et en ajoutant des informations dans le Registre pour créer vos propres options. Vos pages peuvent ensuite être appelées via le modèle objet d’environnement telles que toutes les autres pages options. Si la conception de la fonctionnalité que vous ajoutez à l’environnement via les VSPackages exige que les pages d’options, vous devez ajouter la prise en charge automation. Pour plus d’informations, consultez [prise en charge d’Automation pour les Pages Options](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Objets Automation standard  
 Pour étendre l’automatisation pour les projets, vous implémentez également des objets automation standard (dérivée de `IDispatch`) qui veille à côté des autres objets de projet et implémenter les méthodes et propriétés standard. Les objets de projet qui sont insérées dans la hiérarchie de solution, tels que des exemples d’objets standards `Projects`, `Project`, `ProjectItem`, et `ProjectItems`. Chaque nouveau type de projet doit implémenter ces objets (et éventuellement d’autres en fonction de la sémantique de votre projet).  
  
 Dans un sens, ces objets fournissent l’opposé avantage des objets de projet VSPackage spécifique. Les objets automation standard permettent à votre projet à utiliser de façon généralisée comme n’importe quel autre projet prenant en charge les mêmes objets. Par conséquent, un complément qui est écrit sur Général `Project` et `ProjectItem` objets peuvent fonctionner par rapport à des projets de n’importe quel type. Pour plus d’informations, consultez [projet de modélisation](../../extensibility/internals/project-modeling.md).