---
title: Créer des minidumps avec toutes les piles des appels
description: Découvrez comment créer des minidumps pour un processus Visual Studio qui comprend des informations pour toutes les piles d’appels.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 44ab0873580c7c541fc5e7fdde56cc1780929b75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970775"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Créer des minidumps pour un processus Visual Studio avec toutes les piles des appels

Dans certains cas, Microsoft peut demander un minidump d’un processus Visual Studio en cours d’exécution avec des informations pour toutes les piles des appels. Pour collecter ces informations, procédez comme suit :

## <a name="create-the-minidump-file"></a>Créer le fichier de minividage

1. Ouvrez une nouvelle instance de Visual Studio.
1. Dans le menu principal, choisissez **Déboguer**  >  **attacher au processus**.
1. Cochez les cases correspondantes **Managé** et **Natif** et appuyez sur **Joindre**.

   ![Attacher au processus](../ide/media/attach-to-process.png)

1. Sélectionnez l’autre instance de Visual Studio à joindre dans la liste des processus en cours.
1. Dans le menu principal, choisissez **Déboguer**  >  **arrêter tout**.
1. Dans le menu principal, choisissez **Déboguer**  >  **enregistrer le vidage sous**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Obtenir les piles des appels du minidump

1. Ouvrez le fichier de vidage dans Visual Studio.
1. Accédez à **Outils**  >  **options** de  >  **débogage**  >  **symboles** et assurez-vous que les **serveurs de symboles Microsoft** sont vérifiés dans les **emplacements du fichier de symboles (. pdb)**.
1. Ouvrir la fenêtre **Commande** (**Afficher** > **Autre fenêtres** > **fenêtre Commande**)
1. Saisissez ‘~*k’. La fenêtre affiche toutes les piles des appels des conversations.
1. Copiez tout le texte de la fenêtre Commande et enregistrez le dans un fichier texte.
1. Joignez le fichier txt au bogue.
