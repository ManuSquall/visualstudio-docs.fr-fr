---
title: Choisir une stratégie de mise en œuvre d’un moteur Debug (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739128"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Choisissez une stratégie de mise en œuvre d’un moteur de débogé
Utilisez l’architecture de temps d’exécution pour déterminer votre stratégie de mise en œuvre du moteur de déboguer (DE). Vous pouvez créer le moteur de déboguer en cours de traitement au programme que vous débogage. Créez le moteur débogé en cours de traitement au responsable de la dbug de session Visual Studio (SDM). Ou, créer le moteur de débogé hors-processus pour les deux. Les lignes directrices suivantes devraient vous aider à choisir parmi ces trois stratégies.

## <a name="guidelines"></a>Consignes
 Bien qu’il soit possible pour le DE d’être hors-processus à la fois pour le SDM et le programme que vous débugging, il n’y a généralement aucune raison de le faire. Les appels au-delà des limites des processus sont relativement lents.

 Les moteurs Debug sont déjà fournis pour l’environnement de temps d’exécution natif Win32 et pour l’environnement de course de langue commune. Si vous devez remplacer le DE pour l’un ou l’autre environnement, vous devez créer le PROCESSUS DE avec le SDM.

 Sinon, vous créez soit le DE en cours de traitement au SDM ou en cours de processus pour le programme que vous débogage. Vous devrez considérer si l’évaluateur d’expression de l’EN nécessite un accès fréquent au magasin de symboles du programme. Ou, si le magasin de symboles peut être chargé dans la mémoire pour un accès rapide. En outre, considérez les approches suivantes :

- S’il n’y a pas beaucoup d’appels entre l’évaluateur d’expression et le magasin de symboles, ou si le magasin de symboles peut être lu dans l’espace de mémoire SDM, créez le DE en cours de traitement au SDM. Vous devez retourner le CLSID du moteur de débogé au SDM lorsqu’il se fixe à votre programme. Le SDM utilise ce CLSID pour créer une instance en cours de DE.

- Si le DE doit appeler le programme pour accéder au magasin de symboles, créez le PROCESSUS DE avec le programme. Dans ce cas, le programme crée le cas de la DE.

## <a name="see-also"></a>Voir aussi
- [Visual Studio débbugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
