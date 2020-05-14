---
title: Fournir l’automatisation pour VSPackages (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705947"
---
# <a name="providing-automation-for-vspackages"></a>Fourniture de l’automatisation pour VSPackages
Il existe deux façons principales de fournir l’automatisation de vos VSPackages : en implémentant des objets spécifiques à VSPackage et en implémentant des objets d’automatisation standard. En général, ceux-ci sont utilisés ensemble pour étendre le modèle d’automatisation de l’environnement.

## <a name="vspackage-specific-objects"></a>Objets spécifiques à VSPackage
 Certains endroits du modèle d’automatisation vous obligent à fournir des objets d’automatisation uniques à votre VSPackage. Par exemple, les nouveaux projets nécessitent des objets distincts que seul votre VSPackage fournit. Les noms de ces objets sont inscrits dans le `DTE` registre et obtenus par des appels à l’objet de l’environnement.

 Les objets spécifiques à VSPackage peuvent également être obtenus lorsqu’un consommateur d’automatisation utilise l’objet fourni par la propriété Objet d’un objet standard. Par exemple, `Window` l’objet `Object` standard a une `Windows.Object` propriété, communément connue sous le nom de propriété. Lorsque les `Window.Object` consommateurs appellent le sur une fenêtre implémentée dans votre VSPackage, vous transmettez un objet d’automatisation spécifique de votre propre conception.

#### <a name="projects"></a>Projets
 VSPackages peut étendre le modèle d’automatisation pour les nouveaux types de projets à travers leurs propres objets spécifiques VSPackage. Le but principal de fournir de nouveaux objets d’automatisation pour <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> votre <xref:VSLangProj80.VSProject2> VSPackage est de différencier vos objets de projet uniques d’un ou d’un objet. Cette différenciation est pratique lorsque vous voulez fournir un moyen de distinguer ou d’itérer votre type de projet en dehors d’autres types de projets, si elles apparaissent côte à côte dans une solution. Pour plus d’informations, voir [Exposing Project Objects](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Événements
 L’architecture événementielle de l’environnement vous offre un autre endroit pour ajouter vos propres objets spécifiques à VSPackage. Par exemple, en créant vos propres objets événementiels uniques, vous pouvez étendre le modèle événementiel de l’environnement pour les projets. Vous voudrez peut-être fournir vos propres événements lorsqu’un nouvel élément est ajouté à votre propre type de projet. Pour plus d’informations, voir [Exposing Events](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Objets fenêtres
 Windows peut transmettre un objet d’automatisation spécifique à VSPackage vers l’environnement lorsqu’il est appelé. Vous implémentez un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> objet `IDispatch` dérivé de , ou qui remet des propriétés, l’extension de l’objet de fenêtre dans lequel il est situé. Par exemple, vous pouvez utiliser cette approche pour fournir l’automatisation d’un contrôle situé dans un cadre de fenêtre. La sémantique de cet objet et tous les autres objets qu’il pourrait étendre sont les vôtres à la conception. Pour plus d’informations, voir [Comment : Fournir l’automatisation pour Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Pages d’options sur le menu Outils
 Vous pouvez créer des pages pour étendre le modèle d’automatisation des outils, des options par la mise en œuvre de pages et l’ajout d’informations au registre pour créer vos propres options. Vos pages peuvent alors être appelées à travers le modèle d’objet environnement comme toutes les autres pages d’options. Si la conception de la fonctionnalité que vous ajoutez à l’environnement grâce à VSPackages nécessite des pages d’options, alors vous devriez ajouter le support d’automatisation ainsi. Pour plus d’informations, voir [Automation Support for Options Pages](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Objets d’automatisation standard
 Pour étendre l’automatisation des projets, vous `IDispatch`implémentez également des objets d’automatisation standard (dérivés de ) qui se tiennent à côté des autres objets du projet et implémentent des méthodes et des propriétés standard. Des exemples d’objets standard incluent les objets du `Projects` `Project`projet `ProjectItem`qui `ProjectItems`sont insérés dans la hiérarchie de la solution tels que , , , et . Chaque nouveau type de projet doit implémenter ces objets (et peut-être d’autres en fonction de la sémantique de votre projet).

 En un sens, ces objets offrent l’avantage opposé des objets de projet spécifiques à VSPackage. Les objets d’automatisation standard permettent à votre projet d’être utilisé de manière généralisée comme tout autre projet soutenant les mêmes objets. Ainsi, un add-in qui `Project` est `ProjectItem` écrit contre le général et les objets peuvent fonctionner contre des projets de tout type. Pour plus d’informations, voir [Project Modeling](../../extensibility/internals/project-modeling.md).
