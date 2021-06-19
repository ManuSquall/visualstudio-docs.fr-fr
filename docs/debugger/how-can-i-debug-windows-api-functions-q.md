---
title: Déboguer les fonctions de l’API Windows | Microsoft Docs
description: Découvrez comment déboguer une fonction API Windows dont les symboles NT sont chargés. Dans le code 32 bits, vous utilisez la forme décorée du nom de la fonction pour définir le point d’arrêt.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89fdbcf9d18a7794e1fb2520384db0f9bcec3147
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386941"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Comment puis-je déboguer des fonctions API Windows ?
Si vous voulez déboguer une fonction API Windows qui a chargé les symboles NT, vous devez effectuer les opérations suivantes.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Pour définir un point d'arrêt sur une fonction API Windows qui a chargé des symboles NT

- Dans le [point d’arrêt sur fonction](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file), entrez le nom de la fonction ainsi que le nom de la dll dans laquelle la fonction réside (consultez [opérateur de contexte](../debugger/context-operator-cpp.md)). Dans du code 32 bits, utilisez la forme décorée du nom de la fonction. Pour définir un point d’arrêt sur **MessageBeep**, par exemple, vous devez entrer ce qui suit.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Pour obtenir le nom décoré, consultez [affichage des noms décorés](/previous-versions/5x49w699(v=vs.140)).

     Vous pouvez tester le nom décoré et l’afficher dans le code machine. Pendant la suspension de la fonction dans le débogueur Visual Studio, cliquez avec le bouton droit sur la fonction dans l’éditeur de code ou dans la fenêtre pile des appels, puis sélectionnez atteindre le code **machine**.

- Dans le code 64 bits, vous pouvez utiliser le nom non décoré.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Voir aussi
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
