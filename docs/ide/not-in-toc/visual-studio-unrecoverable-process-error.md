---
title: "Erreur de processus irrécupérable Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/23/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords: editor
ms.assetid: 2263956f-3ae0-4bdc-9d3a-4991dfaf4ddb
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 8750d16a485de062e66041e66e28fa591e957efd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# Erreur de processus irrécupérable Visual Studio

Visual Studio 2017 utilise plusieurs processus hors processus pour exécuter des tâches d’arrière-plan obligatoires, telles que des tests unitaires en direct, des analyseurs de code, et bien plus encore. Grâce à l’exécution hors processus de ces processus, les performances de Visual Studio sont améliorées ; par exemple, Visual Studio répond plus rapidement pendant l’exécution de tâches gourmandes en ressources et de longue durée. En outre, Visual Studio étant un processus 32 bits, l’exécution de processus hors processus met un espace de mémoire plus grand à la disposition des travaux gourmands en mémoire.

Si un de ces processus nécessaires prend fin pour une raison quelconque, une barre d’information contextuelle s’affiche avec le message suivant :

« Malheureusement, un processus utilisé par Visual Studio a rencontré une erreur irrécupérable. Nous vous recommandons d’enregistrer votre travail, puis de fermer et redémarrer Visual Studio. »

Si vous voyez ce message, vous devez immédiatement enregistrer votre travail, puis fermer et redémarrer Visual Studio. Si vous ne faites pas cela, Visual Studio peut se bloquer à tout moment.

## Liste de processus

Voici une de liste de processus hors processus utilisés par Visual Studio et dont l’exécution est nécessaire à son bon fonctionnement.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe
