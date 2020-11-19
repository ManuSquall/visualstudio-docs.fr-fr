---
title: Changer la notation entre les membres et les associations (Concepteur de classes)
description: Découvrez comment modifier la façon dont le diagramme de classes représente une relation d’association entre deux types, de la notation membre à la notation Association et vice versa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64d26b6ca1c71fe3484544f02006a27866ff4843
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901659"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Guide pratique pour changer la notation entre les membres et les associations dans le Concepteur de classes

Dans **Concepteur de classes**, vous pouvez modifier la façon dont le diagramme de classes représente une relation d’association entre deux types, de la notation membre à la notation Association et vice versa. Les membres affichés sous forme de lignes d’association fournissent souvent une visualisation utile pour comprendre la relation entre les types.

> [!NOTE]
> Les relations d’association peuvent être représentées en tant que champ ou propriété de membre. Pour que vous puissiez passer de la notation membre à la notation association, un type doit avoir un membre d’un autre type. Pour que vous puissiez passer de la notation association à la notation membre, les deux types doivent être connectés par une ligne d’association. Pour plus d’informations, consultez [Guide pratique pour créer des associations entre les types](how-to-create-associations-between-types.md). Si votre projet contient plusieurs diagrammes de classes, les modifications que vous apportez à la façon dont un diagramme affiche les relations d’association n’affectent que ce diagramme. Pour modifier la façon dont un autre diagramme affiche les relations d’association, ouvrez ou affichez le diagramme et effectuez les étapes suivantes.

## <a name="to-change-member-notation-to-association-notation"></a>Pour passer de la notation membre à la notation association

1. Depuis le nœud de projet affiché dans l’Explorateur de solutions, ouvrez le fichier du diagramme de classes (.cd).

2. Dans la forme de type sur le diagramme de classes, cliquez avec le bouton droit sur le champ ou propriété de membre représentant l’association, puis choisissez **Afficher en tant qu’association**.

    > [!TIP]
    > Si aucun champ ou propriété n’est visible dans la forme de type, les compartiments de la forme peuvent être réduits. Pour développer la forme de type, double-cliquez sur le nom du compartiment ou cliquez avec le bouton droit sur la forme de type et choisissez **Développer**.

    Le membre disparaît du compartiment dans la forme de type et une ligne d’association s’affiche pour connecter les deux types. La ligne d’association est étiquetée avec le nom de la propriété ou du champ.

## <a name="to-change-association-notation-to-member-notation"></a>Pour passer de la notation association à la notation membre

Sur le diagramme de classes, cliquez avec le bouton droit sur la ligne d’association, puis choisissez **Afficher en tant que propriété** ou **Afficher en tant que champ** selon le cas. La ligne d’association disparaît, et la propriété s’affiche dans le compartiment approprié au sein de sa forme de type sur le diagramme.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer l’héritage entre les types](how-to-create-inheritance-between-types.md)
- [Guide pratique pour afficher l’héritage entre des types](how-to-view-inheritance-between-types.md)
- [Affichage des types et des relations](designing-and-viewing-classes-and-types.md)
- [Guide pratique pour visualiser une association de collections](how-to-visualize-a-collection-association.md)
