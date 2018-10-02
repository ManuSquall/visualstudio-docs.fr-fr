---
title: Vue d’ensemble de la fenêtre Propriétés | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1bd869cd9d5fd10a31383d93671bf820887087a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502688"
---
# <a name="properties-window-overview"></a>Vue d'ensemble de la fenêtre Propriétés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue d’ensemble de la fenêtre Propriétés](https://docs.microsoft.com/visualstudio/extensibility/internals/properties-window-overview).  
  
Le **propriétés** fenêtre permet d’afficher les propriétés d’objets sélectionnés dans les deux principaux types de fenêtres disponibles dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE). Ces deux types de fenêtres sont :  
  
-   Fenêtres d’outils tels que navigateur de l’Explorateur de solutions, affichage de classes et objets  
  
-   Fenêtres de document contenant ces éditeurs et les concepteurs en tant que le Concepteur de formulaires, un éditeur XML et un éditeur HTML  
  
## <a name="using-the-properties-window"></a>À l’aide de la fenêtre Propriétés  
 Le **propriétés** fenêtre affiche les propriétés d’un ou plusieurs éléments sélectionnés. Si plusieurs éléments sont sélectionnés, l’intersection de toutes les propriétés pour tous les objets sélectionnés s’affiche.  
  
 Événements liés à un objet sélectionné dans une fenêtre de conception de formulaire ou d’un éditeur de code HTML à l’aide des métadonnées COM + sont affichés dans le **propriétés** fenêtre. Par exemple, vous pouvez sélectionner un bouton et afficher les événements associés, comme un `OnClick` événement, qui peut être liée à ce bouton.  
  
 Les événements affichés dans le **propriétés** fenêtre sont principalement utilisées avec des objets qui sont liés au code. Si vous modifiez un format de fichier qui n’a pas rien à voir avec le code, vous ne souhaitez pas avoir tous les événements. Les événements sont affichés uniquement dans le **propriétés** fenêtre lorsqu’il existe une liaison entre l’exécution de code et certains événements associés à des objets spécifiques. Un exemple serait code-behind d’un objet sélectionné qui s’exécute lorsque cet objet est activé.  
  
 Le tableau suivant répertorie les interfaces principales utilisées par le **propriétés** fenêtre.  
  
|Nom de l’interface|Description|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fournit une liste des catégories pour le **propriétés** fenêtre et mappe chaque propriété à une catégorie.|  
|[Interface IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Expose des méthodes et des propriétés à la programmation des outils et autres applications qui prennent en charge d’automation d’un objet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fournit des boutons de sélection (...) appelé *générateurs* qui ouvrir des fenêtres de boîte de dialogue modale implémentées par l’objet lui-même. Utilisé lorsqu’une valeur n’est pas facilement tapée par l’utilisateur dans un champ de texte. Par exemple, il peut être utilisé pour ouvrir un sélecteur de couleurs qui détermine la valeur RVB pour vous.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fournit l’accès aux objets utilisés pour mettre à jour les informations affichées dans le **propriétés** fenêtre. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> est implémenté par les VSPackages pour chaque fenêtre qui contient les objets sélectionnables avec les propriétés associées à afficher.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fournit des informations sur le type d’un objet comme des méthodes d’une interface et des champs d’une structure.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permet aux VSPackages pour recevoir une notification d’événements de sélection et récupérer des informations sur la hiérarchie de projet actuelle, élément, valeur de l’élément et contexte d’interface utilisateur de commande.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fournit l’environnement avec un accès à des sélections multiples.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Permet de fournir des noms localisés sur certaines propriétés affichées dans le **propriétés** fenêtre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Avertit les VSPackages enregistrés des modifications apportées à la sélection actuelle, la valeur de l’élément ou le contexte d’interface utilisateur de commande.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Indique à l’environnement d’un changement de la sélection actuelle et donne accès aux informations de hiérarchie et les éléments relatifs à la nouvelle sélection.|  
  
 Pour plus d’informations sur `IDispatch`, consultez MSDN library.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre les propriétés](../../extensibility/internals/extending-properties.md)   
 [Champs et interfaces de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)

