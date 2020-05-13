---
title: Aperçu des fenêtres des propriétés (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706031"
---
# <a name="properties-window-overview"></a>Vue d'ensemble de la fenêtre Propriétés
La fenêtre **Propriétés** est utilisée pour afficher les propriétés des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objets sélectionnés dans les deux principaux types de fenêtres disponibles dans l’environnement de développement intégré (IDE). Ces deux types de fenêtres sont :

- Fenêtres d’outils telles que Solution Explorer, Class View, et le navigateur Objet

- Fenêtres de documents contenant des éditeurs et des concepteurs tels que le concepteur de formulaires, rédacteur en chef de XML, et éditeur DE HTML

## <a name="using-the-properties-window"></a>Utilisation de la fenêtre propriétés
 La fenêtre **Propriété** affiche les propriétés d’éléments sélectionnés ou uniques. Si plusieurs éléments sont sélectionnés, l’intersection de toutes les propriétés pour tous les objets sélectionnés est affichée.

 Les événements liés à un objet sélectionné dans une fenêtre de conception de formulaire ou un éditeur HTML à l’aide de métadonnées COMMD sont affichés dans la fenêtre **Propriétés.** Par exemple, vous pouvez sélectionner un bouton et `OnClick` afficher les événements associés, tels qu’un événement, qui peut être lié à ce bouton.

 Les événements **affichés** dans la fenêtre Propriétés sont principalement utilisés avec des objets qui sont liés au code. Si vous modifiez un format de fichier qui n’a rien à voir avec le code, vous n’allez pas avoir d’événements. Les événements ne s’affichent dans la fenêtre **Propriétés** que lorsqu’il y a une liaison entre le code d’exécution et certains événements associés à des objets spécifiques. Un exemple de ceci serait code derrière un objet sélectionné qui exécute quand cet objet est activé.

 Le tableau suivant répertorie les interfaces primaires utilisées par la fenêtre **Propriétés.**

|Nom de l'interface|Description|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fournit une liste de catégories à la fenêtre **Propriétés** et cartographie chaque propriété à une catégorie.|
|[IDispatch Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Expose les méthodes et les propriétés d’un objet aux outils de programmation et à d’autres applications qui prennent en charge l’automatisation.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fournit l’ellipsis (...) boutons appelés *constructeurs* qui ouvrent des fenêtres de dialogue modal mises en œuvre par l’objet lui-même. Utilisé lorsqu’une valeur n’est pas facilement tapée par l’utilisateur dans un champ de texte. Par exemple, il peut être utilisé pour ouvrir un cueilleur de couleurs qui détermine la valeur RGB pour vous.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Donne accès aux objets utilisés pour mettre à jour les informations affichées dans la fenêtre **Propriétés.** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>est implémenté par VSPackages pour chaque fenêtre qui contient des objets sélectionnables avec des propriétés connexes à afficher.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fournit des informations sur le type d’objet tels que les méthodes d’une interface et les champs d’une structure.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permet à VSPackages de recevoir une notification des événements de sélection et de récupérer des informations sur la hiérarchie actuelle du projet, l’élément, la valeur de l’élément et le contexte de l’interface utilisateur de commande.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fournit à l'environnement l'accès à des sélections multiples.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Utilisé pour fournir des noms localisés sur certaines propriétés affichées dans la fenêtre **Propriétés.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Avertit les VSPackages enregistrés des modifications apportées à la sélection, à la valeur de l'élément ou au contexte de l'interface utilisateur de commande actuels.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Indique à l'environnement une modification de la sélection actuelle et permet d'accéder aux informations sur la hiérarchie et les éléments concernant la nouvelle sélection.|

 Pour plus `IDispatch`d’informations sur , voir la bibliothèque MSDN.

## <a name="see-also"></a>Voir aussi
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
- [Champs et interfaces de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)
