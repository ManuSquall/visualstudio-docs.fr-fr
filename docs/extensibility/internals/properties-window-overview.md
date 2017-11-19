---
title: "Vue d’ensemble de la fenêtre Propriétés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0094accca0feb026fca02c78bf6e86fe512ce981
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-overview"></a>Vue d'ensemble de la fenêtre Propriétés
Le **propriétés** fenêtre est utilisée pour afficher les propriétés pour les objets sélectionnés dans les deux principaux types de fenêtres disponibles dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Ces deux types de fenêtres sont :  
  
-   Fenêtres d’outils tels que navigateur de l’Explorateur de solutions, affichage de classes et objets  
  
-   Fenêtres de document contenant ces éditeurs et les concepteurs que le Concepteur de formulaires, un éditeur XML et un éditeur HTML  
  
## <a name="using-the-properties-window"></a>À l’aide de la fenêtre Propriétés  
 Le **propriétés** fenêtre affiche les propriétés d’un ou plusieurs éléments sélectionnés. Si plusieurs éléments sont sélectionnés, l’intersection de toutes les propriétés de tous les objets sélectionnés s’affiche.  
  
 Événements liés à un objet sélectionné dans une fenêtre de conception de formulaires ou l’éditeur HTML à l’aide des métadonnées COM + sont affichent dans le **propriétés** fenêtre. Par exemple, vous pouvez sélectionner un bouton et afficher ses événements associés, tel qu’un `OnClick` événement, qui peut être lié à ce bouton.  
  
 Les événements affichés dans le **propriétés** fenêtre sont principalement utilisées avec les objets qui sont liés au code. Si vous modifiez un format de fichier qui n’a pas rien à voir avec le code, vous ne souhaitez pas avoir tous les événements. Les événements sont affichés dans le **propriétés** fenêtre lorsqu’il existe une liaison entre l’exécution de code et certains événements associés à des objets spécifiques. Un exemple serait code-behind d’un objet sélectionné qui s’exécute lorsque cet objet est activé.  
  
 Le tableau suivant répertorie les interfaces principales utilisées par le **propriétés** fenêtre.  
  
|Nom de l’interface|Description|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fournit une liste de catégories pour le **propriétés** fenêtre et mappe chaque propriété à une catégorie.|  
|[Interface IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|Expose des méthodes et des propriétés pour la programmation des outils et autres applications qui prennent en charge d’automation d’un objet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fournit des boutons de sélection (...) appelé *générateurs* qui ouvrir des fenêtres de dialogue modale implémentées par l’objet lui-même. Utilisé lorsqu’une valeur n’est pas facilement tapée par l’utilisateur dans un champ de texte. Par exemple, il peut être utilisé pour ouvrir un sélecteur de couleur qui détermine la valeur RVB pour vous.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fournit l’accès aux objets utilisés pour mettre à jour les informations affichées dans le **propriétés** fenêtre. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>est implémentée par les packages VS pour chaque fenêtre qui contient des objets sélectionnables avec des propriétés connexes à afficher.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fournit des informations sur le type d’un objet, telles que les méthodes d’une interface et les champs d’une structure.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Active les VSPackages pour recevoir une notification d’événements de sélection et récupérer des informations sur la hiérarchie de projet en cours, élément, valeur de l’élément et contexte de l’interface utilisateur de commande.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fournit l’environnement avec un accès à plusieurs sélections.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Utilisé pour fournir des noms localisés sur certaines propriétés affichées dans le **propriétés** fenêtre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifie les VSPackages inscrits des modifications apportées à la sélection actuelle, la valeur de l’élément ou le contexte de l’interface utilisateur de commande.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifie l’environnement d’un changement de la sélection actuelle et donne accès aux informations de hiérarchie et élément relatives à la nouvelle sélection.|  
  
 Pour plus d’informations sur `IDispatch`, consultez MSDN library.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre les propriétés](../../extensibility/internals/extending-properties.md)   
 [Champs et interfaces de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)