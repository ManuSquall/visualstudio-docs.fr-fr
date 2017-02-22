---
title: "Visual C++ Structures in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], structures"
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Structures in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le Concepteur de classes prend en charge des structures C\+\+ qui sont déclarées avec le mot clé `struct`.  Voici un exemple :  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Pour plus d'informations sur l'utilisation du type `struct`, consultez [struct](/visual-cpp/cpp/struct-cpp).  
  
 Une forme de structure de C\+\+ dans un diagramme de classes apparaît et fonctionne comme une forme de classe, mais l'étiquette indique **Struct** et elle comporte des angles carrés et non arrondis.  
  
|Élément de code|Affichage Concepteur de classes|  
|---------------------|-------------------------------------|  
|`struct StructureName {};`|**NomStructure**<br /><br /> Struct|  
  
## Voir aussi  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Classes et structs](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)