---
title: Algorithme de routage de commande | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44fc431f008c59a7d4ceff2d9b9ec14d85091daf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728001"
---
# <a name="command-routing-algorithm"></a>Algorithme de routage de commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans Visual Studio, les commandes sont gérées par un nombre de différents composants. Commandes sont routées à partir du contexte plus profond, ce qui est basé sur la sélection actuelle, pour le contexte le plus extérieur (également appelé global). Pour plus d’informations, consultez [disponibilité](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Ordre de résolution de la commande  
 Commandes sont transmises via les niveaux de contexte de commande suivants :  
  
1.  Compléments : L’environnement offre tout d’abord la commande pour n’importe quel des compléments qui sont présents.  
  
2.  Commandes de priorité : ces commandes sont inscrits à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Ils sont appelés pour chaque commande dans Visual Studio et sont appelés dans l’ordre dans lequel ils ont été inscrits.  
  
3.  Commandes de menu contextuel : une commande qui se trouve dans un menu contextuel est tout d’abord proposée à la cible de commande qui est fournie au menu contextuel, puis la suite pour le routage par défaut.  
  
4.  Barre d’outils de définir des cibles de commande : ces cibles de commande sont enregistrés lorsque vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Le `pCmdTarget` paramètre peut être `null`. Si ce n’est pas `null`, cette cible de commande est utilisé pour mettre à jour toutes les commandes de la barre d’outils que vous configurez. Si l’interpréteur de commandes consiste à configurer votre barre d’outils, puis il transmet le frame de fenêtre comme le `pCmdTarget` afin que toutes les mises à jour pour les commandes sur votre flux de la barre d’outils via le frame de fenêtre, même quand il n’est pas le focus.  
  
5.  Tool Window : Outil windows, qui implémentent généralement les <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> l’interface, doit également implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface afin que Visual Studio puisse la cible de commande lorsque la fenêtre outil est la fenêtre active. Toutefois, si la fenêtre outil qui a le focus est la **projet** fenêtre, puis la commande est acheminé vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface qui est le parent commun des éléments sélectionnés. Si cette sélection s’étend sur plusieurs projets, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hiérarchie. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface contient la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> méthodes sont analogues aux commandes correspondantes sur le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
6.  Fenêtre de document : Si la commande RouteToDocs indicateur est défini dans son fichier .vsct, Visual Studio recherche une cible de commande sur l’objet de vue de document, qui est soit une instance d’un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface ou une instance d’un objet de document (généralement un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interface ou un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface). Si l’objet de vue de document ne prend pas en charge la commande, Visual Studio achemine la commande pour le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface qui est retournée. (Il s’agit d’une interface facultative pour les objets de données de document.)  
  
7.  Hiérarchie actuelle : la hiérarchie actuelle peut être le projet qui possède la fenêtre de document active ou de la hiérarchie est sélectionnée dans **l’Explorateur de solutions**. Visual Studio recherche la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface est implémentée sur la hiérarchie, active, ou en cours. La hiérarchie doit prendre en charge les commandes qui sont valides, chaque fois que la hiérarchie est active, même si une fenêtre de document d’un élément de projet a le focus. Toutefois, les commandes qui s’appliquent uniquement lorsque **l’Explorateur de solutions** a le focus doit être pris en charge à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface et sa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>méthodes.  
  
     **Couper**, **copie**, **coller**, **supprimer**, **renommer**, **entrez**et **DoubleClick** commandes nécessitent un traitement spécial. Pour plus d’informations sur la gestion **supprimer** et **supprimer** commandes dans les hiérarchies, consultez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interface.  
  
8.  Global : Si une commande n’a pas été gérée par les contextes mentionnés précédemment, Visual Studio tente de router vers le VSPackage qui possède une commande qui implémente le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Si le VSPackage n’a pas déjà été chargé, il n’est pas chargé lorsque Visual Studio appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode). Le VSPackage est chargé uniquement lorsque le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de commande](../../extensibility/internals/command-design.md)

