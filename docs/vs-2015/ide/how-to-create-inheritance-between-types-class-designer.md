---
title: 'Procédure : Créer un héritage entre les types (Concepteur de classes) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba27b32cc322da2e14cec86b878a7dd42dae0039
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668103"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Procédure : Créer l’héritage entre les types (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour créer une relation d'héritage entre deux types sur un diagramme de classes à l'aide du Concepteur de classes, connectez le type de base à son ou ses types dérivés. Vous pouvez avoir une relation d'héritage entre deux classes, entre une classe et une interface ou entre deux interfaces.

### <a name="to-create-an-inheritance-between-types"></a>Pour créer un héritage entre des types

1. Depuis votre projet affiché dans l'Explorateur de solutions, ouvrez le fichier du diagramme de classes (.cd).

     Si vous n'avez pas de diagramme de classes, créez-en un. Voir [Guide pratique pour Ajoutez des diagrammes de classes à des projets (Concepteur de classes) ](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. Dans la **boîte à outil**, sous **Concepteur de classes**, cliquez sur **Héritage**.

3. Dans le diagramme de classes, dessinez une ligne d'héritage entre les types de votre choix, depuis :

    - une classe dérivée vers la classe de base ;

    - une classe d'implémentation vers l'interface implémentée ;

    - une interface d'extension vers l'interface étendue.

4. Éventuellement, dans le cas d'un type dérivé d'un type générique, cliquez sur la ligne d'héritage. Dans la fenêtre **Propriétés**, définissez la propriété **Arguments de type** sur le type souhaité pour le type générique.

    > [!NOTE]
    > Si une classe abstraite parente contient au moins un membre abstrait, tous les membres abstraits sont implémentés en tant que classes d'héritage non abstraites.
    >
    >  Bien que vous puissiez visualiser les types génériques existants, vous ne pouvez pas créer de types génériques. En outre, vous ne pouvez pas modifier les paramètres des types génériques existants.

## <a name="see-also"></a>Voir aussi
 [Notions de base de l’héritage](https://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5) de [l’héritage](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea) [How à : Afficher l’héritage entre les types (Concepteur de classes) ](../ide/how-to-view-inheritance-between-types-class-designer.md) les [classes visuelles C++ dans Concepteur de classes](../ide/visual-cpp-classes-in-class-designer.md)
