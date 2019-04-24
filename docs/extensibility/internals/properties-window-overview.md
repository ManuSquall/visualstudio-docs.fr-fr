---
title: Vue d’ensemble de la fenêtre Propriétés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06844e8723cc118d6cc10c44c5c788e48c206684
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101026"
---
# <a name="properties-window-overview"></a>Vue d'ensemble de la fenêtre Propriétés
Le **propriétés** fenêtre permet d’afficher les propriétés d’objets sélectionnés dans les deux principaux types de fenêtres disponibles dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Ces deux types de fenêtres sont :

- Fenêtres d’outils tels que navigateur de l’Explorateur de solutions, affichage de classes et objets

- Fenêtres de document contenant ces éditeurs et les concepteurs en tant que le Concepteur de formulaires, un éditeur XML et un éditeur HTML

## <a name="using-the-properties-window"></a>À l’aide de la fenêtre Propriétés
 Le **propriétés** fenêtre affiche les propriétés d’un ou plusieurs éléments sélectionnés. Si plusieurs éléments sont sélectionnés, l’intersection de toutes les propriétés pour tous les objets sélectionnés s’affiche.

 Événements liés à un objet sélectionné dans une fenêtre de conception de formulaire ou d’un éditeur de code HTML à l’aide des métadonnées COM + sont affichés dans le **propriétés** fenêtre. Par exemple, vous pouvez sélectionner un bouton et afficher les événements associés, comme un `OnClick` événement, qui peut être liée à ce bouton.

 Les événements affichés dans le **propriétés** fenêtre sont principalement utilisées avec des objets qui sont liés au code. Si vous modifiez un format de fichier qui n’a pas rien à voir avec le code, vous ne souhaitez pas avoir tous les événements. Les événements sont affichés uniquement dans le **propriétés** fenêtre lorsqu’il existe une liaison entre l’exécution de code et certains événements associés à des objets spécifiques. Un exemple serait code-behind d’un objet sélectionné qui s’exécute lorsque cet objet est activé.

 Le tableau suivant répertorie les interfaces principales utilisées par le **propriétés** fenêtre.

|Nom de l’interface|Description|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fournit une liste des catégories pour le **propriétés** fenêtre et mappe chaque propriété à une catégorie.|
|[Interface IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Expose des méthodes et des propriétés à la programmation des outils et autres applications qui prennent en charge d’automation d’un objet.|
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
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
- [Champs et interfaces de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)