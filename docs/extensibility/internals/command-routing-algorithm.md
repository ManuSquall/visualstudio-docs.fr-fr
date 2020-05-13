---
title: Algorithme de routage de commande (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709536"
---
# <a name="command-routing-algorithm"></a>Algorithme de routage de commande
Dans Visual Studio commandes sont traitées par un certain nombre de composants différents. Les commandes sont acheminées du contexte le plus intime, qui est basé sur la sélection actuelle, au contexte le plus extérieur (également connu sous le nom global). Pour plus d’informations, voir [disponibilité du Commandement](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Résolution de l’ordre de commandement
 Les commandes passent par les niveaux suivants du contexte de commandement :

1. Add-ins: L’environnement offre d’abord la commande à tous les add-ins qui sont présents.

2. Commandes prioritaires : Ces commandes <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>sont enregistrées à l’aide de . Ils sont appelés pour chaque commande dans Visual Studio, et sont appelés dans l’ordre dans lequel ils ont été enregistrés.

3. Commandes de menu contextuelle : Une commande située sur un menu contextuelle est d’abord offerte à la cible de commande fournie au menu contextuelle, et après cela au routage typique.

4. Toolbar définir des objectifs de commande: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>Ces cibles de commande sont enregistrées lorsque vous appelez . Le `pCmdTarget` paramètre `null`peut être . Si ce `null`n’est pas le cas, cette cible de commande est utilisée pour mettre à jour les commandes situées sur la barre d’outils que vous configurez. Si la coque configure votre barre d’outils, alors `pCmdTarget` elle passe le cadre de fenêtre comme le de sorte que toutes les mises à jour des commandes sur votre flux de barre d’outils à travers le cadre de fenêtre, même quand il n’est pas au point.

5. Fenêtre d’outil : Les <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> fenêtres d’outil, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> qui implémentent généralement l’interface, devraient également implémenter l’interface afin que Visual Studio puisse obtenir la cible de commande lorsque la fenêtre d’outil est la fenêtre active. Toutefois, si la fenêtre d’outil qui a mis l’accent <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> est la fenêtre **du projet,** alors la commande est acheminée vers l’interface qui est le parent commun des éléments sélectionnés. Si cette sélection s’étend sur plusieurs projets, la commande est acheminée vers la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hiérarchie. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> contient <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> les méthodes et les méthodes analogues aux commandes correspondantes sur l’interface. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

6. Fenêtre de document : `RouteToDocs` Si la commande a le drapeau placé dans son fichier *.vsct,* Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> recherche une cible de commande sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> l’objet de vue de document, qui est soit une instance d’une interface ou une instance d’un objet de document (généralement une interface ou une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface). Si l’objet de vue de document ne prend <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pas en charge la commande, Visual Studio achemine la commande vers l’interface qui est retournée. (Il s’agit d’une interface facultative pour les objets de données documentaires.)

7. Hiérarchie actuelle : La hiérarchie actuelle peut être le projet qui possède la fenêtre de document active ou la hiérarchie qui est sélectionnée dans **Solution Explorer**. Visual Studio recherche <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l’interface qui est implémentée sur la hiérarchie actuelle ou active. La hiérarchie doit prendre en charge les commandes qui sont valides chaque fois que la hiérarchie est active, même si une fenêtre de document d’un élément de projet est ciblée. Toutefois, les commandes qui ne s’appliquent que <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> lorsque Solution <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> **Explorer** a mis l’accent doivent être prises en charge en utilisant l’interface et ses méthodes.

     **Couper**, **Copier**, **Coller**, **Supprimer**, **renommer**, **Entrer**, et les commandes **DoubleClick** nécessitent une manipulation spéciale. Pour plus d’informations sur la façon de gérer <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> les commandes **Supprimer** et **supprimer** dans les hiérarchies, consultez l’interface.

8. Global: Si une commande n’a pas été traitée par les contextes mentionnés précédemment, Visual Studio <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tente de l’acheminer vers le VSPackage qui possède une commande qui implémente l’interface. Si le VSPackage n’a pas déjà été chargé, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il n’est pas chargé lorsque Visual Studio appelle la méthode. Le VSPackage n’est <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> chargé que lorsque la méthode est appelée.

## <a name="see-also"></a>Voir aussi
- [Conception de commande](../../extensibility/internals/command-design.md)
