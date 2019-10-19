---
title: Énumérations de Visual C++ dans le concepteur de classes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f967420e37d6337ce6d86cc56524f2751218f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651662"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Énumérations de Visual C++ dans le concepteur de classes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le Concepteur de classes prend en charge les types `enum` C++ et `enum class` dont la portée est définie. Voici un exemple :

```
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

 Pour plus d’informations sur l’utilisation du type `enum`, consultez [Énumérations](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).

## <a name="see-also"></a>Voir aussi
 Utilisation des [énumérations](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3) [de Code visuel C++ (Concepteur de classes)](../ide/working-with-visual-cpp-code-class-designer.md)
