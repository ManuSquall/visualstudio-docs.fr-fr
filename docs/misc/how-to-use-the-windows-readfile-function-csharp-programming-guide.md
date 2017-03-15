---
title: "Comment&#160;: utiliser la fonction ReadFile de Windows (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ReadFile (fonction C#)"
ms.assetid: 46bb53e0-a658-48c9-ae36-6720da7781c1
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "billchi"
manager: "douge"
---
# Comment&#160;: utiliser la fonction ReadFile de Windows (Guide de programmation C#)
Cet exemple illustre la fonction `ReadFile` de Windows en lisant et affichant un fichier texte.  La fonction `ReadFile` nécessite l'utilisation de code `unsafe`, car elle requiert un pointeur comme paramètre.  
  
 Le tableau d'octets passé à la fonction `Read` est un type managé.  Cela signifie que le garbage collector de common language runtime \(CLR\) pourrait déplacer la mémoire utilisée par le tableau.  Pour empêcher ceci, [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) est utilisé pour obtenir un pointeur vers la mémoire et le marquer afin que le garbage collector ne le déplace pas.  À la fin du bloc `fixed`, la mémoire est automatiquement retournée à un état susceptible d'être soumis à parcourir le garbage collection.  
  
 Cette fonction est désignée par le terme « *épinglage déclaratif* ».  L'épinglage est intéressant parce qu'il nécessite très peu de traitement supplémentaire sauf si une opération de garbage collection doit s'opérer sur le bloc `fixed`, ce qui est peu probable.  Toutefois, l'épinglage peut mener à quelques effets secondaires indésirables pendant l'exécution du garbage collection global.  La capacité du garbage collector de condenser la mémoire est limitée grandement par les mémoires tampons épinglées.  Par conséquent, l'épinglage doit être évité si possible.  
  
## Exemple  
 [!code-cs[csProgGuidePointers#2](../misc/codesnippet/CSharp/how-to-use-the-windows-readfile-function-csharp-programming-guide_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](/dotnet/csharp/programming-guide/index)   
 [Référence C\#](/dotnet/csharp/language-reference/index)   
 [Pointeurs et code unsafe](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)   
 [Types pointeur](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)