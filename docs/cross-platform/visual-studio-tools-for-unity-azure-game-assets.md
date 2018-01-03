---
title: "Procédure pas à pas des ressources de jeu Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 19b98dc472b9e01529725b95133d289edff6334d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="import-sample-game-assets"></a>Importer les ressources de l’exemple de jeu

Maintenant que la fonctionnalité principale a été testée et que son fonctionnement a été démontré, il est temps d’importer les ressources de l’exemple de jeu.

## <a name="import-package"></a>Importer un package

1. Téléchargez le [package des ressources de l’exemple de jeu](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage).

2. Vérifiez que votre projet Unity est ouvert, puis accédez à l’emplacement de téléchargement et double-cliquez sur le fichier. La boîte de dialogue d’importation s’affiche dans Unity.

3. Cliquez sur **All** (Tout), puis sur **Importer**. Attendez que les barres de progression obtenues s’arrêtent.

  ![Importer un package](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>Ajouter des scènes aux paramètres de build

Une fois l’importation des fichiers terminée, les fichiers de scène nécessaires doivent être ajoutés aux paramètres de build du projet Unity.

1. Dans la fenêtre Projet d’Unity, accédez au répertoire **Azure Easy Tables sample game assets/Scenes** (Ressources de l’exemple de jeu des tables faciles Azure/Scènes).

2. Dans le menu Unity, sélectionnez **Fichier > Paramètres de build...** . La boîte de dialogue Paramètres de build s’affiche alors.

3. Faites glisser les fichiers **HeatmapScene**, **LeaderboardScene**, **MenuScene** et **RaceScene** de la fenêtre Projet dans la section **Scenes In Build** (Scènes dans la build) de la boîte de dialogue Paramètres de build.

  ![Importer un package](media/vstu_azure-import-sample-assets-image2.png)

4. Dans le menu Unity, sélectionnez **Fichier > Enregistrer le projet** pour garantir que les paramètres de build sont enregistrés.

## <a name="next-step"></a>Étape suivante

* [Tester l’exemple de jeu](visual-studio-tools-for-unity-azure-game.md)