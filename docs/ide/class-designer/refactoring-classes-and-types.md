---
title: Renommer et déplacer des classes et des types dans le Concepteur de classes
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83649a5b2b1053453a36e5ae8ad6f8636112ffd9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069510"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Refactoriser des classes et des types dans le Concepteur de classes

Quand vous refactorisez du code, vous le rendez plus facile à comprendre et à gérer. Vous le rendez également plus efficace en changeant sa structure interne et la conception de ses objets, sans altérer son comportement externe. Utilisez le Concepteur de classes et la fenêtre Détails de classe pour réduire votre charge de travail et limiter le risque d'introduire des bugs quand vous refactorisez du code C#, Visual Basic ou C++ dans votre projet Visual Studio.

> [!NOTE]
> Les fichiers d'un projet peuvent être en lecture seule, car le projet est sous contrôle de code source et n'est pas extrait (projet référencé), ou ses fichiers sont marqués en lecture seule sur le disque. Quand vous travaillez dans un projet ayant l’un de ces états, vous avez plusieurs façons différentes d’enregistrer votre travail. Cela s'applique au code que vous refactorisez et au code que vous changez d'une autre façon, par exemple en le modifiant directement.

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu de support|
|----------| - |
|**Refactoriser des classes :** vous pouvez utiliser les opérations de refactorisation pour fractionner une classe en classes partielles ou pour implémenter une classe de base abstraite.|-   [Guide pratique pour fractionner une classe en classes partielles](how-to-split-a-class-into-partial-classes.md)|
|**Utiliser des interfaces :** Dans le Concepteur de classes, vous pouvez implémenter une interface pour le diagramme de classes en la connectant à une classe qui fournit du code pour les méthodes d’interface.|-   [Guide pratique pour implémenter une interface](how-to-implement-an-interface.md)|
|**Refactoriser des types, des membres de type et des paramètres :** avec le Concepteur de classes, vous pouvez renommer des types, substituer des membres de type ou les déplacer d’un type à un autre. Vous pouvez également créer des types Nullable.|-   [Renommer des types et des membres de type](#rename-types-and-type-members)<br />-   [Déplacer des membres de type d’un type à un autre](#move-type-members-from-one-type-to-another)<br />-   [Guide pratique pour créer un type Nullable](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Renommer des types et des membres de type

Dans le Concepteur de classes, vous pouvez renommer un type ou un membre de type dans le diagramme de classes ou dans la fenêtre **Propriétés**. Dans la fenêtre **Détails de classe**, vous pouvez changer le nom d’un membre mais pas d’un type. Le changement de nom d'un type ou d'un membre de type se propage à toutes les fenêtres et tous les emplacements de code où apparaissait l'ancien nom.

### <a name="rename-in-the-class-designer"></a>Attribuer un nouveau nom dans le Concepteur de classes

1. Dans le diagramme de classes, sélectionnez le type ou le membre, puis sélectionnez le nom.

     Le nom du membre devient modifiable.

2. Tapez le nouveau nom du membre de type ou du type

### <a name="rename-in-the-class-details-window"></a>Attribuer un nouveau nom dans la fenêtre Détails de classe

1. Pour afficher la fenêtre **Détails de classe**, cliquez avec le bouton droit sur le type ou le membre de type, puis sélectionnez **Détails de classe**.

     La fenêtre **Détails de classe** s’affiche.

2. Dans la colonne **Nom** , changez le nom du membre de type.

3. Pour déplacer le focus hors de la cellule, appuyez sur la touche **Entrée** ou cliquez en dehors de la cellule.

    > [!NOTE]
    > Dans la fenêtre **Détails de classe**, vous pouvez changer le nom d’un membre mais pas d’un type.

### <a name="rename-in-the-properties-window"></a>Attribuer un nouveau nom dans la fenêtre Propriétés

1. Dans le diagramme de classes ou la fenêtre **Détails de classe**, cliquez avec le bouton droit sur le type ou le membre, puis sélectionnez **Propriétés**.

     La fenêtre **Propriétés** apparaît et affiche les propriétés du type ou du membre de type.

2. Dans la propriété **Nom** , changez le nom du type ou du membre de type.

     Le nouveau nom se propage à l'ensemble des fenêtres et des emplacements de code du projet actif, où apparaissait l'ancien nom.

## <a name="move-type-members-from-one-type-to-another"></a>Déplacer des membres de type d’un type à un autre

À l’aide du **Concepteur de classes**, vous pouvez déplacer un membre de type d’un type à un autre. Les deux types doivent être visibles dans le diagramme de classes actif.

1. Dans un type visible sur l’aire de conception, cliquez avec le bouton droit sur le membre à déplacer vers un autre type, puis sélectionnez **Couper**.

2. Cliquez avec le bouton droit sur le type de destination, puis sélectionnez **Coller**.

     La propriété est supprimée du type source et apparaît dans le type de destination.

## <a name="see-also"></a>Voir aussi

- [Conception des classes et des types](designing-and-viewing-classes-and-types.md)