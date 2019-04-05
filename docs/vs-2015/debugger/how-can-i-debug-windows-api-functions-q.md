---
title: Comment puis-je déboguer des fonctions API Windows ? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb57f2d46eb103c6b59805ae15bc339b7e3bdc84
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952680"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Comment puis-je déboguer des fonctions API Windows ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous voulez déboguer une fonction API Windows qui a chargé les symboles NT, vous devez effectuer les opérations suivantes.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Pour définir un point d'arrêt sur une fonction API Windows qui a chargé des symboles NT  
  
-   Entrez le nom de la fonction ainsi que le nom du fichier DLL dans lequel la fonction réside. Dans du code 32 bits, utilisez la forme décorée du nom de la fonction. Pour définir un point d’arrêt sur **MessageBeep**, par exemple, vous devez entrer ce qui suit.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Pour obtenir le nom décoré, consultez [affichage de noms décorés](http://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Voir aussi  
 [Questions fréquentes (FAQ) sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
