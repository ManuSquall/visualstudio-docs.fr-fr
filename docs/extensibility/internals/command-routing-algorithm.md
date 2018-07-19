---
title: Algorithme de routage de commande | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aba7ddcdda4dd4eabbb9266e0fa89c916bb028f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131491"
---
# <a name="command-routing-algorithm"></a>Algorithme de routage de commande
Dans Visual Studio, les commandes sont gérées par un nombre des différents composants. Commandes sont routées à partir du contexte plus profond, ce qui est basé sur la sélection actuelle, vers le contexte le plus extérieur (également appelé global). Pour plus d’informations, consultez [disponibilité](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Ordre de résolution de commande  
 Commandes sont transmises via les niveaux de contexte de commande suivants :  
  
1.  Les compléments : L’environnement offre tout d’abord la commande pour les compléments qui sont présents.  
  
2.  Les commandes de priorité : ces commandes sont inscrits à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Ils sont appelés pour toutes les commandes dans Visual Studio et sont appelés dans l’ordre dans lequel ils ont été enregistrés.  
  
3.  Commandes de menu contextuel : une commande qui se trouve dans un menu contextuel est tout d’abord proposée à la cible de commande qui est fournie au menu contextuel, puis pour le routage par défaut.  
  
4.  Barre d’outils de définir des cibles de commande : ces cibles de commande sont enregistrés lorsque vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Le `pCmdTarget` paramètre peut être `null`. Si elle n’est pas `null`, cette cible de commande est utilisée pour mettre à jour toutes les commandes situées sur la barre d’outils que vous configurez. Si l’interface de configuration de votre barre d’outils, puis il transmet le frame de fenêtre comme le `pCmdTarget` afin que toutes les mises à jour pour les commandes de votre flux de barre d’outils dans le frame de fenêtre, même quand il n’est pas le focus.  
  
5.  Tool Window : Fenêtres, qui implémentent généralement le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> l’interface, doit également implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de l’interface qui permet d’obtenir la cible de commande dans Visual Studio lorsque la fenêtre outil est la fenêtre active. Toutefois, si la fenêtre outil qui a le focus est la **projet** fenêtre, puis la commande est acheminé vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface qui est le parent commun des éléments sélectionnés. Si cette sélection s’étend sur plusieurs projets, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hiérarchie. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface contient la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> méthodes analogues pour les commandes correspondantes sur le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
6.  Fenêtre de document : Si la commande RouteToDocs indicateur est défini dans le fichier .vsct, Visual Studio recherche une cible de la commande sur l’objet de vue de document, qui est soit une instance d’un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface ou une instance d’un objet de document (en général un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interface ou un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface). Si l’objet de vue de document ne prend pas en charge la commande, Visual Studio achemine la commande pour le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface qui est retournée. (Ceci est une interface facultative pour les objets de données de document.)  
  
7.  Hiérarchie actuelle : la hiérarchie actuelle peut être le projet qui possède la fenêtre de document actif ou de la hiérarchie sélectionnée dans **l’Explorateur de solutions**. Visual Studio recherche la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface est implémentée sur la hiérarchie, active, ou en cours. La hiérarchie doit prendre en charge les commandes qui sont valides lorsque la hiérarchie est active, même si une fenêtre de document d’un élément de projet a le focus. Toutefois, les commandes qui s’appliquent uniquement lorsque **l’Explorateur de solutions** a le focus doit être pris en charge à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface et son <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>méthodes.  
  
     **Couper**, **copie**, **coller**, **supprimer**, **renommer**, **entrez**et **Le double-clic** commandes nécessitent un traitement spécial. Pour plus d’informations sur la gestion **supprimer** et **supprimer** commandes dans les hiérarchies, voir la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interface.  
  
8.  Global : Si une commande n’a pas été gérée par les contextes mentionnées précédemment, Visual Studio tente de router vers le VSPackage qui possède une commande qui implémente le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Si le package Visual Studio n’a pas déjà été chargé, il n’est pas chargé quand Visual Studio appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode). Le VSPackage est chargé uniquement lorsque le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de commande](../../extensibility/internals/command-design.md)