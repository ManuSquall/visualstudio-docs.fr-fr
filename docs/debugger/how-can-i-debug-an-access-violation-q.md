---
title: "Comment puis-je d&#233;boguer une violation d&#39;acc&#232;s&#160;? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "violation d'accès (débogage)"
  - "déboguer (Visual Studio), violations d'accès"
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment puis-je d&#233;boguer une violation d&#39;acc&#232;s&#160;?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Description du problème  
 Mon programme provoque une violation d'accès. Comment puis\-je corriger cette erreur ?  
  
## Solution  
 Si vous obtenez une violation d’accès sur une ligne de code qui déréférence plusieurs pointeurs, il peut être difficile de trouver le pointeur à l’origine de la violation d’accès. À compter de Visual Studio 2015 Update 1, la boîte de dialogue d’exception nomme désormais de manière explicite le pointeur à l’origine de la violation d’accès.  
  
 Par exemple, le code suivant doit générer une violation d’accès :  
  
```cpp  
#include <iostream> using namespace std; class ClassB { public: ClassC* C; ClassB() { C = new ClassC(); } void printHello() { cout << "hello world"; } }; class ClassA { public: ClassB* B; ClassA() { B = nullptr; } }; int main() { ClassA* A = new ClassA(); A->B->printHello(); }  
```  
  
 Si vous exécutez ce code dans Visual Studio 2015 Update 1, la boîte de dialogue d’exception suivante doit s’afficher :  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Si vous n’arrivez pas à déterminer la raison pour laquelle le pointeur a provoqué une violation d’accès, tracez le code pour vérifier que le pointeur à l’origine du problème a été correctement assigné.  S’il est passé en tant que paramètre, vérifiez qu’il est passé correctement et qu’une [copie superficielle](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy) n’est pas accidentellement créée. Vérifiez ensuite que les valeurs ne sont pas modifiées de manière non intentionnelle à un endroit du programme. Pour cela, créez un point d’arrêt sur variable pour le pointeur en question pour vous assurer qu’il n’est pas en cours de modification autre part dans le programme. Pour plus d’informations sur les points d’arrêt sur variable, consultez la section consacrée à ce sujet dans [Utilisation des points d'arrêt](../debugger/using-breakpoints.md).  
  
## Voir aussi  
 [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)