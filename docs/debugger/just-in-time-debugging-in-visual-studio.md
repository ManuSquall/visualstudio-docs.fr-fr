---
title: 'Comment : répondre au débogueur juste-à-temps | Documents Microsoft'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b97e2d6b9ca269a86c3b66ffbcc4bb441051f29
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454660"
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Comment : répondre au débogueur juste-à-temps

Les actions à entreprendre lorsque vous consultez juste-à-temps débogueur boîte de dialogue varient selon que vous essayez de faire :

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Si vous souhaitez corriger ou déboguer l’erreur (utilisateurs de Visual Studio)

- Vous devez avoir [installé Visual Studio](http://www.visualstudio.com) pour afficher des informations détaillées sur l’erreur et essayez de déboguer. Pour plus d’informations, consultez [déboguer à l’aide du débogueur juste à temps](../debugger/debug-using-the-just-in-time-debugger.md). Si vous ne pouvez pas résoudre l’erreur et corriger l’application, contactez le propriétaire de l’application pour résoudre l’erreur.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Si vous souhaitez empêcher l’affichage de la boîte de dialogue

Vous pouvez prendre des mesures pour empêcher juste-à-temps débogueur de boîte de dialogue d’apparaître. Si l’application gère l’erreur, vous pouvez exécuter l’application normalement.

1. (Applications web) Si vous essayez d’exécuter une application web, vous pouvez désactiver le débogage de script.

    Pour Internet Explorer ou Edge, désactivez le débogage de script dans la boîte de dialogue Options Internet. Vous pouvez accéder à ces paramètres à partir de la **le panneau de configuration** > **réseau et Internet** > **Options Internet** (la procédure exacte varie selon votre version de Windows et de votre navigateur).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Rouvrez la page web où vous avez trouvé l’erreur. Si la modification de ce paramètre ne résout pas le problème, contactez le propriétaire de l’application web pour résoudre le problème.

3. (Utilisateurs de visual Studio) Si vous avez installé Visual Studio (ou si vous aviez installé précédemment elle supprimé), [juste-à-temps de désactiver le débogage](../debugger/debug-using-the-just-in-time-debugger.md) et essayez de réexécuter l’application.

    > [!IMPORTANT]
    > Si vous désactivez juste-à-temps de débogage et de l’application rencontre une exception non gérée (erreur), vous soit verrez une boîte de dialogue d’erreur standard à la place, ou l’application se bloque ou de blocage. L’application ne s’exécutera pas normalement jusqu'à ce que l’erreur est fixe (par vous ou le propriétaire de l’application).

2. (IIS et ASP.NET) Si vous hébergez une application Web ASP.NET dans IIS, désactivez le débogage côté serveur.

    Dans le Gestionnaire des services Internet, cliquez sur le nœud du serveur et choisissez **basculer vers l’affichage des fonctionnalités**. Dans la section ASP.NET, choisissez **Compilation .NET** et vérifiez que vous choisissez **False** en tant que le comportement de débogage (les étapes sont différentes dans les versions antérieures d’IIS).
  
## <a name="see-also"></a>Voir aussi    
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
