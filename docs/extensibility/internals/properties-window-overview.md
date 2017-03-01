---
title: "Présentation de la fenêtre Propriétés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1ec1a650c72fbd181d176aea84b228c9973ad526
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-overview"></a>Vue d'ensemble de la fenêtre Propriétés
Le **propriétés** fenêtre est utilisée pour afficher les propriétés pour les objets sélectionnés dans les deux principaux types de fenêtres disponibles dans les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Ces deux types de fenêtres sont :  
  
-   Fenêtres d’outils tels que navigateur de l’Explorateur de solutions, affichage de classes et objets  
  
-   Fenêtres de document contenant ces éditeurs et les concepteurs que le Concepteur de formulaires, un éditeur XML et un éditeur HTML  
  
## <a name="using-the-properties-window"></a>À l’aide de la fenêtre Propriétés  
 Le **propriétés** affiche les propriétés d’un ou plusieurs éléments sélectionnés. Si plusieurs éléments sont sélectionnés, l’intersection de toutes les propriétés de tous les objets sélectionnés s’affiche.  
  
 Événements liés à un objet sélectionné dans une fenêtre de conception de formulaires ou l’éditeur HTML à l’aide des métadonnées COM + sont affichent dans le **propriétés** fenêtre. Par exemple, vous pouvez sélectionner un bouton et afficher ses événements associés, tel qu’un `OnClick` événement, qui peut être lié à ce bouton.  
  
 Les événements affichés dans le **propriétés** fenêtre sont principalement utilisées avec les objets qui sont liés au code. Si vous modifiez un format de fichier qui n’a pas rien à voir avec le code, vous ne vont pas avoir d’événements. Les événements sont affichés uniquement dans le **propriétés** fenêtre lorsqu’il y a une liaison entre l’exécution de code et certains événements associés à des objets spécifiques. Un exemple serait code-behind d’un objet sélectionné qui s’exécute lorsque cet objet est activé.  
  
 Le tableau suivant répertorie les interfaces principales utilisées par le **propriétés** fenêtre.  
  
|Nom de l'interface|Description|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties></xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fournit une liste de catégories pour le **propriétés** fenêtre et mappe chaque propriété à une catégorie.|  
|[IDispatch (Interface)](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Expose des méthodes et des propriétés à la programmation des outils et autres applications qui prennent en charge automation d’un objet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder></xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fournit des boutons de sélection (...) appelé *générateurs* qui fenêtres boîte de dialogue modale implémentée par l’objet lui-même. Utilisé lorsqu’une valeur n’est pas facilement tapée par l’utilisateur dans un champ de texte. Par exemple, il peut être utilisé pour ouvrir un sélecteur de couleurs qui détermine la valeur RVB pour vous.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer></xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fournit l’accès à des objets utilisés pour mettre à jour les informations affichées dans le **propriétés** fenêtre. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>est implémentée par les packages VS pour chaque fenêtre qui contient les objets pouvant être avec les propriétés associées à afficher.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo></xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fournit des informations sur le type d’un objet, comme les méthodes d’une interface et les champs d’une structure.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permet de packages VS pour recevoir une notification d’événements de sélection et récupérer des informations sur la hiérarchie de projet en cours, élément, valeur de l’élément et contexte de l’interface utilisateur de commande.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect></xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fournit l’environnement avec un accès à plusieurs sélections.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing></xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Permet de fournir des noms localisés sur certaines propriétés s’affichées dans le **propriétés** fenêtre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifie les VSPackages enregistrés des modifications apportées à la sélection actuelle, la valeur de l’élément ou le contexte de l’interface utilisateur de commande.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifie l’environnement d’un changement de la sélection actuelle et fournit l’accès à la hiérarchie et l’élément d’informations relatives à la nouvelle sélection.|  
  
 Pour plus d’informations sur `IDispatch`, consultez MSDN library.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre les propriétés](../../extensibility/internals/extending-properties.md)   
 [Interfaces et les champs de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)
