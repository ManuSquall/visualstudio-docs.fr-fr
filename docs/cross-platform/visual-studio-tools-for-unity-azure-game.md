---
title: "Procédure pas à pas de jeu Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: DA86FC7F-E456-4DFC-84BF-D780421508B9
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 204389c2341c3aa9f729b92b5f3d459e7b101d24
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="test-the-sample-game"></a>Tester l’exemple de jeu

L’exemple de jeu est un jeu de course simple qui enregistre les données sur le comportement du joueur et les stocke dans les tables faciles Azure. L’exemple de jeu inclut également des scènes qui lisent les données à partir d’Azure et les représentent pour le joueur.

Cette section explique simplement comment jouer à l’exemple de jeu et vérifier qu’il fonctionne correctement. Les sections suivantes décrivent plus en détail le fonctionnement de l’exemple de jeu.

## <a name="starting-the-game"></a>Démarrage du jeu

1. Dans la fenêtre Projet d’Unity, accédez au dossier **Assets/Azure Easy Tables sample game assets/Scenes** (Ressources/Ressources de l’exemple de jeu des tables faciles Azure/Scènes).

2. Double-cliquez sur **MenuScene** pour l’ouvrir.

3. Dans la fenêtre Jeu d’Unity, cliquez sur le **menu déroulant des proportions** et choisissez **16:9**.

  ![Définir les proportions](media/vstu_azure-test-sample-game-image1.png)

4. Cliquez sur le bouton **Lire** pour exécuter le jeu dans l’éditeur Unity.


## <a name="complete-a-race"></a>Effectuer une course

Avant d’afficher le classement ou la carte thermique, il est préférable de créer des exemples de données en effectuant la course au moins une fois.

1. Tout en exécutant le jeu dans l’éditeur Unity, cliquez sur le bouton **Race!** (Course !) pour démarrer une nouvelle course.

2. Utilisez les touches **WASD** ou les **touches de direction** pour piloter la voiture et effectuer un tour dans le sens des aiguilles d’une montre autour de la piste. Dans l’intérêt de l’exemple, veillez à percuter quelques murs pendant la course. Une sortie de débogage dans la console Unity doit indiquer quand une collision a été enregistrée.

  >[!NOTE]
  > Si vous parvenez à retourner la voiture et n’êtes pas en mesure de continuer, cliquez sur **Redémarrer**. Les données ne sont envoyées à Azure qu’à la fin d’un tour.

  ![Démarrer une course](media/vstu_azure-test-sample-game-image2.png)

3. Après avoir franchi la ligne d’arrivée, le jeu doit afficher le message **Terminé**. À ce stade, les données d’incident sont chargées sur Azure.

4. Si vous avez effectué l’un des 10 tours les plus rapides, vous êtes invité à entrer un nom pour un score élevé. Entrez votre nom, puis cliquez sur **Envoyer**.

  ![Démarrer une course](media/vstu_azure-test-sample-game-image3.png)

## <a name="view-the-heatmap"></a>Afficher la carte thermique

1. Cliquez sur le bouton **View Crash Heatmap** (Afficher la carte thermique des incidents) à partir de la scène de course ou sélectionnez **Crash Heatmap** (Carte thermique des incidents) dans le menu principal.

2. La scène de carte thermique charge des données à partir de la table CrashInfo dans Azure et affiche une sphère rouge transparente aux emplacements où les joueurs ont heurté les murs de la piste de course. Si plusieurs incidents se produisent dans une zone de chevauchement, la couleur des sphères doit être plus vive.

  ![Carte thermique](media/vstu_azure-test-sample-game-image4.png)

## <a name="view-the-leaderboard"></a>Afficher le classement

1. Cliquez sur le bouton **Leaderboard** à partir de la scène de course ou dans le menu principal.

2. La scène de classement charge des données de scores élevés à partir de la table HighScoreInfo dans Azure et affiche un nom de joueur ainsi qu’un temps au tour pour chaque entrée de score élevé.

  ![Leaderboard](media/vstu_azure-test-sample-game-image5.png)

## <a name="next-step"></a>Étape suivante

* [Explication de RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
