---
title: Grille d’affichage des propriétés | Microsoft Docs
description: Découvrez où se trouvent les champs noms de propriété et valeurs de propriété dans la grille de la Fenêtre Propriétés et comment utiliser la grille dans extension des propriétés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee3d7d8d6277f9cfa0352cb4961644e4860b46bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899652"
---
# <a name="properties-display-grid"></a>Grille d’affichage des propriétés

La fenêtre **Propriétés** affiche les champs dans une grille. La colonne de gauche contient les noms des propriétés ; la colonne de droite contient les valeurs de propriété.

## <a name="work-with-the-grid"></a>Utiliser la grille

La liste de deux colonnes affiche des propriétés indépendantes de la configuration qui peuvent être modifiées au moment de la conception et leurs paramètres actuels. Notez que toutes les propriétés peuvent ne pas être affichées. Une propriété peut être définie comme masquée, par exemple en implémentant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> méthode. Plus précisément, pour masquer les propriétés qui ont des propriétés enfants :

1. Définissez le `pfDisplay` paramètre dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> sur `FALSE` .

2. Définissez le `pfHide` paramètre dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> sur `TRUE` .

Pour transmettre des informations à la fenêtre **Propriétés** , l’IDE utilise <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> est appelé par les VSPackages pour chaque fenêtre qui contient des objets sélectionnables avec les propriétés associées à afficher dans la fenêtre **Propriétés** . Implémentation de **Explorateur de solutions** des <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> appels `GetProperty` à l’aide de [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) dans votre hiérarchie de projet pour obtenir les objets consultables dans la hiérarchie.

Si votre VSPackage ne prend pas en charge [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), l’IDE tente d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> à l’aide de la valeur de [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que le ou les éléments de la hiérarchie fournissent.

Votre VSPackage de projet n’a pas besoin d’être créé <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , car le package de fenêtre fourni par l’IDE qui l’implémente (par exemple, **Explorateur de solutions**) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en son nom.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se compose de trois méthodes qui sont appelées par l’IDE :

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contient le nombre d’objets sélectionnés pour être affichés dans la fenêtre **Propriétés** .

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> retourne les `IDispatch` objets sélectionnés pour être affichés dans la fenêtre **Propriétés** .

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> permet à l’utilisateur de sélectionner l’un des objets retournés par <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> l’utilisateur. Cela permet au VSPackage de mettre visuellement à jour la sélection affichée à l’utilisateur dans l’interface utilisateur.

La fenêtre **Propriétés** extrait des informations à partir des `IDispatch` objets pour récupérer les propriétés parcourues. L’Explorateur de propriétés utilise `IDispatch` pour demander à l’objet les propriétés qu’il prend en charge en interrogeant `ITypeInfo` , qui est obtenu à partir de `IDispatch::GetTypeInfo` . Le navigateur utilise ensuite ces valeurs pour remplir la fenêtre **Propriétés** et modifier les valeurs des propriétés individuelles affichées dans la grille. Les informations sur les propriétés sont conservées dans l’objet lui-même.

Étant donné que les objets retournés prennent en charge `IDispatch` , l’appelant peut obtenir des informations telles que le nom de l’objet en appelant `IDispatch::Invoke` ou `ITypeInfo::Invoke` à l’aide d’un identificateur de dispatch (DISPID) prédéfini qui représente les informations souhaitées. Les DISPID déclarés sont négatifs pour s’assurer qu’ils ne sont pas en conflit avec les identificateurs définis par l’utilisateur.

La fenêtre **Propriétés** affiche différents types de champs en fonction des attributs des propriétés spécifiques d’un objet sélectionné. Ces champs incluent des zones d’édition, des listes déroulantes et des liens vers des boîtes de dialogue d’éditeur personnalisées.

- Les valeurs contenues dans une liste énumérée sont récupérées par une <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> requête à `IDispatch` . Les valeurs obtenues à partir d’une liste énumérée peuvent être modifiées dans la grille des propriétés en double-cliquant sur le nom du champ, ou en cliquant sur la valeur et en sélectionnant la nouvelle valeur dans la liste déroulante. Pour les propriétés qui ont des paramètres prédéfinis à partir de listes énumérées, le fait de double-cliquer sur le nom de la propriété dans la liste Propriétés vous fait passer en revue les choix disponibles. Pour les propriétés prédéfinies avec seulement deux options, comme true/false, double-cliquez sur le nom de la propriété pour basculer entre les choix.

- Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> est `false` , indiquant que la valeur a été modifiée, la valeur est affichée en gras. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> est utilisé pour déterminer si la valeur peut être réinitialisée à la valeur d’origine. Dans ce cas, vous pouvez revenir à la valeur par défaut en cliquant avec le bouton droit sur la valeur et en choisissant **Réinitialiser** dans le menu qui s’affiche. Dans le cas contraire, vous devez rétablir manuellement la valeur par défaut. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> vous permet également de localiser et de masquer les noms des propriétés affichées au moment de la conception, mais n’affecte pas les noms de propriété affichés au moment de l’exécution.

- Cliquer sur le bouton des points de suspension (...) affiche la liste des valeurs de propriété à partir desquelles l’utilisateur peut sélectionner (par exemple, un sélecteur de couleurs ou une liste de polices). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> fournit ces valeurs.

## <a name="see-also"></a>Voir aussi

- [Étendre les propriétés](../../extensibility/internals/extending-properties.md)
