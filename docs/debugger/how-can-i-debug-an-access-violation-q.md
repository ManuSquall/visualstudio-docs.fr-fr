---
title: Déboguer une violation d’accès C++ | Microsoft Docs
description: Consultez les conseils sur la résolution d’une violation d’accès lorsque plusieurs pointeurs sont candidats. Les versions récentes de Visual Studio renomment le pointeur errant.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3689942c9db9fde3598590cf30100fc590c50753
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387032"
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

![Capture d’écran d’une boîte de dialogue d’exception Microsoft Visual Studio, montrant une violation d’accès en lecture pour « A->B était nullptr ». Le bouton arrêter est sélectionné.](../debugger/media/accessviolationcplus.png)

Si vous n’arrivez pas à déterminer la raison pour laquelle le pointeur a provoqué une violation d’accès, tracez le code pour vérifier que le pointeur à l’origine du problème a été correctement assigné.  S’il est passé en tant que paramètre, assurez-vous qu’il est passé correctement et que vous ne créez pas de [copie superficielle](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)par inadvertance. Vérifiez ensuite que les valeurs ne sont pas modifiées de manière non intentionnelle à un endroit du programme. Pour cela, créez un point d’arrêt sur variable pour le pointeur en question pour vous assurer qu’il n’est pas en cours de modification autre part dans le programme. Pour plus d’informations sur les points d’arrêt sur variable, consultez la section consacrée à ce sujet dans [Using Breakpoints](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Voir aussi
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)