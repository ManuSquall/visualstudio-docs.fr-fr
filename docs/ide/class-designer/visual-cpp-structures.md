---
title: Structures de Visual C++ dans le Concepteur de classes
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: e9b8e81ee25e081a324a8520317fa57a1314ccd0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954528"
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