---
title: Conseils pour le débogage de Threads en Code natif | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c299d3585d9089f8525c2ec7f470601797cc3a2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684873"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Conseils pour le débogage de threads en code natif
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Voici quelques conseils que vous utiles pour le débogage de threads en code natif :  
  
- Vous pouvez consulter le contenu du bloc d’informations du thread en entrant `@TIB` dans la fenêtre **Espion** ou dans la boîte de dialogue **Espion express**.  
  
- Vous pouvez consulter le dernier code d’erreur du thread actuel en entrant `@Err` dans la fenêtre **Espion** ou dans la boîte de dialogue **Espion express**.  
  
- Vous pouvez utiliser les fonctions des bibliothèques Runtime C pour déboguer une application multithread. Pour plus d’informations, consultez [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
