---
title: Conseils pour le débogage de Threads en Code natif | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 72b913c64d78966bde96419978a066cc9921ebaa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Conseils pour le débogage de threads en code natif
Voici quelques conseils que vous utiles pour le débogage de threads en code natif :  
  
-   Vous pouvez afficher le contenu du bloc d’informations du Thread en tapant `@TIB` dans les **espion** fenêtre ou **Espion express** boîte de dialogue.  
  
-   Vous pouvez afficher le dernier code d’erreur pour le thread actuel en entrant `@Err` dans les **espion** fenêtre ou **Espion express** boîte de dialogue.  
  
-   Vous pouvez utiliser les fonctions des bibliothèques Runtime C pour déboguer une application multithread. Pour plus d’informations, consultez [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)