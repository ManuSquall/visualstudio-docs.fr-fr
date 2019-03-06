---
title: Opérateur de contexte dans le débogueur (C++) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3c39a9e4f268a0e11d7a0962820b418876e9733b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633536"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Opérateur de contexte dans le débogueur de Visual Studio (C++)
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

- *module* est le nom d’un module. Vous pouvez utiliser un chemin complet pour distinguer les modules portant le même nom.

   Si le chemin du *module* comprend une virgule, un espace incorporé ou une accolade, vous devez utiliser des guillemets au début et à la fin du chemin afin que l’analyseur de contexte reconnaisse la chaîne. Les guillemets simples sont considérés comme faisant partie d’un nom de fichier Windows, c’est pourquoi vous devez utiliser des guillemets doubles. Par exemple :

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *expression* correspond à une expression C++ valide qui correspond à une cible valide, telle qu’un nom de fonction, un nom de variable ou une adresse de pointeur dans *module*.

  Lorsque l’évaluateur d’expression rencontre un symbole dans une expression, il recherche le symbole en procédant dans l’ordre suivant :

1.  Portée lexicale, vers l’extérieur, du bloc actuel (série d’instructions entre accolades) au bloc englobant. Le bloc actuel est le code contenant l’emplacement actuel (adresse du pointeur d’instruction).

2.  Portée de la fonction. La fonction actuelle.

3.  Portée de la classe, si l’emplacement actuel se trouve à l’intérieur d’une fonction membre C++. La portée de la classe comprend toutes les classes de base. L’évaluateur d’expression utilise les règles de dominance classiques.

4.  Symboles globaux dans le module actuel.

5.  Symboles publics dans le programme actuel.