---
title: Un processus a rencontré une erreur irrécupérable
description: En savoir plus sur les processus susceptibles de rencontrer des erreurs irrécupérables pendant les opérations normales de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/10/2020
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2ff53ecf1e3f3b377180fe85f972dca665b81f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909152"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Erreur de processus irrécupérable Visual Studio

Visual Studio utilise plusieurs processus hors processus pour exécuter des tâches d’arrière-plan obligatoires, telles que des tests unitaires en direct, des analyseurs de code, et bien plus encore. Grâce à l’exécution hors processus de ces processus, les performances de Visual Studio sont améliorées ; par exemple, Visual Studio répond plus rapidement pendant l’exécution de tâches gourmandes en ressources et de longue durée. En outre, Visual Studio étant un processus 32 bits, l’exécution de processus hors processus met un espace de mémoire plus grand à la disposition des travaux gourmands en mémoire.

Si le processus *ServiceHub.RoslynCodeAnalysisService.exe* ou *ServiceHub.RoslynCodeAnalysisService32.exe* se termine pour une raison quelconque, une barre d’information contextuelle s’affiche avec le message suivant :

**«Malheureusement, un processus utilisé par Visual Studio a rencontré une erreur irrécupérable. Nous vous recommandons d’enregistrer votre travail, puis de fermer et redémarrer Visual Studio.»**

Si vous voyez ce message, vous devez enregistrer votre travail, puis fermer et redémarrer Visual Studio.

## <a name="list-of-processes"></a>Liste de processus

Voici une liste des processus hors processus utilisés par Visual Studio. Cette liste comprend les processus qui démarrent dans des scénarios ou des flux de travail spécifiques. Par conséquent, dans la plupart des cas ils ne s’exécutent pas tous en même temps.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- MSBuild.exe
- PerfWatson2.exe
- ScriptedSandbox64.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.VSDetouredHost.exe
- VBCSCompiler.exe
- VsHub.exe
- vstest.discoveryengine.x86.exe
- WaAppAgent.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe

Si l’un de ces processus s’arrête de façon inattendue, certaines fonctionnalités dans Visual Studio cessent de fonctionner. Pour certains processus, la perte de fonctionnalité peut être négligeable. Pour d’autres, la stabilité de Visual Studio est affectée et un message d’erreur s’affiche.

> [!NOTE]
> Si vous rencontrez un problème qui n’est pas référencé sur cette page, veuillez nous le signaler via l’outil [signaler un problème](../../ide/how-to-report-a-problem-with-visual-studio.md) qui s’affiche à la fois dans le Visual Studio installer et dans l’IDE de Visual Studio.
