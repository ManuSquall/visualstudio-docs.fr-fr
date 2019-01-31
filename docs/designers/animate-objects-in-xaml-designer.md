---
title: Animer des objets dans le concepteur XAML
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: f6fbeceeb0c9943e561c5bd4e353551005be23a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960202"
---
# <a name="animate-objects-in-xaml-designer"></a>Animer des objets dans le concepteur XAML

Vous pouvez créer des animations courtes qui déplacent des objets ou les font apparaître ou disparaître en fondu.

Pour commencer, créez un *storyboard*. Un storyboard contient une ou plusieurs *chronologies*. Définissez des *images clés* sur une chronologie pour représenter les modifications apportées aux propriétés. Ensuite, au moment d'exécuter l'animation, Blend interpole les modifications apportées aux propriétés au cours de la période désignée. Il en résulte une transition en douceur. Vous pouvez animer n'importe quelle propriété appartenant à un objet, y compris les propriétés non visuelles.

L'illustration suivante montre un storyboard nommé **MoveUp**. La chronologie contient des images clés qui représentent les positions X et Y d'un rectangle. Quand cette animation s'exécute, le rectangle se déplace en douceur d'une position à un autre.

![Plan conceptuel MoveUp dans le concepteur XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Voir aussi

- [Créer une IU à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)