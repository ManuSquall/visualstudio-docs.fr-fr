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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0aa325aa016b95a0dac0047f4b6fe9ae67f52ecc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800860"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Options (boîte de dialogue), Projets et solutions, Générer et exécuter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Dans cette boîte de dialogue, vous pouvez spécifier le nombre maximal de projets Visual C++ ou Visual C# pouvant être générés simultanément, certains comportements de génération par défaut et certains paramètres du journal de génération. Pour ouvrir la boîte de dialogue **Options**, choisissez **Outils**, **Options** dans la barre de menus. Pour accéder à ce jeu d’options, développez **Projets et solutions**, puis choisissez **Générer et exécuter**.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Nombre maximal de générations de projets en parallèle**  
 Spécifie le nombre maximal de projets Visual C++ et Visual C# qui peuvent être générés en même temps. Pour optimiser le processus de génération, le nombre maximal de générations de projets en parallèle est automatiquement défini par rapport au nombre de processeurs équipant votre ordinateur. Le nombre maximal est 32.  
  
 **Générer uniquement des projets de démarrage et des dépendances à l'exécution**  
 Seul le projet de démarrage et ses dépendances sont générés si cette case est cochée quand vous appuyez sur la touche F5, quand vous choisissez **Déboguer**, **Démarrer** dans la barre de menus, ou quand vous choisissez **Build**, **Build** dans la barre de menus. Tous les projets, dépendances et fichiers solution sont générés si cette case est décochée quand vous appuyez sur la touche F5, quand vous choisissez **Déboguer**, **Démarrer** dans la barre de menus, ou quand vous choisissez **Build**, **Build** dans la barre de menus. Cette option est décochée par défaut.  
  
 **À l'exécution, lorsque les projets sont obsolètes**  
 > [!NOTE]
>  Cette liste s'applique aux projets [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] uniquement.  
  
 Par défaut, un message s'affiche si une configuration de projet est obsolète quand vous appuyez sur la touche F5 ou quand vous choisissez **Déboguer**, **Démarrer** dans la barre de menus. Vous pouvez spécifier s'il faut ou non générer le projet obsolète, et si un message doit s'afficher. Utilisez cette option pour spécifier si le message s'affiche et, s'il ne s'affiche pas, indiquer le comportement de génération souhaité.  
  
 **Toujours générer**  
 Le message ne s'affiche pas, et le projet est généré malgré sa configuration obsolète. Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Oui**.  
  
 **Ne jamais générer**  
 Le message ne s'affiche pas, et le projet n'est pas généré. Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Non**.  
  
 **Inviter à générer**  
 Affiche le message chaque fois qu'une configuration de projet est obsolète.  
  
 **À l’exécution, lors d’erreurs de génération ou de déploiement**  
 Si des erreurs de génération se produisent quand vous démarrez une génération à partir du menu **Build**, un message s'affiche. Vous pouvez spécifier s'il faut continuer en démarrant l'application et si le message doit s'afficher dès qu'une erreur de génération se produit. Utilisez cette option pour spécifier si le message s'affiche et, s'il ne s'affiche pas, indiquer le comportement souhaité.  
  
> [!NOTE]
>  Cette option s'applique aux projets [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] uniquement.  
  
 **Inviter à lancer**  
 Affiche un message chaque fois qu'une erreur de génération se produit.  
  
 **Ne pas lancer**  
 Le message ne s'affiche pas, et l'application n'est pas démarrée. Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Non**.  
  
 **Lancer l’ancienne version**  
 Le message ne s'affiche pas, et la nouvelle version de l'application générée n'est pas démarrée. Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Oui**.  
  
 **Pour les nouvelles solutions, utiliser le projet sélectionné actuellement comme projet de démarrage**  
 Si cette case est cochée, toutes les nouvelles solutions utilisent le projet actuellement sélectionné comme projet de démarrage.  
  
 **Commentaires relatifs à la sortie de build du projet MSBuild**  
 Détermine quelles informations s’affichent dans la fenêtre **Sortie** de la build.  
  
 **Commentaires du fichier journal de génération du projet MSBuild**  
 > [!NOTE]
>  Cette option s'applique aux projets Visual C++ uniquement.  
  
 Détermine quelles informations sont écrites dans le fichier journal de build, qui se trouve dans \\...\\*Nom_Projet*\Debug\\*Nom_Projet*.log.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)
