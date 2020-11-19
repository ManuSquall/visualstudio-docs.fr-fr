---
title: 'Comment : implémenter une interface (Concepteur de classes)'
description: Apprenez à implémenter une interface sur le diagramme de classes en la connectant à une classe qui fournit du code pour les méthodes d’interface.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad038774b4acfb7256edbaa35ae4c67cfe835891
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901373"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Guide pratique pour implémenter une interface dans le Concepteur de classes

Dans le **Concepteur de classes**, vous pouvez implémenter une interface pour le diagramme de classes en la connectant à une classe qui fournit du code pour les méthodes d’interface. Le **Concepteur de classes** génère une implémentation d’interface et affiche la relation entre l’interface et la classe sous la forme d’une relation d’héritage. Vous pouvez implémenter une interface en dessinant une ligne d’héritage entre l’interface et la classe ou en faisant glisser l’interface à partir de l’Affichage de classes.

> [!TIP]
> Vous pouvez créer des interfaces de la même façon que vous créez d’autres types. Si l’interface existe mais n’apparaît pas dans le diagramme de classes, affichez-la d’abord. Pour plus d’informations, consultez [Guide pratique pour créer des types à l’aide du Concepteur de classes](how-to-create-types.md) et [Guide pratique pour afficher les types existants](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Pour implémenter une interface en dessinant une ligne d’héritage

1. Sur le diagramme de classes, affichez l’interface et la classe qui implémente cette interface.

2. Dessinez une ligne d’héritage entre la classe et l’interface.

     Un symbole d’interface (lollipop) attaché à la classe s’affiche, et une étiquette avec le nom de l’interface identifie la relation d’héritage. Visual Studio génère des stubs pour tous les membres de l’interface.

Pour plus d’informations, consultez [Guide pratique pour créer un héritage entre les types](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Pour implémenter une interface à partir de la fenêtre Affichage de classes

1. Sur le diagramme de classes, affichez la classe choisie pour implémenter cette interface.

2. Ouvrez **affichage de classes** et recherchez l’interface.

    > [!TIP]
    > Si **l’Affichage de classes** n’est pas ouvert, ouvrez **l’Affichage de classes** à partir du menu **Affichage** ou appuyez sur **Ctrl**+**Maj**+**C**.

3. Faites glisser le nœud de l’interface vers la forme de classe sur le diagramme.

     Un symbole d’interface (lollipop) attaché à la classe s’affiche, et une étiquette avec le nom de l’interface identifie la relation d’héritage. Visual Studio génère des stubs pour tous les membres de l’interface. L’interface est maintenant implémentée.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des types à l’aide du Concepteur de classes](how-to-create-types.md)
- [Guide pratique pour afficher les types existants](how-to-view-existing-types.md)
- [Guide pratique pour créer l’héritage entre les types](how-to-create-inheritance-between-types.md)
- [Refactorisation des classes et des types](refactoring-classes-and-types.md)
