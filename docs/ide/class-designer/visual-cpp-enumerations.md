---
title: C++Énumérations dans Concepteur de classes
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: a514d5eb4b7f79e2fd193c79de670b6dd9c14cb5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747990"
---
# <a name="c-enumerations-in-class-designer"></a>C++énumérations dans Concepteur de classes

Le **Concepteur de classes** prend en charge les types `enum` C++ et `enum class` dont la portée est définie. Voici un exemple :

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Une forme d’énumération C++ dans un diagramme de classes se présente et fonctionne comme une forme de structure, hormis le fait que l’étiquette indique **Enum** ou **Enum class**, elle est rose plutôt que bleu, et elle comporte une bordure colorée sur les marges gauche et supérieure. Les formes d’énumération et les formes de structure ont des angles carrés.

Pour plus d’informations sur l’utilisation du type `enum`, consultez [Énumérations](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Voir aussi

- [Utilisation du C++ code](working-with-visual-cpp-code.md)
- [Énumérations](/cpp/cpp/enumerations-cpp)