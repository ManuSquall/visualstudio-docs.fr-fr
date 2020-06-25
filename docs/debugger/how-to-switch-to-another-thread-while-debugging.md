---
title: Basculer vers un autre thread pendant un débogage
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9306e68c7d8906c6956eb5e3810327898bc56567
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348910"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Comment : basculer vers un autre thread pendant le débogage dans Visual Studio (C#, Visual Basic, C++)
Quand vous déboguez une application multithread, vous pouvez utiliser l’une des méthodes suivantes pour basculer du thread que vous avez utilisé à un autre thread.

> [!NOTE]
> Si vous souhaitez contrôler l’ordre dans lequel les threads s’exécutent, vous devez [geler et libérer des threads](../debugger/get-started-debugging-multithreaded-apps.md).

Lorsque vous examinez les threads dans l’éditeur de code et les différentes fenêtres de débogage multithread, la flèche jaune indique le thread actuel. Une flèche verte avec un point d’ancrage signifie qu’un thread non actuel a le contexte du débogueur actuel.

### <a name="to-switch-to-any-thread-that-appears"></a>Pour basculer vers un thread qui s’affiche

- Dans la fenêtre **Threads** ou **Espion parallèle** , double-cliquez sur le thread.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Pour basculer vers un thread dans une fenêtre source

- Dans la marge gauche, cliquez avec le bouton droit sur un ![marqueur](../debugger/media/dbg-thread-marker.png "ThreadMarker")d’icône de marqueur de thread, pointez sur **basculer vers**, puis cliquez sur le nom de ce thread vers lequel vous souhaitez basculer. Le menu contextuel contient uniquement les threads de cet emplacement spécifique.

     Si aucun marqueur de thread n’apparaît, cliquez avec le bouton droit dans la fenêtre **Threads** et vérifiez que **l’option Afficher les threads dans la source** est sélectionnée.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Pour basculer vers un thread dans la barre d'outils Emplacement de débogage

1. Dans la barre d’outils **emplacement de débogage** , cliquez sur la liste **thread** .

2. Dans la liste, cliquez sur le thread vers lequel vous souhaitez basculer.

## <a name="see-also"></a>Voir aussi
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
