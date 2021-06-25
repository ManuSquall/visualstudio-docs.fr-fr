---
title: Vue d’ensemble de la fenêtre Propriétés | Microsoft Docs
description: En savoir plus sur les interfaces utilisées pour interagir avec le Fenêtre Propriétés dans l’IDE de Visual Studio dans cette vue d’ensemble.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0b775cbc96303f53bcd795b2121d10af83714e6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899665"
---
# <a name="properties-window-overview"></a>Vue d'ensemble de la fenêtre Propriétés
La fenêtre **Propriétés** permet d’afficher les propriétés des objets sélectionnés dans les deux principaux types de fenêtres disponibles dans l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE). Ces deux types de fenêtres sont les suivants :

- Fenêtres outil, telles que Explorateur de solutions, Affichage de classes et Explorateur d’objets

- Fenêtres de document contenant des éditeurs et des concepteurs tels que le concepteur de formulaires, l’éditeur XML et l’éditeur HTML

## <a name="using-the-properties-window"></a>Utilisation de la fenêtre Propriétés
 La fenêtre **Propriétés** affiche les propriétés d’un ou plusieurs éléments sélectionnés. Si plusieurs éléments sont sélectionnés, l’intersection de toutes les propriétés de tous les objets sélectionnés s’affiche.

 Les événements liés à un objet sélectionné dans une fenêtre de création de formulaire ou un éditeur HTML à l’aide de métadonnées COM+ s’affichent dans la fenêtre **Propriétés** . Par exemple, vous pouvez sélectionner un bouton et afficher ses événements associés, tels qu’un `OnClick` événement, qui peuvent être liés à ce bouton.

 Les événements affichés dans la fenêtre **Propriétés** sont principalement utilisés avec les objets liés au code. Si vous modifiez un format de fichier qui n’a rien à faire avec le code, vous n’allez pas avoir d’événements. Les événements s’affichent uniquement dans la fenêtre **Propriétés** lorsqu’il existe une liaison entre le code en cours d’exécution et certains événements associés à des objets spécifiques. Par exemple, le code se trouve derrière un objet sélectionné qui s’exécute lorsque cet objet est activé.

 Le tableau suivant répertorie les interfaces principales utilisées par la fenêtre **Propriétés** .

|Nom de l'interface|Description|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fournit une liste de catégories à la fenêtre **Propriétés** et mappe chaque propriété à une catégorie.|
|[Interface IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Expose les méthodes et les propriétés d’un objet aux outils de programmation et à d’autres applications qui prennent en charge l’automatisation.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fournit des points de suspension (...) appelés *générateurs* qui ouvrent des fenêtres de dialogue modales implémentées par l’objet lui-même. Utilisé lorsqu’une valeur n’est pas facilement tapée par l’utilisateur dans un champ de texte. Par exemple, il peut être utilisé pour ouvrir un sélecteur de couleurs qui détermine la valeur RVB pour vous.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fournit l’accès aux objets utilisés pour mettre à jour les informations affichées dans la fenêtre **Propriétés** . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> est implémenté par les VSPackages pour chaque fenêtre qui contient des objets sélectionnables avec les propriétés associées à afficher.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fournit des informations sur le type d’un objet, comme les méthodes d’une interface et les champs d’une structure.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permet aux VSPackages de recevoir des notifications d’événements de sélection et de récupérer des informations sur la hiérarchie de projet, l’élément, la valeur d’élément et le contexte de l’interface utilisateur de commande actuels.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fournit à l'environnement l'accès à des sélections multiples.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Utilisé pour fournir des noms localisés sur certaines propriétés affichées dans la fenêtre **Propriétés** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Avertit les VSPackages enregistrés des modifications apportées à la sélection, à la valeur de l'élément ou au contexte de l'interface utilisateur de commande actuels.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Indique à l'environnement une modification de la sélection actuelle et permet d'accéder aux informations sur la hiérarchie et les éléments concernant la nouvelle sélection.|

 Pour plus d’informations sur `IDispatch` , consultez MSDN Library.

## <a name="see-also"></a>Voir aussi
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
- [Champs et interfaces de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)
