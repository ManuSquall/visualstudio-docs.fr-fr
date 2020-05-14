---
title: Boutons de fenêtre de propriétés Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706171"
---
# <a name="properties-window-buttons"></a>Boutons de la fenêtre Propriétés
Selon le langage de développement et le type de produit, certains boutons sont affichés par défaut sur la barre d’outils de la fenêtre **Propriétés.** Dans tous les cas, les boutons **Catégorisés,** **Alphabétique,** **Propriétés**et **Pages De propriété** sont affichés. Dans Visual C et Visual Basic, le bouton **Événements** est également affiché. Dans certains projets Visual CMD, les **messages VCMD** et les boutons **VC Overrides** s’affichent. Des boutons supplémentaires peuvent être affichés pour d’autres types de projets. Pour plus d’informations sur les boutons dans la fenêtre **Propriétés,** voir [Properties Window](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Mise en œuvre de boutons de fenêtre propriétés
 Lorsque vous cliquez sur le bouton <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> **Catégorisé,** Visual Studio appelle l’interface sur l’objet qui s’est concentré pour trier ses propriétés par catégorie. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>est implémenté sur l’objet `IDispatch` qui est présenté à la fenêtre **Propriétés.**

 Il y a 11 catégories de propriété prédéfinie, qui ont des valeurs négatives. Vous pouvez définir des catégories personnalisées, mais nous vous recommandons de leur attribuer des valeurs positives pour les distinguer des catégories prédéfinies.

 La <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> méthode renvoie la valeur appropriée de la catégorie de propriété pour la propriété spécifiée. La <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> méthode renvoie une chaîne qui contient le nom de la catégorie. Vous n’avez qu’à fournir un soutien pour les valeurs de catégorie personnalisées parce que Visual Studio connaît les valeurs standard de catégorie de propriété.

 Lorsque vous cliquez sur le bouton **Alphabetized,** les propriétés sont affichées par ordre alphabétique par leur nom. Les noms sont `IDispatch` récupérés selon un algorithme de tri localisé.

 Lorsque la fenêtre **Propriétés** est ouverte, le bouton **Propriétés** est automatiquement affiché tel qu’il est sélectionné. Dans d’autres parties de l’environnement, le même bouton est affiché, et vous pouvez cliquer dessus pour afficher la fenêtre **Propriétés.**

 Le bouton Pages de `ISpecifyPropertyPages` **propriété** n’est pas disponible s’il n’est pas implémenté pour l’objet sélectionné. Les pages de propriété affichent des propriétés dépendantes de la configuration qui sont généralement associées à des solutions et des projets, mais elles peuvent également être associées à des éléments de projet (par exemple, dans Visual CMD).

> [!NOTE]
> Vous ne pouvez pas ajouter des boutons de barre d’outils à la fenêtre **Propriétés** en utilisant du code non menté. Pour ajouter un bouton de barre d’outils, <xref:System.Windows.Forms.Design.PropertyTab>vous devez créer un objet géré qui dérive de .

## <a name="see-also"></a>Voir aussi
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
