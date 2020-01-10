---
title: Animer des objets dans le concepteur XAML
titleSuffix: Blend for Visual Studio
ms.date: 07/31/2019
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ab5be23d2756c1afc38f5ea071fe10a621c5cf2e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593047"
---
# <a name="animate-objects-in-xaml-designer"></a>Animer des objets dans le concepteur XAML

Blend pour Visual Studio vous permet de créer facilement des animations courtes qui déplacent les objets, ou les font apparaître ou disparaître en fondu, par exemple.

Pour créer une animation, vous avez besoin d’un *plan conceptuel*. Un storyboard contient une ou plusieurs *chronologies*. Définissez des *images clés* sur une chronologie pour représenter les modifications apportées aux propriétés. Ensuite, au moment d’exécuter l’animation, Blend pour Visual Studio interpole les modifications apportées aux propriétés au cours de la période désignée. Il en résulte une transition en douceur. Vous pouvez animer n'importe quelle propriété appartenant à un objet, y compris les propriétés non visuelles.

Les illustrations suivantes montrent un plan conceptuel nommé **Storyboard1**. La chronologie contient des images clés qui représentent les positions X et Y d'un rectangle. Quand cette animation s'exécute, le rectangle se déplace en douceur d'une position à un autre.

![Plan conceptuel de l’animation dans Blend pour Visual Studio](media/storyboard-timeline.png)

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

- [Créer une IU à l’aide de Blend pour Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
