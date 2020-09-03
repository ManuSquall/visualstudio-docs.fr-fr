---
title: Un processus a rencontré une erreur irrécupérable
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c30ac5950ca9bf775b05e9f77867c119b7c7565d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81544339"
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
