---
title: "Algorithme de routage de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "routage des commandes"
  - "routage des commandes"
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Algorithme de routage de commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans Visual Studio, les commandes sont gérées par un nombre de différents composants. Commandes sont routées à partir du contexte plus profond, ce qui est basé sur la sélection actuelle, vers le contexte le plus extérieur \(également appelé global\). Pour plus d'informations, consultez [Disponibilité](../../extensibility/internals/command-availability.md).  
  
## Ordre de résolution de commande  
 Commandes sont transmis via les niveaux de contexte de commande suivants :  
  
1.  Compléments : L’environnement offre tout d’abord la commande pour les compléments qui sont présents.  
  
2.  Commandes de priorité : ces commandes sont enregistrés à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Ils sont appelés pour chaque commande dans Visual Studio et sont appelés dans l’ordre dans lequel ils ont été enregistrés.  
  
3.  Commandes de menu contextuel : la première mise en une commande qui se trouve dans un menu contextuel à la cible de commande est fournie pour le menu contextuel, puis pour le routage par défaut.  
  
4.  Barre d’outils de définie des cibles de la commande : ces cibles de la commande sont enregistrés lorsque vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Le `pCmdTarget` paramètre peut être `null`. Si ce n’est pas `null`, cette cible de commande est utilisé pour mettre à jour toutes les commandes situées sur la barre d’outils que vous configurez. Si l’interface de configuration de votre barre d’outils, puis il transmet le frame de fenêtre comme le `pCmdTarget` afin que toutes les mises à jour pour les commandes de votre flux de la barre d’outils via le frame de fenêtre, même lorsqu’il n’est pas active.  
  
5.  Fenêtre outil : Outil windows, qui implémentent généralement les <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface, doivent également implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface afin que Visual Studio puisse la cible de commande lorsque la fenêtre outil est la fenêtre active. Toutefois, si la fenêtre outil qui a le focus est la **projet** fenêtre, puis la commande est acheminé vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface qui est le parent commun des éléments sélectionnés. Si cette sélection s’étend sur plusieurs projets, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hiérarchie. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface contient la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> méthodes sont analogues aux commandes correspondantes sur le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
6.  Fenêtre de document : Si la commande RouteToDocs indicateur est défini dans le fichier .vsct, Visual Studio recherche une cible de commande sur l’objet de vue de document, qui est soit une instance d’un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface ou une instance d’un objet document \(généralement un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface ou un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface\). Si l’objet de vue de document ne prend pas en charge la commande, Visual Studio achemine la commande pour le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface retournée. \(Ceci est une interface facultative pour les objets de données de document\).  
  
7.  Hiérarchie actuelle : la hiérarchie actuelle peut être le propriétaire de la fenêtre du document ou la hiérarchie est sélectionnée dans le projet **l’Explorateur de solutions**. Visual Studio recherche la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface est implémentée sur la hiérarchie, active, ou en cours. La hiérarchie doit prendre en charge les commandes qui sont valides, chaque fois que la hiérarchie est active, même si une fenêtre de document d’un élément de projet a le focus. Toutefois, les commandes qui s’appliquent uniquement lorsque **l’Explorateur de solutions** a le focus doivent être pris en charge à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface et son <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>méthodes.  
  
     **Couper**, **copie**, **Coller**, **Supprimer**, **Renommer**, **entrée**, et **le double\-clic** commandes nécessitent un traitement spécial. Pour plus d’informations sur la gestion **Supprimer** et **Supprimer** commandes dans des hiérarchies, consultez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interface.  
  
8.  Global : Si une commande n’a pas été gérée par les contextes mentionnés précédemment, Visual Studio tente de router vers le VSPackage qui possède une commande qui implémente le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Si le VSPackage n’a pas déjà été chargé, il n’est pas chargé lorsque Visual Studio appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(méthode\). Le VSPackage est chargé uniquement lorsque le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode est appelée.  
  
## Voir aussi  
 [Création de la commande](../../extensibility/internals/command-design.md)