---
title: Mise à disposition de l’automatisation pour les VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6eb76eba76567f2966323d4058c9e752cb6fb69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200983"
---
# <a name="providing-automation-for-vspackages"></a>Fourniture de l’automatisation pour VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il existe deux méthodes principales pour fournir une automatisation pour vos VSPackages : en implémentant des objets spécifiques au VSPackage et en implémentant des objets Automation Standard. En règle générale, ils sont utilisés ensemble pour étendre le modèle Automation de l’environnement.  
  
## <a name="vspackage-specific-objects"></a>Objets spécifiques au VSPackage  
 Certains emplacements dans le modèle Automation nécessitent que vous fournissiez des objets Automation qui sont uniques à votre VSPackage. Par exemple, les nouveaux projets nécessitent des objets distincts fournis par le VSPackage. Les noms de ces objets sont entrés dans le registre et obtenus par le biais d’appels à l’objet d’environnement `DTE` .  
  
 Vous pouvez également obtenir des objets spécifiques au VSPackage lorsqu’un consommateur Automation utilise l’objet fourni par le biais de la propriété Object d’un objet standard. Par exemple, l' `Window` objet standard a une `Object` propriété, communément connue sous le nom de `Windows.Object` propriété. Lorsque les consommateurs appellent le `Window.Object` sur une fenêtre implémentée dans votre VSPackage, vous transmettez un objet Automation spécifique de votre propre conception.  
  
#### <a name="projects"></a>Projets  
 Les VSPackages peuvent étendre le modèle Automation pour les nouveaux types de projets par le biais de leurs propres objets spécifiques au VSPackage. L’objectif principal de la fourniture de nouveaux objets Automation pour votre VSPackage est de différencier vos objets de projet uniques d’un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> <xref:VSLangProj80.VSProject2> objet ou. Cette différenciation est pratique lorsque vous souhaitez fournir un moyen d’effectuer une simple sortie ou d’itérer le type de projet à partir d’autres types de projets, s’ils apparaissent côte à côte dans une solution. Pour plus d’informations, consultez [exposition des objets de projet](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Événements  
 L’architecture des événements de l’environnement vous permet d’ajouter vos propres objets spécifiques au VSPackage. Par exemple, en créant vos propres objets d’événement uniques, vous pouvez étendre le modèle d’événement de l’environnement pour les projets. Vous souhaiterez peut-être fournir vos propres événements lorsqu’un nouvel élément est ajouté à votre propre type de projet. Pour plus d’informations, consultez [exposition des événements](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Objets fenêtres  
 Windows peut retourner un objet Automation spécifique au VSPackage dans l’environnement lorsqu’il est appelé. Vous implémentez un objet dérivé de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> , <xref:EnvDTE.IExtensibleObject> ou `IDispatch` qui transmet des propriétés en étendant l’objet de fenêtre dans lequel il est sur site. Par exemple, vous pouvez utiliser cette approche pour fournir une automatisation pour un contrôle dans un cadre de fenêtre. La sémantique de cet objet et de tous les autres objets qu’il peut étendre vous permet de concevoir. Pour plus d’informations, consultez [Comment : fournir une automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Pages Options du menu outils  
 Vous pouvez créer des pages pour étendre les outils, le modèle Automation options via l’implémentation des pages et l’ajout d’informations au registre pour créer vos propres options. Vos pages peuvent ensuite être appelées par le biais du modèle objet d’environnement comme toutes les autres pages d’options. Si la conception de la fonctionnalité que vous ajoutez à l’environnement par le biais de VSPackages requiert des pages d’options, vous devez également ajouter la prise en charge de l’automatisation. Pour plus d’informations, consultez [prise en charge d’Automation pour les pages d’options](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Objets Automation Standard  
 Pour étendre l’Automation pour les projets, vous implémentez également des objets Automation Standard (dérivés de `IDispatch` ) qui se trouvent en regard des autres objets de projet et implémentent des méthodes et des propriétés standard. Parmi les exemples d’objets standard, citons les objets de projet insérés dans la hiérarchie de la solution, tels que `Projects` ,, `Project` `ProjectItem` et `ProjectItems` . Chaque nouveau type de projet doit implémenter ces objets (et éventuellement d’autres en fonction de la sémantique de votre projet).  
  
 Dans un sens, ces objets fournissent l’avantage inverse des objets de projet spécifiques au VSPackage. Les objets Automation Standard permettent à votre projet d’être utilisé de manière généralisée comme tout autre projet prenant en charge les mêmes objets. Par conséquent, un complément écrit par rapport à des `Project` objets généraux et `ProjectItem` peut fonctionner sur des projets de n’importe quel type. Pour plus d’informations, consultez [modélisation de projet](../../extensibility/internals/project-modeling.md).
