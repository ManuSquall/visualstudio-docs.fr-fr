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
ms.openlocfilehash: eefcbefa8b728afa677e7bd04fd538633ae117f0
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518175"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Créer des minidumps pour un processus Visual Studio avec toutes les piles des appels

Dans certains cas, Microsoft peut demander un minidump d’un processus en cours d’exécution de Visual Studio avec des informations pour toutes les piles des appels. Pour collecter ces informations, procédez comme suit :

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
