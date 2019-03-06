---
title: Préparer le débogage des projets console | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f94dcc62b829078fb8efc43ef92ddb203e1a1e32
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709237"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Préparation du débogage : Projets Console (C#, C++, Visual Basic, F#)

La préparation du débogage d'un projet console est identique à celle d'un projet Windows, avec quelques éléments supplémentaires à prendre en compte. Pour plus d’informations, consultez [les Applications Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), et [préparation du débogage : applications Windows Forms (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)) En raison de la similarité de toutes les applications console, cette rubrique couvre les types de projets suivants :

- C#, Visual Basic, et F# Application Console

- Application console C++ (.NET)

- Application console C++ (Win32)

  Vous pouvez être amené à spécifier des arguments de ligne de commande pour votre application console. Pour plus d’informations, consultez [paramètres de projet pour une Configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [paramètres de projet pour une Configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), ou [paramètres de projet pour C# déboguer Configurations](../debugger/project-settings-for-csharp-debug-configurations.md).

  Comme toutes les propriétés de projet, ces arguments persistent entre les sessions de débogage et celles de Visual Studio. Par conséquent, si vous avez débogué précédemment l’application console, n’oubliez pas qu’il existe peut-être des arguments provenant des sessions précédentes dans la boîte de dialogue **Pages de propriétés de \<Projet>**.

  Une application console utilise la fenêtre **Console** pour accepter les entrées et afficher les messages de sortie. Pour écrire dans le **Console** fenêtre, votre application doit utiliser le **Console** objet au lieu de l’objet Debug. Pour écrire dans la fenêtre **Sortie Visual Studio**, utilisez l’objet Debug, comme d’habitude. Vérifiez l'emplacement dans lequel écrit votre application, sinon vous risquez de rechercher les messages au mauvais endroit. Pour plus d’informations, consultez [Console, classe](/dotnet/api/system.console), [Debug, classe](/dotnet/api/system.diagnostics.debug) et [Sortie, fenêtre](../ide/reference/output-window.md).

## <a name="starting-the-application"></a>Démarrage de l'application
 Lorsque certaines applications console démarrent, elles s'exécutent jusqu'à la fin, puis se ferment. Ce comportement peut ne pas vous fournir suffisamment de temps pour interrompre l'exécution et le débogage. Pour pouvoir déboguer une application, utilisez l'une des procédures suivantes pour démarrer l'application :

- Définissez un point d’arrêt dans votre code et démarrer votre application.

- Démarrez votre application à l’aide **F10** (**déboguer** > **pas à pas principal**) ou **F11** (**déboguer**  >  **Pas à pas détaillé**), puis accédez via le code à l’aide d’autres options telles que **exécuter jusqu’au clic**.

- Dans l’éditeur de code, cliquez sur une ligne, puis sélectionnez **exécuter jusqu’au curseur**.

  Lors du débogage d'une application console, vous pouvez démarrer l'application à partir de l'invite de commandes au lieu de la démarrer à partir de Visual Studio. Dans ce cas, vous pouvez démarrer l'application à partir de l'invite de commandes, puis l'attacher au débogueur Visual Studio. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Quand vous démarrez une application console à partir de Visual Studio, la fenêtre **Console** apparaît parfois derrière la fenêtre Visual Studio. Si vous essayez de démarrer votre application console à partir de Visual Studio et que rien ne se produit, essayez de déplacer la fenêtre Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Débogage du code natif](../debugger/debugging-native-code.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Types de projets Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)