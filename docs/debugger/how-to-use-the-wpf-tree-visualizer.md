---
title: 'Procédure : Utiliser le visualiseur de l’arborescence WPF | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da18990620644834192c38c24ced9a25ecb56215
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071263"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Procédure : Utiliser le visualiseur de l’arborescence WPF
Vous pouvez utiliser le visualiseur de l'arborescence WPF pour explorer l'arborescence d'éléments visuels d'un objet WPF et visualiser les propriétés de dépendance WPF pour les objets contenus dans cette arborescence. Pour plus d’informations sur les arborescences d’éléments visuels, consultez [arborescences dans WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Lorsque vous ouvrez le visualiseur de l’arborescence WPF, vous verrez deux volets : le **arborescence d’éléments visuels** sur la gauche et le **propriétés de** _nom_**:**  _Type_ volet de droite. Sélectionnez n’importe quel objet dans le **arborescence d’éléments visuels** volet et le **propriétés de** _nom_**:**_Type_ volet est mise à jour automatiquement pour afficher les propriétés pour cet objet.

### <a name="to-open-the-wpf-tree-visualizer"></a>Pour ouvrir le visualiseur de l’arborescence WPF

1. Dans la fenêtre **Espion**, **Automatique** ou **Variables locales** d’un DataTip, cliquez sur la flèche à côté de l’icône de loupe située en regard d’un nom d’objet WPF.

     Une liste de visualiseurs s'affiche.

2. Cliquez sur **Visualiseur de l’arborescence WPF**.

### <a name="to-search-the-visual-tree"></a>Pour effectuer une recherche sur l'arborescence d'éléments visuels

- Dans le volet **Arborescence d’éléments visuels**, tapez la chaîne que vous souhaitez rechercher dans la zone **Recherche**.

     Le visualiseur de l’arborescence WPF recherche immédiatement le premier objet de l’arborescence d’éléments visuels qui correspond à la chaîne que vous avez tapée. Tapez plus de caractères pour rechercher une correspondance plus pertinente.

    - Cliquez sur **Suivant** pour accéder à la correspondance suivante de l’arborescence d’éléments visuels.

    - Cliquez sur **Préc.** pour revenir à la correspondance précédente.

    - Cliquez sur **Effacer** pour effacer les critères de recherche.

### <a name="to-search-the-properties-list"></a>Pour effectuer une recherche sur la liste des propriétés

- Dans le **propriétés de** _nom_**:**_Type_ volet, tapez la chaîne que vous souhaitez rechercher dans le **filtrer**boîte.

     Le visualiseur de l'arborescence WPF recherche immédiatement les propriétés qui correspondent à la chaîne que vous avez tapée. À présent, la liste n'affiche que les propriétés correspondant à la chaîne que vous avez tapée. Tapez plus de caractères pour rechercher une correspondance plus pertinente.

    - Cliquez sur **Effacer** pour effacer les critères de recherche.

### <a name="to-close-the-visualizer"></a>Pour fermer le visualiseur

- Cliquez sur l’icône **Fermer** située dans le coin supérieur droit de la boîte de dialogue.

## <a name="see-also"></a>Voir aussi
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
- [Arborescences dans WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Vue d’ensemble des propriétés de dépendance](/dotnet/framework/wpf/advanced/dependency-properties-overview)
