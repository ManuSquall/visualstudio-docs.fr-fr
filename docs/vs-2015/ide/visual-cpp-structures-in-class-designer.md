---
title: Structures de Visual C++ dans le Concepteur de classes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 19ffa241fdc1f58500c7065e2cee2a33340e33f8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54794468"
---
# <a name="visual-c-structures-in-class-designer"></a>Structures de Visual C++ dans le Concepteur de classes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le Concepteur de classes prend en charge les structures C++ qui sont déclarées avec le mot clé `struct`. Voici un exemple :  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Pour plus d’informations sur l’utilisation du type `struct`, consultez [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).  
  
 Une forme de structure C++ dans un diagramme de classes apparaît. Elle fonctionne comme une forme de classe, mais l’étiquette indique **Struct** et ses angles sont carrés, et non pas arrondis.  
  
|Élément de code|Vue Concepteur de classes|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du code Visual C++ (Concepteur de classes)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Classes et structs](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)
