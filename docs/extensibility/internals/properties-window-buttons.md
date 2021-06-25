---
title: Boutons de la fenêtre Propriétés | Microsoft Docs
description: En savoir plus sur les boutons affichés par défaut dans la barre d’outils de la Fenêtre Propriétés et sur l’implémentation des boutons.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c45d6cf0f271683c3c708bd71ef46377a5c5ca
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903448"
---
# <a name="properties-window-buttons"></a>Boutons de la fenêtre Propriétés
Selon le langage de développement et le type de produit, certains boutons s’affichent par défaut dans la barre d’outils de la fenêtre **Propriétés** . Dans tous les cas, les boutons **classer**, classer par **alphabet**, **Propriétés** et **pages de propriétés** s’affichent. En Visual C# et Visual Basic, le bouton **événements** s’affiche également. Dans certains projets Visual C++, les boutons **VC + +** et les **remplacements VC** s’affichent. Des boutons supplémentaires peuvent s’afficher pour d’autres types de projets. Pour plus d’informations sur les boutons de la fenêtre **Propriétés** , consultez [fenêtre Propriétés](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implémentation des boutons de la fenêtre Propriétés
 Lorsque vous cliquez sur le bouton **catégorisé** , Visual Studio appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interface sur l’objet qui a le focus pour trier ses propriétés par catégorie. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> est implémenté sur l' `IDispatch` objet présenté dans la fenêtre **Propriétés** .

 Il existe 11 catégories de propriétés prédéfinies, qui ont des valeurs négatives. Vous pouvez définir des catégories personnalisées, mais nous vous recommandons de leur attribuer des valeurs positives pour les distinguer des catégories prédéfinies.

 La <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> méthode retourne la valeur de catégorie de propriété appropriée pour la propriété spécifiée. La <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> méthode retourne une chaîne qui contient le nom de la catégorie. Il vous suffit de fournir la prise en charge des valeurs de catégorie personnalisées, car Visual Studio connaît les valeurs de catégorie de propriété standard.

 Lorsque vous cliquez sur le bouton **alphabétique** , les propriétés sont affichées par ordre alphabétique par nom. Les noms sont récupérés par `IDispatch` selon un algorithme de tri localisé.

 Quand la fenêtre **Propriétés** est ouverte, le bouton **Propriétés** s’affiche automatiquement comme étant sélectionné. Dans d’autres parties de l’environnement, le même bouton s’affiche et vous pouvez cliquer dessus pour afficher la fenêtre **Propriétés** .

 Le bouton **pages de propriétés** n’est pas disponible si `ISpecifyPropertyPages` n’est pas implémenté pour l’objet sélectionné. Les pages de propriétés affichent des propriétés dépendantes de la configuration qui sont généralement associées à des solutions et des projets, mais elles peuvent également être associées à des éléments de projet (par exemple, dans Visual C++).

> [!NOTE]
> Vous ne pouvez pas ajouter de boutons de barre d’outils à la fenêtre **Propriétés** à l’aide de code non managé. Pour ajouter un bouton de barre d’outils, vous devez créer un objet managé qui dérive de <xref:System.Windows.Forms.Design.PropertyTab> .

## <a name="see-also"></a>Voir aussi
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
