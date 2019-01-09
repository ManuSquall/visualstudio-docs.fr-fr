---
title: Énumérations de Visual C++ dans le concepteur de classes
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: dde9e749a58935e0b50b604897092f69f16300b3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869201"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Énumérations de Visual C++ dans le concepteur de classes

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

- [Utilisation du code Visual C++](working-with-visual-cpp-code.md)
- [Énumérations](/cpp/cpp/enumerations-cpp)