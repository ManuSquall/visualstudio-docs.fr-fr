---
title: C++Structures dans Concepteur de classes
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2aa8014835df2b5b2bd3dc68e2aaf0b079e001e8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590682"
---
# <a name="c-structures-in-class-designer"></a>C++structures dans Concepteur de classes

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

|élément de code|Vue Concepteur de classes|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|

## <a name="see-also"></a>Voir aussi

- [Utilisation du C++ code](working-with-visual-cpp-code.md)
- [Classes et structs](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)
