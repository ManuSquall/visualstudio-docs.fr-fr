---
title: Properties Window Fields and Interfaces | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 515540eee455fcf22151e336897dd5f586867a82
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947976"
---
# <a name="properties-window-fields-and-interfaces"></a>Champs et interfaces de la fenêtre Propriétés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le modèle de sélection à déterminer quelles informations sont affichées dans le **propriétés** fenêtre est basée sur la fenêtre qui a le focus dans l’IDE. Chaque fenêtre et chaque objet dans la fenêtre sélectionnée, peuvent avoir son objet de contexte de sélection vers le contexte de la sélection globale. L’environnement des mises à jour le contexte de sélection global avec des valeurs à partir d’un frame de fenêtre lorsque cette fenêtre a le focus. Lorsque le focus est modifié, tout comme le fait le contexte de sélection.  
  
## <a name="tracking-selection-in-the-ide"></a>Suivi de sélection dans l’IDE  
 Le frame de fenêtre ou le site, détenu par l’IDE, propose un service appelé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Les étapes suivantes montrent comment une modification dans une sélection, ce qui a provoqué par l’utilisateur modifie le focus vers une autre fenêtre ouverte ou en sélectionnant un élément de projet différent dans **l’Explorateur de solutions**, est implémentée pour modifier le contenu affiché dans le  **Propriétés** fenêtre.  
  
1. L’objet créé par votre VSPackage est placé dans les appels de la fenêtre sélectionnée <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> avoir <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> appeler <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Le conteneur de sélection fourni par la fenêtre sélectionnée, crée son propre <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objet. Lorsque la sélection change, le VSPackage appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> pour informer les écouteurs dans l’environnement, y compris le **propriétés** fenêtre, de la modification. Il donne également accès aux informations de hiérarchie et les éléments liés à la nouvelle sélection.  
  
3. Appel <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> et en lui passant les éléments de la hiérarchie sélectionnée dans le `VSHPROPID_BrowseObject` paramètre remplit le <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objet.  
  
4. Objet dérivé de la [IDispatch Interface](http://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) est retournée pour <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> pour l’élément demandé, et l’environnement encapsulé dans un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (voir l’étape suivante). Si l’appel échoue, l’environnement, un deuxième appel à `IVsHierarchy::GetProperty`, en lui passant le conteneur de sélection <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que l’ou les éléments de hiérarchie fournissent.  
  
    Votre projet ne crée pas de VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , car la fenêtre d’environnement fourni VSPackage qui implémente (par exemple, **l’Explorateur de solutions**) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en son nom.  
  
5. L’environnement appelle les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pour obtenir les objets basés sur le `IDispatch` interface pour renseigner le **propriétés** fenêtre.  
  
   Lorsqu’une valeur dans le **propriétés** fenêtre est modifiée, les VSPackages implémenter `IVsTrackSelectionEx::OnElementValueChangeEx` et `IVsTrackSelectionEx::OnSelectionChangeEx` pour signaler la modification à la valeur de l’élément. L’environnement appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ou <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> pour conserver les informations affichées dans le **propriétés** fenêtre synchronisé avec les valeurs de propriété. Pour plus d’informations, consultez [la mise à jour des valeurs de propriété dans la fenêtre Propriétés](../../misc/updating-property-values-in-the-properties-window.md).  
  
   En plus de sélectionner un autre élément de projet dans **l’Explorateur de solutions** pour afficher les propriétés liées à cet élément, vous pouvez également choisir un objet différent dans un formulaire ou fenêtre de document à l’aide de la liste déroulante disponible sur le **Propriétés** fenêtre. Pour plus d’informations, consultez [liste d’objets de fenêtre de propriétés](../../extensibility/internals/properties-window-object-list.md).  
  
   Vous pouvez modifier le mode d’affichent d’informations dans le **propriétés** grille de la fenêtre à partir d’alphabétique aux catégories, et, s’il est disponible, vous pouvez également ouvrir une page de propriétés d’un objet sélectionné en cliquant sur les boutons appropriés sur le  **Propriétés** fenêtre. Pour plus d’informations, consultez [boutons de la fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md) et [Pages de propriétés](../../extensibility/internals/property-pages.md).  
  
   Enfin, la partie inférieure de la **propriétés** fenêtre contient également une description du champ sélectionné dans le **propriétés** grille de la fenêtre. Pour plus d’informations, consultez [l’obtention de Descriptions de champs à partir de la fenêtre Propriétés](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)
