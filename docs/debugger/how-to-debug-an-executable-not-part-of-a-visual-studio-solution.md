---
title: Déboguer une application qui ne fait pas partie d’une solution Visual Studio
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8cb71acb9c1c332f269f77129fa2d11a9a874f8
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350145"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Déboguer une application qui ne fait pas partie d’une solution Visual Studio (C++, C#, Visual Basic, F #)

Vous pouvez déboguer une application (fichier *. exe* ) qui ne fait pas partie d’une solution Visual Studio. Il peut s’agir d’un projet de [dossier ouvert](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) , ou vous-même ou quelqu’un d’autre avez créé l’application en dehors de Visual Studio, ou vous avez obtenu l’application à partir d’un autre emplacement.

- Pour un projet de dossier ouvert dans Visual Studio (qui n’a aucun fichier projet ou solution), consultez [exécuter et déboguer votre code](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) ou, pour C++, [configurer les paramètres de débogage avec launch.vs.jssur](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Pour une application qui n’existe pas dans Visual Studio, la méthode habituelle de débogage consiste à démarrer l’application en dehors de Visual Studio, puis à l’attacher à l’aide de l' **attachement au processus** dans le débogueur Visual Studio. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   L’attachement à une application nécessite des étapes manuelles qui prennent quelques secondes. En raison de ce délai, l’attachement ne permet pas de déboguer un problème de démarrage ou une application qui n’attend pas l’entrée de l’utilisateur et se termine rapidement.

   Dans ces situations, vous pouvez créer un projet Visual Studio EXE pour l’application, ou l’importer dans une solution C#, Visual Basic ou C++ existante. Tous les langages de programmation ne prennent pas en charge les projets EXE.

>[!IMPORTANT]
>Les fonctionnalités de débogage pour une application qui n’a pas été générée dans Visual Studio sont limitées, que vous attachiez l’application ou l’ajoutiez à une solution Visual Studio.
>
>Si vous disposez du code source, la meilleure approche consiste à importer le code dans un projet Visual Studio. Ensuite, exécutez une version Debug de l’application.
>
>Si vous n’avez pas le code source et que l’application n’a pas d' [informations de débogage](../debugger/how-to-set-debug-and-release-configurations.md) dans un format compatible, les fonctionnalités de débogage disponibles sont très rares.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Pour créer un projet EXE pour une application existante

1. Dans Visual Studio, sélectionnez **fichier**  >  **ouvrir**le  >  **projet**.

1. Dans la boîte de dialogue **ouvrir un projet** , sélectionnez **tous les fichiers projet**, s’ils ne sont pas déjà sélectionnés, dans la liste déroulante en regard de **nom de fichier**.

1. Accédez au fichier *. exe* , sélectionnez-le, puis sélectionnez **ouvrir**.

   Le fichier apparaît dans une nouvelle solution Visual Studio temporaire.

1. Démarrez le débogage de l’application en sélectionnant une commande d’exécution, par exemple **Démarrer le débogage**, dans le menu **Déboguer** .

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Pour importer une application dans une solution Visual Studio existante

1. Avec une solution C++, C# ou Visual Basic ouverte dans Visual Studio, sélectionnez **fichier**  >  **Ajouter**un  >  **projet existant**.

1. Dans la boîte de dialogue **ouvrir un projet** , sélectionnez **tous les fichiers projet**, s’ils ne sont pas déjà sélectionnés, dans la liste déroulante en regard de **nom de fichier**.

1. Accédez au fichier *. exe* , sélectionnez-le, puis sélectionnez **ouvrir**.

   Le fichier apparaît sous la forme d’un nouveau projet sous la solution actuelle.

1. Une fois le nouveau fichier sélectionné, démarrez le débogage de l’application en sélectionnant une commande d’exécution, par exemple **Démarrer le débogage**, dans le menu **Déboguer** .

### <a name="see-also"></a>Voir aussi
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Fichiers DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))