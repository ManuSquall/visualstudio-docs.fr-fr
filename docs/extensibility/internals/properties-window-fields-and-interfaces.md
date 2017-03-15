---
title: "Interfaces et les champs de la fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Les interfaces, les champs et fenêtre Propriétés"
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Interfaces et les champs de la fen&#234;tre Propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le modèle pour la sélection détermine les informations sont affichées dans la fenêtre de **Propriétés** est basée sur la fenêtre qui a le focus dans l'IDE.  Chaque fenêtre, et l'objet dans la fenêtre sélectionnée, peut avoir son objet de contexte de sélection de type push au contexte global de sélection.  L'environnement met à jour le contexte global de sélection avec des valeurs d'un frame de fenêtre lorsque cette fenêtre a le focus.  Lorsque le focus est modifié, fait le contexte de sélection.  
  
## Sélection de traçage dans l'IDE  
 Le frame de fenêtre ou le site, détenu par l'IDE, a un service intitulé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.  Les étapes suivantes indiquent comment une modification dans une sélection, provoquée par l'utilisateur modifiant le focus vers une autre fenêtre active ou la sélection d'un élément de projet différent dans **Explorateur de solutions**, est implémenté pour modifier le contenu affiché dans la fenêtre de **Propriétés** .  
  
1.  L'objet créé par votre VSPackage qui se trouve dans la fenêtre sélectionnée appelle <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> pour faire appeler <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection><xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Le conteneur de sélection, le cas par la fenêtre sélectionnée, crée son propre objet d' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  Lorsque la sélection change, le VSPackage appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> pour notifier à tous les écouteurs dans l'environnement, y compris la fenêtre de **Propriétés** , la modification.  Elle fournit également l'accès à la hiérarchie et l'élément des informations relatives à la nouvelle sélection.  
  
3.  L' <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> appelant et le passer les éléments sélectionnés de hiérarchie du paramètre d' `VSHPROPID_BrowseObject` remplit l'objet d' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
4.  Un objet dérivé d' [IDispatch Interface](http://msdn.microsoft.com/fr-fr/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) est retourné pour <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> pour l'élément demandé, et l'environnement l'encapsule dans <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> \(consultez l'étape suivante\).  Si l'appel échoue, l'environnement fait un deuxième appel à `IVsHierarchy::GetProperty`, en lui passant le conteneur <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> de choix que le ou les éléments de la hiérarchie fournissent.  
  
     Votre projet VSPackage ne crée pas <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> car la fenêtre environnement\-fournie VSPackage qui l'implémente \(par exemple, **Explorateur de solutions**\) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> de sa part.  
  
5.  L'environnement appelle les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pour obtenir les objets basées sur l'interface d' `IDispatch` de terminer la fenêtre de **Propriétés** .  
  
 Lorsqu'une valeur dans la fenêtre de **Propriétés** est modifiée, VSPackages implémentent `IVsTrackSelectionEx::OnElementValueChangeEx` et `IVsTrackSelectionEx::OnSelectionChangeEx` pour stocker la modification apportée à la valeur d'élément.  L'environnement appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ou <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> pour gérer les informations affichées dans la fenêtre de **Propriétés** synchronisée avec les valeurs de propriété.  Pour plus d'informations, consultez [Mise à jour des valeurs de propriété dans la fenêtre Propriétés](../../misc/updating-property-values-in-the-properties-window.md).  
  
 En plus de sélectionner un élément de projet différent dans **Explorateur de solutions** aux propriétés d'affichage en rapport avec cet élément, vous pouvez également choisir un autre objet d'un formulaire ou d'une fenêtre de document à l'aide de la liste déroulante disponible dans la fenêtre de **Propriétés** .  Pour plus d'informations, consultez [Objet liste de la fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md).  
  
 Vous pouvez modifier la façon dont les informations sont affichées dans la grille de fenêtre de **Propriétés** d'alphabétique à par catégorie, et, si disponible, vous pouvez également ouvrir une page de propriétés pour un objet sélectionné en cliquant sur les boutons appropriés dans la fenêtre de **Propriétés** .  Pour plus d'informations, consultez [Boutons de la fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md) et [Pages de propriétés](../../extensibility/internals/property-pages.md).  
  
 Enfin, le bas de la fenêtre de **Propriétés** contient également une description du champ sélectionné dans la grille de fenêtre de **Propriétés** .  Pour plus d'informations, consultez [Obtenir des descriptions de champs à partir de la fenêtre Propriétés](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## Voir aussi  
 [Étendre les propriétés](../../extensibility/internals/extending-properties.md)