---
title: Algorithme de routage des commandes | Microsoft Docs
description: En savoir plus sur l’ordre de résolution de commande dans Visual Studio, car les commandes sont gérées par différents composants et acheminées du contexte le plus profond au contexte le plus externe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e02493cbb2f872806ade33d77609d45d1938ccd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057310"
---
# <a name="command-routing-algorithm"></a>Algorithme de routage des commandes
Dans, les commandes Visual Studio sont gérées par plusieurs composants différents. Les commandes sont routées du contexte le plus profond, qui est basé sur la sélection actuelle, vers le contexte le plus à l’extérieur (également connu sous le nom de Global). Pour plus d’informations, consultez [disponibilité des commandes](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Ordre de résolution de commande
 Les commandes sont transmises à travers les niveaux de contexte de commande suivants :

1. Compléments : l’environnement propose d’abord la commande à tous les compléments présents.

2. Commandes de priorité : ces commandes sont inscrites à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Elles sont appelées pour chaque commande dans Visual Studio et sont appelées dans l’ordre dans lequel elles ont été inscrites.

3. Commandes de menu contextuel : une commande située dans un menu contextuel est d’abord proposée à la cible de commande fournie dans le menu contextuel, puis à l’acheminement par défaut.

4. Cibles de commande du jeu de barres d’outils : ces cibles de commande sont inscrites lorsque vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . Le `pCmdTarget` paramètre peut être `null` . Si ce n’est pas `null` le cas, cette cible de commande est utilisée pour mettre à jour toutes les commandes situées sur la barre d’outils que vous configurez. Si l’interpréteur de commandes configure votre barre d’outils, il passe le frame de fenêtre en tant que `pCmdTarget` pour que toutes les mises à jour des commandes de votre barre d’outils se déplacent dans le cadre de la fenêtre, même lorsqu’il n’est pas actif.

5. Fenêtre outil : les fenêtres outil, qui implémentent généralement l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface, doivent également implémenter l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface afin que Visual Studio puisse recevoir la cible de commande lorsque la fenêtre outil est la fenêtre active. Toutefois, si la fenêtre outil qui a le focus est la fenêtre de **projet** , la commande est routée vers l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface qui est le parent commun des éléments sélectionnés. Si cette sélection s’étend sur plusieurs projets, la commande est routée vers la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hiérarchie. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface contient les <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> méthodes et qui sont analogues aux commandes correspondantes sur l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.

6. Fenêtre de document : si l’indicateur de la commande est `RouteToDocs` défini dans son fichier *. vsct* , Visual Studio recherche une cible de commande sur l’objet de vue de document, qui est soit une instance d’une interface, soit <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> une instance d’un objet de document (généralement une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface ou une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface). Si l’objet de vue de document ne prend pas en charge la commande, Visual Studio route la commande vers l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface retournée. (Il s’agit d’une interface facultative pour les objets de données de document.)

7. Hiérarchie actuelle : la hiérarchie actuelle peut être le projet qui possède la fenêtre de document active ou la hiérarchie sélectionnée dans **Explorateur de solutions**. Visual Studio recherche l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface qui est implémentée sur la hiérarchie actuelle ou active. La hiérarchie doit prendre en charge les commandes qui sont valides lorsque la hiérarchie est active, même si une fenêtre de document d’un élément de projet a le focus. Toutefois, les commandes qui s’appliquent uniquement lorsque **Explorateur de solutions** a le focus doivent être prises en charge à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface et de ses <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> méthodes et.

     Les commandes **couper**, **copier**, **coller**, **supprimer**, **Renommer**, **entrer** et **DoubleClick** nécessitent un traitement spécial. Pour plus d’informations sur la gestion des commandes **Delete** et **Remove** dans les hiérarchies, consultez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interface.

8. Global : si une commande n’a pas été gérée par les contextes mentionnés précédemment, Visual Studio tente de la router vers le VSPackage qui possède une commande qui implémente l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Si le VSPackage n’a pas déjà été chargé, il n’est pas chargé quand Visual Studio appelle la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode. Le VSPackage est chargé uniquement lorsque la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode est appelée.

## <a name="see-also"></a>Voir aussi
- [Conception de commande](../../extensibility/internals/command-design.md)
