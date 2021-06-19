---
title: Préparer le débogage des projets de console | Microsoft Docs
description: 'Obtenir des informations sur la préparation du débogage des projets de console (C#, C++, Visual Basic, F #) dans Visual Studio.'
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d1610919667fdaf1a752ca56aef5358c0bd34f3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387812"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Préparation du débogage : projets console (C#, C++, Visual Basic, F #)

La préparation du débogage d’un projet de console est semblable à la préparation du débogage d’un projet Windows, avec des considérations supplémentaires telles que la définition des arguments de ligne de commande et la façon de suspendre l’application pour le débogage. Pour plus d’informations, consultez [préparation du débogage pour les applications Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md). En raison de la similarité de toutes les applications console, cette rubrique couvre les types de projets suivants :

- Application console C#, Visual Basic et F #

- Application console C++ (.NET)

- Application console C++ (Win32)

  Une application console utilise la fenêtre **Console** pour accepter les entrées et afficher les messages de sortie. Pour écrire dans la fenêtre de **console** , votre application doit utiliser l’objet **console** au lieu de l’objet Debug. Pour écrire dans la fenêtre **Sortie Visual Studio**, utilisez l’objet Debug, comme d’habitude. Vérifiez l'emplacement dans lequel écrit votre application, sinon vous risquez de rechercher les messages au mauvais endroit. Pour plus d’informations, consultez [Console, classe](/dotnet/api/system.console), [Debug, classe](/dotnet/api/system.diagnostics.debug) et [Sortie, fenêtre](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Définir les arguments de ligne de commande

Vous pouvez être amené à spécifier des arguments de ligne de commande pour votre application console. Pour plus d’informations, consultez [paramètres de projet pour une configuration de débogage C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)ou [paramètres de projet pour les configurations de débogage C#](../debugger/project-settings-for-csharp-debug-configurations.md).

Comme toutes les propriétés de projet, ces arguments persistent entre les sessions de débogage et celles de Visual Studio. Par conséquent, si vous avez débogué précédemment l’application console, n’oubliez pas qu’il existe peut-être des arguments provenant des sessions précédentes dans la boîte de dialogue **\<Project> pages de propriétés** .

## <a name="start-the-application"></a>Lancer l’application

 Lorsque certaines applications console démarrent, elles s'exécutent jusqu'à la fin, puis se ferment. Ce comportement peut ne pas vous fournir suffisamment de temps pour interrompre l'exécution et le débogage. Pour pouvoir déboguer une application, utilisez l'une des procédures suivantes pour démarrer l'application :

- Définissez un point d’arrêt dans votre code et démarrez votre application.

- Démarrez votre application en utilisant **F10** (**Déboguer**  >  **pas à pas principal**) ou **F11** (pas à  >  **pas détaillé dans**), puis parcourez le code à l’aide d’autres options, telles que **Exécuter jusqu’au clic**.

- Dans l’éditeur de code, cliquez avec le bouton droit sur une ligne et sélectionnez **Exécuter jusqu’au curseur**.

  Lors du débogage d'une application console, vous pouvez démarrer l'application à partir de l'invite de commandes au lieu de la démarrer à partir de Visual Studio. Dans ce cas, vous pouvez démarrer l'application à partir de l'invite de commandes, puis l'attacher au débogueur Visual Studio. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Quand vous démarrez une application console à partir de Visual Studio, la fenêtre **Console** apparaît parfois derrière la fenêtre Visual Studio. Si vous essayez de démarrer votre application console à partir de Visual Studio et que rien ne se produit, essayez de déplacer la fenêtre Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Débogage du code natif](../debugger/debugging-native-code.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Préparer le débogage de projets C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)