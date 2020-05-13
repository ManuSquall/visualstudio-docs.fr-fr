---
title: Grille d’affichage des propriétés (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706191"
---
# <a name="properties-display-grid"></a>Grille d’affichage des propriétés

La fenêtre **Properties** affiche les champs à l’intérieur d’une grille. La colonne de gauche contient les noms de propriété; la colonne de droite contient les valeurs de la propriété.

## <a name="work-with-the-grid"></a>Travailler avec la grille

La liste de deux colonnes affiche les propriétés indépendantes de configuration qui peuvent être modifiées au moment de la conception et leurs paramètres actuels. Notez que toutes les propriétés peuvent ne pas être affichées. Une propriété peut être définie comme cachée, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> par exemple, en mettant en œuvre la méthode. Plus précisément, pour cacher les propriétés qui ont des propriétés enfant:

1. Définissez `pfDisplay` le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> `FALSE`paramètre pour .

2. Définissez `pfHide` le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> `TRUE`paramètre pour .

Pour pousser l’information à la <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>fenêtre **Propriétés,** l’IDE utilise . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>est appelé par VSPackages pour chaque fenêtre qui contient des objets sélectionnables avec des propriétés connexes à afficher dans la fenêtre **propriétés.** **Solution Explorer**La mise en <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> œuvre des appels `GetProperty` par Solution Explorer à [l’aide de __VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) dans votre hiérarchie de projet pour acquérir les objets de navigation dans la hiérarchie.

Si votre VSPackage ne prend pas en charge [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), l’IDE tente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> d’utiliser la valeur pour [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que l’élément de hiérarchie ou les éléments fournissent.

Votre projet VSPackage n’a pas besoin de créer <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> parce que le package de fenêtre fourni par IDE qui l’implémente (par exemple, Solution **Explorer**) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en son nom.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>se compose de trois méthodes qui sont appelées par l’IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>contient le nombre d’objets sélectionnés pour être affichés dans la fenêtre **Propriétés.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>retourne `IDispatch` les objets sélectionnés pour être affichés dans la fenêtre **Propriétés.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>permet à l’un ou <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> l’autre des objets retournés par être sélectionnés par l’utilisateur. Cela permet à l’emballage VS de mettre à jour visuellement la sélection affichée à l’utilisateur dans l’interface utilisateur.

La fenêtre **Properties** extrait `IDispatch` des informations des objets pour récupérer les propriétés parcourues. Le navigateur `IDispatch` Properties utilise pour demander à l’objet quelles propriétés il prend en charge en interrogeant `ITypeInfo`, qui est obtenu à partir de `IDispatch::GetTypeInfo`. Le navigateur utilise ensuite ces valeurs pour remplir la fenêtre **Propriétés** et modifier les valeurs des propriétés individuelles affichées dans la grille. Les informations sur les propriétés sont maintenues dans l’objet lui-même.

Étant donné que `IDispatch`les objets retournés prennent en charge, l’appelant peut obtenir des informations telles que le nom de l’objet en appelant l’un ou l’autre `IDispatch::Invoke` ou `ITypeInfo::Invoke` avec un identifiant de répartition prédéfini (DISPID) qui représente les informations souhaitées. Les DISPID déclarés sont négatifs pour s’assurer qu’ils ne sont pas en conflit avec les identifiants définis par l’utilisateur.

La fenêtre **Propriété** affiche différents types de champs en fonction des attributs des propriétés spécifiques d’un objet sélectionné. Ces champs comprennent des boîtes d’édition, des listes d’abandon et des liens vers des boîtes de dialogue d’éditeurs personnalisées.

- Les valeurs contenues dans une liste <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> énumérée `IDispatch`sont récupérées par une requête à . Les valeurs obtenues à partir d’une liste énumérée peuvent être modifiées dans la grille des propriétés en cliquant à deux clics sur le nom de champ, ou en cliquant sur la valeur et en sélectionnant la nouvelle valeur de la liste d’abandon. Pour les propriétés qui ont prédéfinis les paramètres des listes énumérées, en double clic le nom de propriété dans les cycles de liste propriétés à travers les choix disponibles. Pour les propriétés prédéfinies avec seulement deux choix, tels que vrai / faux, double-cliquez sur le nom de la propriété pour passer entre les choix.

- Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false`c’est, indiquant que la valeur a été changée, la valeur est affichée dans le texte en gras. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>est utilisé pour déterminer si la valeur peut être réinitialisée à la valeur d’origine. Si c’est le cas, vous pouvez revenir à la valeur par défaut en cliquant à droite sur la valeur et en choisissant **Reset** dans le menu affiché. Dans le cas contraire, vous devez changer la valeur de nouveau à la valeur manuellement. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>vous permet également de localiser et de masquer les noms des propriétés affichées pendant le temps de conception, mais n’affecte pas les noms de propriété affichés pendant le temps d’exécution.

- En cliquant sur le bouton ellipsis (...) affiche une liste des valeurs de propriété à partir desquelles l’utilisateur peut sélectionner (comme un cueilleur de couleurs ou une liste de polices). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>fournit ces valeurs.

## <a name="see-also"></a>Voir aussi

- [Étendre les propriétés](../../extensibility/internals/extending-properties.md)
