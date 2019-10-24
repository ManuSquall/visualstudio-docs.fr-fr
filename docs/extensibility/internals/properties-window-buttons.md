---
title: Boutons de la fenêtre Propriétés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2a41917a58a6fc5780b62c2c9e3db8aa52d407
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725269"
---
# <a name="properties-window-buttons"></a>Boutons de la fenêtre Propriétés
Selon le langage de développement et le type de produit, certains boutons s’affichent par défaut dans la barre d’outils de la fenêtre **Propriétés** . Dans tous les cas, les boutons **classer**, classer par **alphabet**, **Propriétés**et **pages de propriétés** s’affichent. Dans Visual C# et Visual Basic, le bouton **événements** s’affiche également. Dans certains projets C++ visuels, les boutons **VC + +** et les **remplacements VC** s’affichent. Des boutons supplémentaires peuvent s’afficher pour d’autres types de projets. Pour plus d’informations sur les boutons de la fenêtre **Propriétés** , consultez [fenêtre Propriétés](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implémentation des boutons de la fenêtre Propriétés
 Lorsque vous cliquez sur le bouton **catégorisé** , Visual Studio appelle l’interface <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> sur l’objet qui a le focus pour trier ses propriétés par catégorie. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> est implémenté sur l’objet `IDispatch` présenté dans la fenêtre **Propriétés** .

 Il existe 11 catégories de propriétés prédéfinies, qui ont des valeurs négatives. Vous pouvez définir des catégories personnalisées, mais nous vous recommandons de leur attribuer des valeurs positives pour les distinguer des catégories prédéfinies.

 La méthode <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> retourne la valeur de catégorie de propriété appropriée pour la propriété spécifiée. La méthode <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> retourne une chaîne qui contient le nom de la catégorie. Il vous suffit de fournir la prise en charge des valeurs de catégorie personnalisées, car Visual Studio connaît les valeurs de catégorie de propriété standard.

 Lorsque vous cliquez sur le bouton **alphabétique** , les propriétés sont affichées par ordre alphabétique par nom. Les noms sont récupérés par `IDispatch` selon un algorithme de tri localisé.

 Quand la fenêtre **Propriétés** est ouverte, le bouton **Propriétés** s’affiche automatiquement comme étant sélectionné. Dans d’autres parties de l’environnement, le même bouton s’affiche et vous pouvez cliquer dessus pour afficher la fenêtre **Propriétés** .

 Le bouton **pages de propriétés** n’est pas disponible si `ISpecifyPropertyPages` n’est pas implémenté pour l’objet sélectionné. Les pages de propriétés affichent des propriétés dépendantes de la configuration qui sont généralement associées à des solutions et des projets, mais elles peuvent également être associées à C++des éléments de projet (par exemple, en Visual).

> [!NOTE]
> Vous ne pouvez pas ajouter de boutons de barre d’outils à la fenêtre **Propriétés** à l’aide de code non managé. Pour ajouter un bouton de barre d’outils, vous devez créer un objet managé qui dérive de <xref:System.Windows.Forms.Design.PropertyTab>.

## <a name="see-also"></a>Voir aussi
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)