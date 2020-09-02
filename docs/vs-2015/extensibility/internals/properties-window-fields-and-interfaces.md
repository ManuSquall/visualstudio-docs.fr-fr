---
title: Champs et interfaces de la fenêtre Propriétés | Microsoft Docs
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
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700821"
---
# <a name="properties-window-fields-and-interfaces"></a>Champs et interfaces de la fenêtre Propriétés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le modèle de sélection permettant de déterminer les informations qui s’affichent dans la fenêtre **Propriétés** est basé sur la fenêtre qui a le focus dans l’IDE. Chaque fenêtre et objet dans la fenêtre sélectionnée peut faire l’objet d’un push de l’objet de contexte de sélection dans le contexte de sélection global. L’environnement met à jour le contexte de sélection global avec les valeurs d’un frame de fenêtre lorsque cette fenêtre a le focus. Lorsque le focus change, le contexte de sélection est donc sélectionné.  
  
## <a name="tracking-selection-in-the-ide"></a>Suivi de la sélection dans l’IDE  
 Le cadre de la fenêtre ou le site, appartenant à l’IDE, a un service appelé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Les étapes suivantes montrent comment une modification d’une sélection, provoquée par l’utilisateur à modifier le focus vers une autre fenêtre ouverte ou à sélectionner un autre élément de projet dans **Explorateur de solutions**, est implémentée pour modifier le contenu affiché dans la fenêtre **Propriétés** .  
  
1. L’objet créé par le VSPackage qui est sur site dans la fenêtre sélectionnée appelle <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> pour qu’il appelle <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Le conteneur de sélection, fourni par la fenêtre sélectionnée, crée son propre <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objet. Lorsque la sélection change, le VSPackage appelle <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> pour notifier tous les écouteurs de l’environnement, y compris la fenêtre **Propriétés** , de la modification. Il permet également d’accéder aux informations de hiérarchie et d’élément relatives à la nouvelle sélection.  
  
3. L’appel <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> et la transmission des éléments de la hiérarchie sélectionnés dans le `VSHPROPID_BrowseObject` paramètre remplit l' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objet.  
  
4. Un objet dérivé de l' [interface IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) est retourné pour <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> pour l’élément demandé, et l’environnement l’encapsule dans un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (Voir l’étape suivante). Si l’appel échoue, l’environnement effectue un deuxième appel à `IVsHierarchy::GetProperty` , en lui transmettant le conteneur de sélection <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> fourni par le ou les éléments de la hiérarchie.  
  
    Le VSPackage de votre projet n’est pas créé <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , car le VSPackage de fenêtre fourni par l’environnement qui l’implémente (par exemple, **Explorateur de solutions**) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en son nom.  
  
5. L’environnement appelle les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pour récupérer les objets en fonction de l' `IDispatch` interface à remplir dans la fenêtre **Propriétés** .  
  
   Quand une valeur est modifiée dans la fenêtre **Propriétés** , les VSPackages implémentent `IVsTrackSelectionEx::OnElementValueChangeEx` et `IVsTrackSelectionEx::OnSelectionChangeEx` pour signaler la modification apportée à la valeur de l’élément. L’environnement appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ou <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> pour conserver les informations affichées dans la fenêtre **Propriétés** et les synchroniser avec les valeurs de propriété. Pour plus d’informations, consultez [mise à jour des valeurs de propriété dans la fenêtre Propriétés](../../misc/updating-property-values-in-the-properties-window.md).  
  
   En plus de sélectionner un autre élément de projet dans **Explorateur de solutions** pour afficher les propriétés associées à cet élément, vous pouvez également choisir un autre objet dans un formulaire ou une fenêtre de document à l’aide de la liste déroulante disponible dans la fenêtre **Propriétés** . Pour plus d’informations, consultez Liste des objets de la [fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md).  
  
   Vous pouvez modifier la façon dont les informations sont affichées dans la grille de la fenêtre **Propriétés** de l’ordre alphabétique à catégorie, et, si elles sont disponibles, vous pouvez également ouvrir une page de propriétés pour un objet sélectionné en cliquant sur les boutons appropriés dans la fenêtre **Propriétés** . Pour plus d’informations, consultez boutons et [pages](../../extensibility/internals/property-pages.md)de propriétés de la [fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md) .  
  
   Enfin, le bas de la fenêtre **Propriétés** contient également une description du champ sélectionné dans la grille de la fenêtre **Propriétés** . Pour plus d’informations, consultez [obtention de descriptions de champs à partir de la fenêtre Propriétés](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)
