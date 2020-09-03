---
title: Options (boîte de dialogue), Projets et solutions, Générer et exécuter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b7eb229c5938165607b797205b94a318e3303b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655189"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Options (boîte de dialogue), Projets et solutions, Générer et exécuter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans cette boîte de dialogue, vous pouvez spécifier le nombre maximal de projets Visual C++ ou Visual C# pouvant être générés simultanément, certains comportements de génération par défaut et certains paramètres du journal de génération. Pour ouvrir la boîte de dialogue **Options**, choisissez **Outils**, **Options** dans la barre de menus. Pour accéder à ce jeu d’options, développez **Projets et solutions**, puis choisissez **Générer et exécuter**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **nombre maximal de générations de projets en parallèle** Spécifie le nombre maximal de projets Visual C++ et Visual C# qui peuvent être générés en même temps. Pour optimiser le processus de génération, le nombre maximal de générations de projets en parallèle est automatiquement défini par rapport au nombre de processeurs équipant votre ordinateur. La valeur maximale est de 32.

 **Générer uniquement des projets de démarrage et des dépendances à l’exécution** Seul le projet de démarrage et ses dépendances sont générés si cette case à cocher est activée lorsque vous appuyez sur la touche F5. Choisissez **Déboguer**, **Démarrer** dans la barre de menus. ou choisissez **générer**, **générer** dans la barre de menus. Tous les projets, dépendances et fichiers solution sont générés si cette case est décochée quand vous appuyez sur la touche F5, quand vous choisissez **Déboguer**, **Démarrer** dans la barre de menus, ou quand vous choisissez **Build**, **Build** dans la barre de menus. Cette option est décochée par défaut.

 **À l'exécution, lorsque les projets sont obsolètes**
 > [!NOTE]
> Cette liste s'applique aux projets [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] uniquement.

 Par défaut, un message s'affiche si une configuration de projet est obsolète quand vous appuyez sur la touche F5 ou quand vous choisissez **Déboguer**, **Démarrer** dans la barre de menus. Vous pouvez spécifier s'il faut ou non générer le projet obsolète, et si un message doit s'afficher. Utilisez cette option pour spécifier si le message s'affiche et, s'il ne s'affiche pas, indiquer le comportement de génération souhaité.

 **Toujours générer** La boîte de message ne s’affiche pas, et le projet est généré en dépit de la configuration obsolète. Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Oui**.

 **Ne jamais générer** La boîte de message ne s’affiche pas et le projet n’est pas généré. Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Non**.

 **Inviter à générer** Affiche la boîte de message chaque fois qu’une configuration de projet est obsolète.

 **À l’exécution, lorsque des erreurs de génération ou de déploiement se produisent** Si des erreurs de build se produisent lorsque vous démarrez une build à partir du menu **générer** , un message s’affiche. Vous pouvez spécifier s'il faut continuer en démarrant l'application et si le message doit s'afficher dès qu'une erreur de génération se produit. Utilisez cette option pour spécifier si le message s'affiche et, s'il ne s'affiche pas, indiquer le comportement souhaité.

> [!NOTE]
> Cette option s'applique aux projets [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] uniquement.

 **Inviter à lancer** Affiche une boîte de message chaque fois que des erreurs de build se produisent.

 **Ne pas lancer** La boîte de message ne s’affiche pas et l’application n’est pas démarrée. Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Non**.

 **Lancer l’ancienne version** La boîte de message ne s’affiche pas et la nouvelle version générée de l’application n’est pas démarrée. Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Oui**.

 **Pour les nouvelles solutions, utiliser le projet actuellement sélectionné comme projet de démarrage** Si cette case à cocher est activée, les nouvelles solutions utilisent le projet actuellement sélectionné comme projet de démarrage.

 **Commentaires sur la sortie de génération du projet MSBuild** Détermine la quantité d’informations qui s’affiche dans la fenêtre **sortie** de la génération.

 **Commentaires du fichier journal de génération du projet MSBuild**
 > [!NOTE]
> Cette option s'applique aux projets Visual C++ uniquement.

 Détermine la quantité d’informations qui sont écrites dans le fichier journal de génération, qui se trouve dans \\ ... \\ *NomProjet*\Debug. \\ *ProjectName*. log.

## <a name="see-also"></a>Voir aussi
 [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)
