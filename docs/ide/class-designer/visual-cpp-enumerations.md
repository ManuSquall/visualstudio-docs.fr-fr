---
title: C++Énumérations dans Concepteur de classes
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ee56850c05e4b06ea4325ec238e56e99b38978d0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114197"
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
