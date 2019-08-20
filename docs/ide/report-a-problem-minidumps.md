---
title: Créer des minidumps avec toutes les piles des appels
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7d0580e04968a01dc8e447a9ee35f2b1c5934ccf
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461657"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Créer des minidumps pour un processus Visual Studio avec toutes les piles des appels

Dans certains cas, Microsoft peut demander un minidump d’un processus Visual Studio en cours d’exécution avec des informations pour toutes les piles des appels. Pour collecter ces informations, procédez comme suit :

## <a name="create-the-minidump-file"></a>Créer le fichier de minividage

1. Ouvrez une nouvelle instance de Visual Studio.
1. Dans le menu principal, choisissez **Déboguer** > **Joindre au processus**.
1. Cochez les cases correspondantes **Managé** et **Natif** et appuyez sur **Joindre**.

   ![Attacher au processus](../ide/media/attach-to-process.png)

1. Sélectionnez l’autre instance de Visual Studio à joindre dans la liste des processus en cours.
1. Dans le menu principal, choisissez **Déboguer** > **Interrompre tout**.
1. Dans le menu principal, choisissez **Déboguer** > **Enregistrer l’image mémoire sous**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Obtenir les piles des appels du minidump

1. Ouvrez le fichier de vidage dans Visual Studio.
1. Allez à **Outils** > **Options** > **Débogage** > **Symboles** et assurez-vous que **Serveurs de symboles Microsoft** est enregistré dans les **emplacements du fichier de symboles (.pdb)** .
1. Ouvrir la fenêtre **Commande** (**Afficher** > **Autre fenêtres** > **fenêtre Commande**)
1. Saisissez ‘~*k’. La fenêtre affiche toutes les piles des appels des conversations.
1. Copiez tout le texte de la fenêtre Commande et enregistrez le dans un fichier texte.
1. Joignez le fichier txt au bogue.
