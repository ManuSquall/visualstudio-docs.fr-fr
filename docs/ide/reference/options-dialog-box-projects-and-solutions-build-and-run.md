---
title: "Options (bo&#238;te de dialogue), Projets et solutions, G&#233;n&#233;rer et ex&#233;cuter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.Build_and_Run"
  - "VS.ToolsOptionsPag.Projects.Build_and_Run"
helpviewer_keywords: 
  - "builds (Visual Studio), configuration"
  - "actions d'exécution"
  - "débogueur, options d’exécution"
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Options (bo&#238;te de dialogue), Projets et solutions, G&#233;n&#233;rer et ex&#233;cuter
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans cette boîte de dialogue, vous pouvez spécifier le nombre maximal de projets Visual C\+\+ ou Visual C\# pouvant être générés simultanément, certains comportements de génération par défaut et certains paramètres du journal de génération.  Pour ouvrir la boîte de dialogue **Options**, choisissez **Outils**, **Options** dans la barre de menus.  Pour accéder à ce jeu d'options, développez **Projets et solutions**, puis choisissez **Générer et exécuter**.  
  
## Liste UIElement  
 **Nombre maximal de générations de projets en parallèle**  
 Spécifie le nombre maximal de projets Visual C\+\+ et Visual C\# qui peuvent être générés en même temps.  Pour optimiser le processus de génération, le nombre maximal de générations de projets en parallèle est automatiquement défini par rapport au nombre de processeurs équipant votre ordinateur.  Le nombre maximal est 32.  
  
 **Générer uniquement des projets de démarrage et des dépendances à l'exécution**  
 Seul le projet de démarrage et ses dépendances sont générés si cette case est cochée quand vous appuyez sur la touche F5, quand vous choisissez **Déboguer**, **Démarrer** dans la barre de menus, ou quand vous choisissez **Build**, **Build** dans la barre de menus.  Tous les projets, dépendances et fichiers solution sont générés si cette case est décochée quand vous appuyez sur la touche F5, quand vous choisissez **Déboguer**, **Démarrer** dans la barre de menus, ou quand vous choisissez **Build**, **Build** dans la barre de menus.  Cette option est décochée par défaut.  
  
 **À l'exécution, lorsque les projets sont obsolètes**  
 > [!NOTE]
>  Cette liste s'applique aux projets [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] uniquement.  
  
 Par défaut, un message s'affiche si une configuration de projet est obsolète quand vous appuyez sur la touche F5 ou quand vous choisissez **Déboguer**, **Démarrer** dans la barre de menus.  Vous pouvez spécifier s'il faut ou non générer le projet obsolète, et si un message doit s'afficher.  Utilisez cette option pour spécifier si le message s'affiche et, s'il ne s'affiche pas, indiquer le comportement de génération souhaité.  
  
 **Toujours générer**  
 Le message ne s'affiche pas, et le projet est généré malgré sa configuration obsolète.  Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Oui**.  
  
 **Ne jamais générer**  
 Le message ne s'affiche pas, et le projet n'est pas généré.  Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Non**.  
  
 **Inviter à générer**  
 Affiche le message chaque fois qu'une configuration de projet est obsolète.  
  
 **À l'exécution, lors d'erreurs de génération ou de déploiement**  
 Si des erreurs de génération se produisent quand vous démarrez une génération à partir du menu **Build**, un message s'affiche.  Vous pouvez spécifier s'il faut continuer en démarrant l'application et si le message doit s'afficher dès qu'une erreur de génération se produit.  Utilisez cette option pour spécifier si le message s'affiche et, s'il ne s'affiche pas, indiquer le comportement souhaité.  
  
> [!NOTE]
>  Cette option s'applique aux projets [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] uniquement.  
  
 **Inviter à lancer**  
 Affiche un message chaque fois qu'une erreur de génération se produit.  
  
 **Ne pas lancer**  
 Le message ne s'affiche pas, et l'application n'est pas démarrée.  Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Non**.  
  
 **Lancer l'ancienne version**  
 Le message ne s'affiche pas, et la nouvelle version de l'application générée n'est pas démarrée.  Pour spécifier cette option, cochez **Ne plus afficher cette boîte de dialogue** dans le message et cliquez sur le bouton **Oui**.  
  
 **Pour les nouvelles solutions, utiliser le projet sélectionné actuellement comme projet de démarrage**  
 Si cette case est cochée, toutes les nouvelles solutions utilisent le projet actuellement sélectionné comme projet de démarrage.  
  
 **Commentaires relatifs à la sortie de génération du projet MSBuild**  
 Détermine quelles informations s'affichent dans la fenêtre **Sortie** pour la génération.  
  
 **Commentaires du fichier journal de génération du projet MSBuild**  
 > [!NOTE]
>  Cette option s'applique aux projets Visual C\+\+ uniquement.  
  
 Détermine quelles informations sont écrites dans le fichier journal de génération, situé dans \\...  \\*NomProjet*\\Debug\\*NomProjet*.log.  
  
## Voir aussi  
 [Génération d'applications dans Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)