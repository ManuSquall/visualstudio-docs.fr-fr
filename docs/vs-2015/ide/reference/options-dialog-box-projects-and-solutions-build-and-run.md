---
title: Options (boîte de dialogue), Projets et solutions, Générer et exécuter | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 9669437ff47bc141c898a61c055b3a0de8d5d235
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189291"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Options (boîte de dialogue), Projets et solutions, Générer et exécuter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Dans cette boîte de dialogue, vous pouvez spécifier le nombre maximal de projets Visual C++ ou Visual C# pouvant être générés simultanément, certains comportements de génération par défaut et certains paramètres du journal de génération. Pour ouvrir le **Options** boîte de dialogue, sélectionnez **outils**, **Options** sur la barre de menus. Pour accéder à cet ensemble d’options, développez **projets et Solutions**, puis choisissez **générer et exécuter**.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Nombre maximal de générations de projets en parallèle**  
 Spécifie le nombre maximal de projets Visual C++ et Visual C# qui peuvent être générés en même temps. Pour optimiser le processus de génération, le nombre maximal de générations de projets en parallèle est automatiquement défini par rapport au nombre de processeurs équipant votre ordinateur. Le nombre maximal est 32.  
  
 **Générer uniquement des projets de démarrage et des dépendances à l'exécution**  
 Uniquement le projet de démarrage et ses dépendances sont générés si cette case à cocher est activée lorsque vous appuyez sur la touche F5 ; Choisissez **déboguer**, **Démarrer** dans le menu barre ; ou choisissez **Build**, **Build** sur la barre de menus. Tous les projets, les dépendances et les fichiers solution sont générés si cette case à cocher est désactivée lorsque vous appuyez sur la touche F5 ; Choisissez **déboguer**, **Démarrer** dans le menu barre ; ou choisissez **Build**, **Build** sur la barre de menus. Cette option est décochée par défaut.  
  
 **À l'exécution, lorsque les projets sont obsolètes**  
 > [!NOTE]
>  Cette liste s'applique aux projets [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] uniquement.  
  
 Par défaut, un message s’affiche si une configuration de projet est obsolète lorsque vous appuyez sur la touche F5 ou choisissez **déboguer**, **Démarrer** sur la barre de menus. Vous pouvez spécifier s'il faut ou non générer le projet obsolète, et si un message doit s'afficher. Utilisez cette option pour spécifier si le message s'affiche et, s'il ne s'affiche pas, indiquer le comportement de génération souhaité.  
  
 **Toujours générer**  
 Le message ne s'affiche pas, et le projet est généré malgré sa configuration obsolète. Cette option est définie lorsque vous sélectionnez le **ne plus afficher cette boîte de dialogue** zone dans le message, puis choisissez le **Oui** bouton.  
  
 **Ne jamais générer**  
 Le message ne s'affiche pas, et le projet n'est pas généré. Cette option est définie lorsque vous sélectionnez le **ne plus afficher cette boîte de dialogue** zone dans le message, puis choisissez le **non** bouton.  
  
 **Inviter à générer**  
 Affiche le message chaque fois qu'une configuration de projet est obsolète.  
  
 **À l’exécution, lors d’erreurs de génération ou de déploiement**  
 Si des erreurs de build se produisent lorsque vous démarrez une build à partir de la **Build** menu, un message s’affiche. Vous pouvez spécifier s'il faut continuer en démarrant l'application et si le message doit s'afficher dès qu'une erreur de génération se produit. Utilisez cette option pour spécifier si le message s'affiche et, s'il ne s'affiche pas, indiquer le comportement souhaité.  
  
> [!NOTE]
>  Cette option s'applique aux projets [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] uniquement.  
  
 **Inviter à lancer**  
 Affiche un message chaque fois qu'une erreur de génération se produit.  
  
 **Ne pas lancer**  
 Le message ne s'affiche pas, et l'application n'est pas démarrée. Cette option est définie lorsque vous sélectionnez le **ne plus afficher cette boîte de dialogue** case à cocher dans la boîte de message, puis choisissez le **non** bouton.  
  
 **Lancer l’ancienne version**  
 Le message ne s'affiche pas, et la nouvelle version de l'application générée n'est pas démarrée. Cette option est définie lorsque vous sélectionnez le **ne plus afficher cette boîte de dialogue** case à cocher dans la boîte de message, puis choisissez le **Oui** bouton.  
  
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



