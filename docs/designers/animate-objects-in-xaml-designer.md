---
title: Animer des objets dans le concepteur XAML
titleSuffix: Blend for Visual Studio
ms.date: 07/31/2019
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b396c0428f9810fe41fa70aca7b52fba2dd4f5b
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822185"
---
# <a name="animate-objects-in-xaml-designer"></a>Animer des objets dans le concepteur XAML

Blend pour Visual Studio vous permet de créer facilement des animations courtes qui déplacent les objets, ou les font apparaître ou disparaître en fondu, par exemple.

Pour créer une animation, vous avez besoin d’un *plan conceptuel*. Un storyboard contient une ou plusieurs *chronologies*. Définissez des *images clés* sur une chronologie pour représenter les modifications apportées aux propriétés. Ensuite, au moment d’exécuter l’animation, Blend pour Visual Studio interpole les modifications apportées aux propriétés au cours de la période désignée. Il en résulte une transition en douceur. Vous pouvez animer n'importe quelle propriété appartenant à un objet, y compris les propriétés non visuelles.

Les illustrations suivantes montrent un plan conceptuel nommé **Storyboard1**. La chronologie contient des images clés qui représentent les positions X et Y d'un rectangle. Quand cette animation s'exécute, le rectangle se déplace en douceur d'une position à un autre.

![Plan conceptuel de l’animation dans Blend pour Visual Studio](../designers/media/storyboard-timeline.png)

## <a name="create-an-animation"></a>Créer une animation

1. Pour créer un plan conceptuel, sélectionnez le bouton **Options du plan conceptuel** dans la fenêtre **Objets et chronologie**, puis sélectionnez **Nouveau**.

   ![Ajouter un plan conceptuel dans Blend pour Visual Studio](media/new-storyboard.png)

2. Dans la boîte de dialogue **Créer une ressource de plan conceptuel**, entrez un nom pour le plan conceptuel.

3. Dans la panneau **Composants** du mode Création, ajoutez un rectangle en bas à gauche de la page.

   ![Rectangle dans le panneau Composants du concepteur XAML](media/add-rectangle.PNG)

4. Dans la fenêtre **Objets et chronologie**, déplacez le pointeur de couleur jaune sur **3** secondes.

   ![Indicateur de temps dans la chronologie](media/timeline-indicator.PNG)

5. Dans la page en mode Création, faites glisser le rectangle vers la droite de la page.

6. Appuyez sur **Lire** pour voir le rectangle passer de gauche à droite de la page.

Testez les autres modifications qui peuvent être apportées au rectangle, à différents moments. Par exemple, vous pouvez modifier la couleur de remplissage ou changer l’orientation dans la fenêtre Propriétés.

## <a name="see-also"></a>Voir aussi

- [Créer une IU à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)