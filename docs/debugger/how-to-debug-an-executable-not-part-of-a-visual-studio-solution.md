---
title: Déboguer une application qui ne fait pas partie d’une solution Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
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
ms.openlocfilehash: 49636dc4a43d56afe6d9307fc7ec2ddd44a6c37f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690199"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Déboguer une application qui ne fait pas partie d’une solution Visual Studio (C++, C#, Visual Basic, F#)

Vous pouvez souhaiter de déboguer une application (*.exe* fichier) qui ne fait pas partie d’une solution Visual Studio. Vous ou quelqu'un d’autre a peut-être créé l’application en dehors de Visual Studio, ou vous avez obtenu à l’application à partir d’un autre emplacement.

L’approche habituelle pour déboguer une application qui n’existe pas dans Visual Studio consiste à démarrer l’application en dehors de Visual Studio et puis attachez à l’aide de **attacher au processus** dans le débogueur Visual Studio. Pour plus d’informations, consultez [attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Attachement à une application requiert des étapes manuelles que prennent quelques secondes. En raison de ce délai, attachement ne vous aider à déboguer un problème de démarrage, ou une application qui n’attend pas de l’utilisateur d’entrée et se termine rapidement.

Dans ces situations, vous pouvez créer un projet Visual Studio EXE pour l’application, ou l’importer dans une existante C#, Visual Basic ou C++ solution. Tous les langages de programmation ne prennent pas en charge les projets EXE.

>[!IMPORTANT]
>Fonctionnalités de débogage pour une application qui n’a pas été intégré dans Visual Studio sont limitées, si vous attachez à l’application ou l’ajoutez à une solution Visual Studio.
>
>Si vous avez le code source, la meilleure approche consiste à importer le code dans un projet Visual Studio. Ensuite, exécutez une version debug de l’application.
>
>Si vous n’avez pas le code source, et que l’application n’a pas [les informations de débogage](../debugger/how-to-set-debug-and-release-configurations.md) dans un format compatible, les fonctionnalités de débogage disponibles sont très peu.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Pour créer un projet EXE pour une application existante

1. Dans Visual Studio, sélectionnez **fichier** > **Open** > **projet**.

1. Dans le **ouvrir un projet** boîte de dialogue, sélectionnez **tous les fichiers projet**, le cas échéant, dans la liste déroulante à côté **nom de fichier**.

1. Accédez à la *.exe* , sélectionnez-le et sélectionnez **Open**.

   Le fichier apparaît dans une nouvelle solution Visual Studio temporaire.

1. Démarrer le débogage de l’application en sélectionnant une commande d’exécution, comme **démarrer le débogage**, à partir de la **déboguer** menu.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Pour importer une application dans une solution Visual Studio existante

1.  Avec C++, C#, ou Visual Basic solution ouverte dans Visual Studio, sélectionnez **fichier** > **ajouter** > **projet existant**.

1. Dans le **ouvrir un projet** boîte de dialogue, sélectionnez **tous les fichiers projet**, le cas échéant, dans la liste déroulante à côté **nom de fichier**.

1. Accédez à la *.exe* , sélectionnez-le et sélectionnez **Open**.

   Le fichier apparaît en tant que nouveau projet sous la solution actuelle.

1. Avec le nouveau fichier sélectionné, démarrer le débogage de l’application en sélectionnant une commande d’exécution, comme **démarrer le débogage**, à partir de la **déboguer** menu.

### <a name="see-also"></a>Voir aussi
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Fichiers DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))