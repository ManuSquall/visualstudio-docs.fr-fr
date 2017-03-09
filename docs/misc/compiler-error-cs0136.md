---
title: "Erreur du compilateur CS0136 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0136"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0136"
ms.assetid: 379a1a7d-c52c-4f2b-9e77-c1107d26faf4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0136
Une variable locale nommée 'var' ne peut pas être déclarée dans cette portée car elle modifierait la signification de 'var', déjà utilisée dans une portée  parent ou actuelle\/enfant pour désigner autre chose  
  
 Une déclaration de variable masque une autre déclaration qui serait normalement dans la portée. Renommez la variable déclarée sur la ligne qui a généré l’erreur CS0136.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0136 :  
  
```  
// CS0136.cs  
namespace MyNamespace  
{  
   public class MyClass  
   {  
      public static void Main()  
      {  
         int i = 0;  
         {  
            char i = 'a';   // CS0136, hides int i  
         }  
         i++;  
      }  
   }  
}  
```  
  
 D’après la [Spécification du langage C\#](/dotnet/csharp/language-reference/language-specification), section 7.5.2.1 :  
  
 Pour chaque occurrence d’un identificateur donné en tant que nom simple dans une expression ou un déclarateur, dans l’espace de déclaration de variable locale \(§3.3\) qui englobe immédiatement cette occurrence, toutes les autres occurrences du même identificateur en tant que nom simple dans une expression ou un déclarateur doivent faire référence à la même entité. Cette règle permet de s’assurer que la signification d’un nom est toujours identique au sein d’un bloc, d’un bloc switch, d’une instruction for\-, foreach\- ou using, ou d’une fonction anonyme donnés.