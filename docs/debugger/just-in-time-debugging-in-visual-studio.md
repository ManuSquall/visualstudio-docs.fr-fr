---
title: 'Comment : répondre au débogueur juste-à-temps | Microsoft Docs'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cec8887ddf2023a8abd08f409b93f47efdc7001
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155566"
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Comment : répondre au débogueur juste-à-temps

Les actions que vous devez prendre lorsque vous voyez juste-à-temps boîte de dialogue de débogueur dépendent de ce que vous essayez de faire :

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Si vous souhaitez corriger ou de déboguer l’erreur (utilisateurs de Visual Studio)

- Vous devez avoir [Visual Studio installé](http://visualstudio.microsoft.com) pour afficher les informations détaillées sur l’erreur et essayez de déboguer. Pour plus d’informations, consultez [déboguer à l’aide du débogueur juste à temps](../debugger/debug-using-the-just-in-time-debugger.md). Si vous ne pouvez pas résoudre l’erreur et corriger l’application, contactez le propriétaire de l’application pour résoudre l’erreur.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Si vous souhaitez empêcher l’affichage de la boîte de dialogue

Vous pouvez prendre des mesures pour empêcher le juste-à-temps débogueur de boîte de dialogue d’apparaître. Si l’application gère l’erreur, vous pouvez exécuter l’application normalement.

1. (Applications web) Si vous essayez d’exécuter une application web, vous pouvez désactiver le débogage de script.

    Pour Internet Explorer ou Edge, désactiver le débogage de script dans la boîte de dialogue Options Internet. Vous pouvez accéder à ces paramètres à partir de la **le panneau de configuration** > **réseau et Internet** > **Options Internet** (la procédure exacte varie selon votre version de Windows et de votre navigateur).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Puis rouvrez la page web où vous avez trouvé l’erreur. Si la modification de ce paramètre ne résout pas le problème, contactez le propriétaire de l’application web pour résoudre le problème.

3. (Utilisateurs de visual Studio) Si vous avez installé Visual Studio (ou si vous aviez il déjà installé et supprimé), [juste-à-temps de désactiver le débogage](../debugger/debug-using-the-just-in-time-debugger.md) et essayez à nouveau exécuter l’application.

    > [!IMPORTANT]
    > Si vous désactivez juste-à-temps de débogage et de l’application rencontre une exception non gérée (erreur), vous soit verrez une boîte de dialogue d’erreur standard à la place, ou l’application se bloque ou se bloquer. L’application ne sera pas exécutée normalement jusqu'à ce que l’erreur est corrigée (par vous ou le propriétaire de l’application).

2. (ASP.NET et IIS) Si vous hébergez une application Web ASP.NET dans IIS, désactivez le débogage côté serveur.

    Dans le Gestionnaire des services Internet, cliquez sur le nœud de serveur et choisissez **basculer vers l’affichage des fonctionnalités**. Dans la section ASP.NET, choisissez **Compilation .NET** et vérifiez que vous choisissez **False** en tant que le comportement de débogage (les étapes sont différentes dans les versions antérieures d’IIS).

## <a name="see-also"></a>Voir aussi
 [Principes de base du débogueur](../debugger/debugger-basics.md)
