---
title: Déboguer une violation d’accès C++ | Microsoft Docs
description: Consultez les conseils sur la résolution d’une violation d’accès lorsque plusieurs pointeurs sont candidats. Les versions récentes de Visual Studio renomment le pointeur errant.
ms.custom: SEO-VS-2020, seodec18
ms.date: 02/05/2019
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b0fb7e6f5ae71cf336f9fe206bc7b0208566b615
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398569"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Comment puis-je déboguer une violation d’accès C++ ?

## <a name="problem-description"></a>Description du problème

Mon programme provoque une violation d'accès. Comment puis-je corriger cette erreur ?

## <a name="solution"></a>Solution

Si vous obtenez une violation d’accès sur une ligne de code qui déréférence plusieurs pointeurs, il peut être difficile de trouver le pointeur à l’origine de la violation d’accès. À compter de Visual Studio 2015 Update 1, la boîte de dialogue d’exception nomme désormais de manière explicite le pointeur à l’origine de la violation d’accès.

Par exemple, le code suivant doit générer une violation d’accès :

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

Si vous exécutez ce code dans Visual Studio 2015 Update 1, la boîte de dialogue d’exception suivante doit s’afficher :

![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")

Si vous n’arrivez pas à déterminer la raison pour laquelle le pointeur a provoqué une violation d’accès, tracez le code pour vérifier que le pointeur à l’origine du problème a été correctement assigné.  S’il est passé en tant que paramètre, assurez-vous qu’il est passé correctement et que vous ne créez pas de [copie superficielle](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)par inadvertance. Vérifiez ensuite que les valeurs ne sont pas modifiées de manière non intentionnelle à un endroit du programme. Pour cela, créez un point d’arrêt sur variable pour le pointeur en question pour vous assurer qu’il n’est pas en cours de modification autre part dans le programme. Pour plus d’informations sur les points d’arrêt sur variable, consultez la section consacrée à ce sujet dans [Using Breakpoints](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Voir aussi
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)