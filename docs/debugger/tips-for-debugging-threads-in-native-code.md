---
title: Conseils pour le débogage de Threads en Code natif | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8ee1f1f2f2029325e3d3b87ca44d05d800a62c07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901873"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Conseils pour le débogage de threads en code natif
Voici quelques conseils que vous utiles pour le débogage de threads en code natif :

- Vous pouvez consulter le contenu du bloc d’informations du thread en entrant `@TIB` dans la fenêtre **Espion** ou dans la boîte de dialogue **Espion express**.

- Vous pouvez consulter le dernier code d’erreur du thread actuel en entrant `@Err` dans la fenêtre **Espion** ou dans la boîte de dialogue **Espion express**.

- Vous pouvez utiliser les fonctions des bibliothèques Runtime C pour déboguer une application multithread. Pour plus d’informations, consultez [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Voir aussi
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)