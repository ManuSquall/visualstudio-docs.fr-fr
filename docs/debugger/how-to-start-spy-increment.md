---
title: 'Procédure : Démarrer Spy + + | Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542618"
---
# <a name="how-to-start-spy"></a>Comment : démarrer Spy++

Vous pouvez démarrer Spy + + à partir de Visual Studio ou à partir d’une invite de commandes.

 Quand vous démarrez Spy + +, si un message s’affiche pour demander l’autorisation d’apporter des modifications à l’ordinateur, sélectionnez **Oui**.

> [!NOTE]
> Vous ne pouvez exécuter qu’une seule instance de Spy + +. Si vous essayez de démarrer une deuxième instance, l’instance en cours d’exécution est simplement en train d’obtenir le focus.

## <a name="prerequisites"></a>Prerequisites

Spy + + requiert les composants suivants. Vous pouvez sélectionner ces composants à partir de la Visual Studio Installer en sélectionnant l’onglet **composants individuels** , puis en sélectionnant les composants suivants.

* Sous débogage et test, sélectionnez  **C++ outils de profilage.**
* Sous activités de développement, sélectionnez  **C++ fonctionnalités principales.**

Si vous avez apporté des modifications, suivez les invites pour installer ces composants.

## <a name="start-spy-from-visual-studio"></a>Démarrer Spy + + à partir de Visual Studio

Dans le menu **Outils** , sélectionnez **Spy + +** .

Étant donné que Spy + + s’exécute indépendamment, après son démarrage, vous pouvez fermer Visual Studio.

> [!NOTE]
> Lorsque vous consignez des messages avec Spy + +, le système d’exploitation peut s’exécuter plus lentement.

## <a name="start-spy-at-a-command-prompt"></a>Démarrer Spy + + à partir d’une invite de commandes

1. Dans une fenêtre d’invite de commandes, accédez au dossier qui contient spyxx. exe. En général, le chemin d’accès à ce dossier est..\\*dossier d’installation de Visual Studio*\Common7\Tools\\.

2. Entrez **spyxx. exe**.

## <a name="see-also"></a>Voir aussi
- [Utilisation de Spy++](../debugger/using-spy-increment.md)
- [Vues Spy++](../debugger/spy-increment-views.md)
- [Informations de référence sur Spy++](../debugger/spy-increment-reference.md)
