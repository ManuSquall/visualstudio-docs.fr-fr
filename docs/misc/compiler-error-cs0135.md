---
title: "Erreur du compilateur CS0135 | Microsoft Docs"
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
  - "CS0135"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0135"
ms.assetid: 1bda402c-e8bd-4117-93d9-f4968d9e8303
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0135
Conflit entre 'declaration1' et la déclaration 'declaration2'  
  
 Le compilateur ne permet pas le masquage de noms, qui génère souvent des erreurs logiques dans votre code.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0135 :  
  
```  
// CS0135.cs  
public class MyClass2  
{  
   public static int i = 0;  
  
   public static void Main()  
   {  
      {  
         int i = 4;  
         i++;  
      }  
      i = 0;   // CS0135  
   }  
}  
```  
  
 D’après la [Spécification du langage C\#](/dotnet/csharp/language-reference/language-specification), section 7.5.2.1 :  
  
 Pour chaque occurrence d’un identificateur donné en tant que nom simple dans une expression ou un déclarateur, dans l’espace de déclaration de variable locale \(§3.3\) qui englobe immédiatement cette occurrence, toutes les autres occurrences du même identificateur en tant que nom simple dans une expression ou un déclarateur doivent faire référence à la même entité. Cette règle permet de s’assurer que la signification d’un nom est toujours identique au sein d’un bloc, d’un bloc switch, d’une instruction for\-, foreach\- ou using, ou d’une fonction anonyme donnés.