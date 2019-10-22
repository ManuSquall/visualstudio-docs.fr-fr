---
title: Structures de Visual C++ dans le Concepteur de classes
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: da786e6f598b4b28aeb7758df41f54ea23c4185d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647592"
---
# <a name="visual-c-structures-in-class-designer"></a>Structures de Visual C++ dans le Concepteur de classes

Le **Concepteur de classes** prend en charge les structures C++ qui sont déclarées avec le mot clé `struct`. Voici un exemple :

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Pour plus d’informations sur l’utilisation du type `struct`, consultez [struct](/cpp/cpp/struct-cpp).

Une forme de structure C++ dans un diagramme de classes apparaît. Elle fonctionne comme une forme de classe, mais l’étiquette indique **Struct** et ses angles sont carrés, et non pas arrondis.

|Élément de code|Vue Concepteur de classes|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|

## <a name="see-also"></a>Voir aussi

- [Utilisation du code Visual C++](working-with-visual-cpp-code.md)
- [Classes et structs](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)