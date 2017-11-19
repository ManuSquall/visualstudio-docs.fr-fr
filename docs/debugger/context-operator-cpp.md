---
title: "Opérateur de contexte dans le débogueur (C++) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fc52fb07cd4da994df07410953787272e3cb724
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Opérateur de contexte dans le débogueur Visual Studio (C++)
Vous pouvez utiliser l’opérateur de contexte en C++ pour qualifier l’emplacement d’un point d’arrêt, un nom de variable ou une expression. L’opérateur de contexte est utile pour spécifier un nom issu d’une portée externe qui serait sinon masqué par un nom local.  
  
##  <a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Syntaxe  
 Il existe deux façons de spécifier le contexte :  
  
1.  {,,[*module*] } *expression*  
  
     Les accolades doivent contenir deux virgules et le nom ou le chemin complet du module (fichier exécutable ou DLL).  
  
     Par exemple, pour définir un point d’arrêt dans la fonction `SomeFunction` de EXAMPLE.dll :  
  
    ```C++  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2.  *module*!*expression*  
  
    ```C++  
    EXAMPLE.dll!SomeFunction  
    ```  
  
-   *module* est le nom d’un module. Vous pouvez utiliser un chemin complet pour distinguer les modules portant le même nom.  
  
     Si le chemin du *module* comprend une virgule, un espace incorporé ou une accolade, vous devez utiliser des guillemets au début et à la fin du chemin afin que l’analyseur de contexte reconnaisse la chaîne. Les guillemets simples sont considérés comme faisant partie d’un nom de fichier Windows, c’est pourquoi vous devez utiliser des guillemets doubles. Par exemple :  
  
    ```C++  
    {,,"a long, long, library name.dll"} g_Var  
    ```  
  
-   *expression* correspond à une expression C++ valide qui correspond à une cible valide, telle qu’un nom de fonction, un nom de variable ou une adresse de pointeur dans *module*.  
  
 Lorsque l’évaluateur d’expression rencontre un symbole dans une expression, il recherche le symbole en procédant dans l’ordre suivant :  
  
1.  Portée lexicale, vers l’extérieur, du bloc actuel (série d’instructions entre accolades) au bloc englobant. Le bloc actuel est le code contenant l’emplacement actuel (adresse du pointeur d’instruction).  
  
2.  Portée de la fonction. La fonction actuelle.  
  
3.  Portée de la classe, si l’emplacement actuel se trouve à l’intérieur d’une fonction membre C++. La portée de la classe comprend toutes les classes de base. L’évaluateur d’expression utilise les règles de dominance classiques.  
  
4.  Symboles globaux dans le module actuel.  
  
5.  Symboles publics dans le programme actuel.