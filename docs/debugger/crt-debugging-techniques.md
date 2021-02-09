---
title: Techniques de débogage CRT | Microsoft Docs
description: Vous pouvez utiliser différentes techniques pour déboguer un programme qui utilise la bibliothèque Runtime C (CRT). Utilisez cet article et ses liens pour en savoir plus sur ces techniques.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84d5f85584403cc18cd00708a8d4698723d614ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857608"
---
# <a name="crt-debugging-techniques"></a>Techniques de débogage CRT
Si vous déboguez un programme qui utilise la bibliothèque Runtime C, ces techniques de débogage peuvent se révéler utiles.

## <a name="in-this-section"></a>Dans cette section
 [Utilisation de la bibliothèque de débogage CRT](../debugger/crt-debug-library-use.md)

 Décrit la prise en charge du débogage fournie par la bibliothèque Runtime C et fournit des instructions pour accéder aux outils.

 [Macros pour la création de rapports](../debugger/macros-for-reporting.md)

 Fournit des informations sur les macros **_RPTn** et **_RPTFn**, définies dans CRTDBG.H, qui remplacent les instructions `printf` pour le débogage.

 [Versions Debug des fonctions d’allocation du tas](../debugger/debug-versions-of-heap-allocation-functions.md)

 Aborde les versions Debug spéciales des fonctions d'allocation de tas, y compris la façon dont le CRT mappe les appels, les avantages liés à un appel explicite, la façon d'éviter la conversion, le suivi des différents types d'allocations dans les blocs clients et les résultats si vous ne définissez pas _DEBUG.

 [Détails du tas de débogage CRT](../debugger/crt-debug-heap-details.md)

 Fournit des liens vers la gestion de la mémoire et le tas de débogage, les types de bloc sur le tas de débogage, l'utilisation du tas de débogage, les fonctions de création de rapports sur l'état du tas et le suivi des demandes d'allocation du tas.

 [Écriture de la fonction de raccordement de débogage](../debugger/debug-hook-function-writing.md)

 Répertorie les liens vers les fonctions de raccordement de bloc client, les fonctions de raccordement d'allocation, les raccordements d'allocation et les allocations de la mémoire runtime C, ainsi que les fonctions de raccordement de rapport.

 [Recherche de fuites de mémoire à l'aide de la bibliothèque CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)

 Décrit les techniques de détection et d'identification des fuites de mémoire à l'aide du débogueur et de la bibliothèque runtime C.

## <a name="related-sections"></a>Sections connexes

- [Débogage de code natif](../debugger/debugging-native-code.md) : décrit certains problèmes et techniques de débogage courants pour les applications C et C++.
- [Sécurité du débogueur](../debugger/debugger-security.md) : fournit des recommandations pour un débogage plus sécurisé.