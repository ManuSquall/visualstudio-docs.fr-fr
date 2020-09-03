---
title: Programmation avec Visual Studio Tools pour Unity et Azure | Microsoft Docs
ms.custom: ''
ms.date: 12/18/2017
ms.reviewer: crdun
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: e9a07a7f04cae433803d012302555821fc851075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916827"
---
# <a name="program-with-unity-and-azure"></a>Programmer avec Unity et Azure

Azure fournit une solution scalable pour le stockage des données de télémétrie et d’autres données de jeu dans le cloud. Avec la version Unity 2017, la prise en charge expérimentale de .NET 4.6 par Unity rend l’intégration d’Azure plus simple que jamais en permettant l’utilisation des kits SDK Azure .NET.

## <a name="experimental-azure-sdks"></a>Kits SDK Azure expérimentaux

> [!NOTE]
> Ces kits SDK ne sont pas pris en charge, mais fournis pour aider les clients à tester la prise en charge expérimentale .NET 4.6 d’Unity.

Consultez le bac à sable [Sandbox](/sandbox/) pour tester les kits SDK Azure expérimentaux suivants avec Unity :

* [Kit SDK Azure Storage pour Unity](/sandbox/gamedev/unity/azure-storage-unity?wt.mc_id=azgamedev-sandbox-brpeek)
* [Kit SDK Azure Event Hubs pour Unity](/sandbox/gamedev/unity/azure-event-hubs-unity?WT.mc_id=azgamedev-sandbox-brpeek)
* [Kit SDK Azure Mobile Apps pour Unity](/sandbox/gamedev/unity/azure-mobile-apps-unity?WT.mc_id=azgamedev-sandbox-brpeek)

## <a name="azure-sdk-sample"></a>Exemple de SDK Azure

Vous disposez également d’un [exemple de jeu simple](/sandbox/gamedev/unity/samples/azure-mobile-apps-unity-racer) en utilisant le Kit SDK Easy Tables et Unity. Le jeu utilise le stockage de données Azure Easy Tables pour effectuer le suivi des meilleurs scores et stocker les données de télémétrie du jeu. Il peut être [téléchargé à partir de GitHub](https://github.com/BrianPeek/AzureSamples-Unity).

![Capture d’écran d’un exemple de jeu](media/vstu_azure-test-sample-game-image2.png)
