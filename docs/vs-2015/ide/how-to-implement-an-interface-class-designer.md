---
title: Guide pratique pour implémenter une interface (Concepteur de classes) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b750830e8263d0016f52a71ad4eac8c6950eda8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651862"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Comment : implémenter une interface (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le Concepteur de classes, vous pouvez implémenter une interface pour le diagramme de classes en la connectant à une classe qui fournit du code pour les méthodes d’interface. Le Concepteur de classes génère une implémentation d’interface et affiche la relation entre l’interface et la classe sous la forme d’une relation d’héritage. Vous pouvez implémenter une interface en dessinant une ligne d’héritage entre l’interface et la classe ou en faisant glisser l’interface à partir de l’Affichage de classes.

> [!TIP]
> Vous pouvez créer des interfaces de la même façon que vous créez d’autres types. Si l’interface existe mais n’apparaît pas dans le diagramme de classes, affichez-la d’abord. Pour plus d’informations, consultez [Guide pratique pour créer des types à l’aide du Concepteur de classes](../ide/how-to-create-types-by-using-class-designer.md) et [Guide pratique pour afficher des types existants (Concepteur de classes)](../ide/how-to-view-existing-types-class-designer.md).

### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Pour implémenter une interface en dessinant une ligne d’héritage

1. Sur le diagramme de classes, affichez l’interface et la classe qui implémente cette interface.

2. Dessinez une ligne d’héritage entre la classe et l’interface.

    Un symbole d’interface (lollipop) attaché à la classe s’affiche, et une étiquette avec le nom de l’interface identifie la relation d’héritage. Visual Studio génère des stubs pour tous les membres de l’interface.

   Pour plus d’informations, consultez [Guide pratique pour créer un héritage entre les types (Concepteur de classes)](../ide/how-to-create-inheritance-between-types-class-designer.md).

### <a name="to-implement-an-interface-from-the-class-view-window"></a>Pour implémenter une interface à partir de la fenêtre Affichage de classes

1. Sur le diagramme de classes, affichez la classe choisie pour implémenter cette interface.

2. Ouvrez l’Affichage de classes et recherchez l’interface.

    > [!TIP]
    > Si l’Affichage de classes n’est pas ouvert, ouvrez-le depuis le menu **Affichage**. Pour plus d’informations sur l’affichage des classes, consultez [Affichage des classes et de leurs membres](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

3. Faites glisser le nœud de l’interface vers la forme de classe sur le diagramme.

     Un symbole d’interface (lollipop) attaché à la classe s’affiche, et une étiquette avec le nom de l’interface identifie la relation d’héritage. Visual Studio génère des stubs pour tous les membres de l’interface. L’interface est maintenant implémentée.

## <a name="see-also"></a>Voir aussi
 [Comment : créer des types à l’aide de concepteur de classes](../ide/how-to-create-types-by-using-class-designer.md) [Comment : afficher des types existants (Concepteur de classes)](../ide/how-to-view-existing-types-class-designer.md) [Comment : créer un héritage entre des types (Concepteur de classes)](../ide/how-to-create-inheritance-between-types-class-designer.md) [refactorisation des classes et des types (Concepteur de classes)](../ide/refactoring-classes-and-types-class-designer.md)
