---
title: "Structures de Visual C++ dans le Concepteur de classes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6f2aa3893a230abd52dd5cf19ed9d751e56e50c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-structures-in-class-designer"></a>Structures de Visual C++ dans le Concepteur de classes
Le Concepteur de classes prend en charge les structures C++ qui sont déclarées avec le mot clé `struct`. Voici un exemple :  
  
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
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|  
  
## <a name="see-also"></a>Voir aussi
[Utilisation du code Visual C++](working-with-visual-cpp-code.md)   
[Classes et structs](/cpp/cpp/classes-and-structs-cpp)   
[struct](/cpp/cpp/struct-cpp)