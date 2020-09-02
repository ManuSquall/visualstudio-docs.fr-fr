---
title: Choix d’une stratégie d’implémentation du moteur de débogage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739128"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Choisir une stratégie d’implémentation du moteur de débogage
Utilisez l’architecture Runtime pour déterminer la stratégie d’implémentation de votre moteur DE débogage (DE). Vous pouvez créer le moteur de débogage in-process pour le programme que vous déboguez. Créez le moteur de débogage in-process dans le gestionnaire de débogage de la session Visual Studio (SDM). Vous pouvez aussi créer le moteur de débogage hors processus pour les deux. Les instructions suivantes doivent vous aider à choisir parmi ces trois stratégies.

## <a name="guidelines"></a>Consignes
 Bien qu’il soit possible que le soit hors processus à la fois vers le SDM et le programme que vous déboguez, il n’y a généralement aucune raison de le faire. Les appels entre les limites du processus sont relativement lents.

 Les moteurs de débogage sont déjà fournis pour l’environnement Runtime natif Win32 et pour l’environnement Common Language Runtime. Si vous devez remplacer l’un de ces deux environnements, vous devez créer le de in-process avec le SDM.

 Dans le cas contraire, vous créez le de in-process dans le SDM ou in-process pour le programme que vous déboguez. Vous devez tenir compte du fait que l’évaluateur d’expression de l’argument DE l’DE requiert un accès fréquent au magasin de symboles de programme. Ou, si le magasin de symboles peut être chargé en mémoire pour un accès rapide. Tenez également compte des approches suivantes :

- S’il n’y a pas beaucoup d’appels entre l’évaluateur d’expression et le magasin de symboles, ou si le magasin de symboles peut être lu dans l’espace mémoire SDM, créez le de in-process dans le SDM. Vous devez retourner le CLSID du moteur de débogage au SDM lorsqu’il est attaché à votre programme. Le SDM utilise ce CLSID pour créer une instance in-process du de.

- Si le DE doit appeler le programme pour accéder au magasin de symboles, créez le de in-process avec le programme. Dans ce cas, le programme crée l’instance de l’instance de.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
