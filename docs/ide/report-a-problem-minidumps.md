---
title: Créer des minidumps avec toutes les piles des appels
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7b3be91e5d0d2e1f14724dd647670fc4885bcd4d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271190"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Créer des minidumps pour un processus Visual Studio avec toutes les piles des appels

Dans certains cas, Microsoft peut demander un minidump d’un processus Visual Studio en cours d’exécution avec des informations pour toutes les piles des appels. Pour collecter ces informations, procédez comme suit :

## <a name="create-the-minidump-file"></a>Créer le fichier de minividage

1. Ouvrez une nouvelle instance de Visual Studio.
1. Parmi le menu principal, choisissez **Debug** > **Attach To Process**.
1. Cochez les cases correspondantes **Managé** et **Natif** et appuyez sur **Joindre**.

   ![Attacher au processus](../ide/media/attach-to-process.png)

1. Sélectionnez l’autre instance de Visual Studio à joindre dans la liste des processus en cours.
1. Parmi le menu principal, choisissez **Debug** > **Break All**.
1. Parmi le menu principal, choisissez **Debug** > **Save Dump As**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Obtenir les piles des appels du minidump

1. Ouvrez le fichier de vidage dans Visual Studio.
1. Rendez-vous sur **Tools** > **Options** > **Debugging** > **Symbols** et assurez-vous que microsoft Symbol Servers est vérifié dans les **emplacements** du **fichier Symbol (.pdb).**
1. Ouvrir la fenêtre **Commande** (**Afficher** > **Autre fenêtres** > **fenêtre Commande**)
1. Saisissez ‘~*k’. La fenêtre affiche toutes les piles des appels des conversations.
1. Copiez tout le texte de la fenêtre Commande et enregistrez le dans un fichier texte.
1. Joignez le fichier txt au bogue.
