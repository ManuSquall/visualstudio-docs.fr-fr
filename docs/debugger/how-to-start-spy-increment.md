---
title: Démarrer Spy + + | Microsoft Docs
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7743d36671e1c651b9bcfa89b315399c0696e26d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851903"
---
# <a name="how-to-start-spy"></a>Comment : démarrer Spy++

Vous pouvez démarrer Spy + + à partir de Visual Studio ou à partir d’une invite de commandes.

 Quand vous démarrez Spy + +, si un message s’affiche pour demander l’autorisation d’apporter des modifications à l’ordinateur, sélectionnez **Oui**.

> [!NOTE]
> Vous ne pouvez exécuter qu’une seule instance de Spy + +. Si vous essayez de démarrer une deuxième instance, l’instance en cours d’exécution est simplement en train d’obtenir le focus.

## <a name="prerequisites"></a>Prérequis

Spy + + requiert les composants suivants. Vous pouvez sélectionner ces composants à partir de la Visual Studio Installer en sélectionnant l’onglet **composants individuels** , puis en sélectionnant les composants suivants.

* Sous débogage et test, sélectionnez **outils de profilage C++** .
* Sous activités de développement, sélectionnez **fonctionnalités principales C++** .

Si vous avez apporté des modifications, suivez les invites pour installer ces composants.

## <a name="start-spy-from-visual-studio"></a>Démarrer Spy + + à partir de Visual Studio

Dans le menu **Outils** , sélectionnez **Spy + +**.

Étant donné que Spy + + s’exécute indépendamment, après son démarrage, vous pouvez fermer Visual Studio.

> [!NOTE]
> Lorsque vous consignez des messages avec Spy + +, le système d’exploitation peut s’exécuter plus lentement.

## <a name="start-spy-at-a-command-prompt"></a>Démarrer Spy + + à partir d’une invite de commandes

1. Dans une fenêtre d’invite de commandes, remplacez les répertoires par le dossier qui contient spyxx.exe. En général, le chemin d’accès à ce dossier est.. \\ *Dossier d’installation de Visual Studio*\Common7\Tools \\ .

2. Entrez **spyxx.exe**.

## <a name="see-also"></a>Voir aussi
- [Utiliser Spy++](../debugger/using-spy-increment.md)
- [Vues Spy++](../debugger/spy-increment-views.md)
- [Référence Spy++](../debugger/spy-increment-reference.md)
