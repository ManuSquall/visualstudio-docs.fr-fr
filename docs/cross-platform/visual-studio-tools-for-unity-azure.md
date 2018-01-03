---
title: "Procédure pas à pas Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: d5242dd873591abee15f528d09b6f588ea12f5ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>Utilisation des tables faciles Azure avec Unity - Procédure pas à pas

![Capture d’écran d’un exemple de jeu](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>Introduction

Azure fournit une solution scalable pour le stockage des données de télémétrie et d’autres données de jeu dans le cloud. Avec la version Unity 2017, la prise en charge de .NET 4.6 par Unity rend l’intégration d’Azure plus simple que jamais en permettant l’utilisation du kit SDK Azure Mobile Client.

Ces étapes vous guident dans le processus de configuration d’un projet Unity qui tire parti d’Azure pour enregistrer les données de télémétrie et de classement dans le cloud.

> [!NOTE]
> Ce projet requiert le runtime de script Mono .NET 4.6 « Expérimental » dans Unity 2017. [Unity a déclaré que ce sera bientôt la version par défaut](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/) mais, pour l’instant, elle est toujours qualifiée « d’expérimentale » et vous pouvez rencontrer des problèmes.

> Cette procédure pas à pas décrit un exemple de connexion à un back-end Azure Mobile App à partir d’une build de PC Unity. Au moment de la rédaction de ce document, des problèmes connus empêchent ce projet de fonctionner sur les plateformes Mac et Android. Bien qu’il s’agisse de problèmes connus qui seront corrigés, la chronologie est incertaine. Pour plus d’informations, visitez le [forum Experimental Scripting Previews](https://forum.unity3d.com/forums/experimental-scripting-previews.107/) d’Unity.

## <a name="download-the-completed-project"></a>Télécharger le projet terminé

Le projet terminé est disponible sur GitHub. Toutefois, la procédure pas à pas suppose que vous démarrez à partir d’un nouveau projet vide et fournit des liens pour télécharger des ressources si nécessaire.

## <a name="walkthrough-steps"></a>Étapes de la procédure pas à pas

1. [Configurer les tables faciles dans Azure](visual-studio-tools-for-unity-azure-configure.md)
2. [Créer des tables faciles](visual-studio-tools-for-unity-azure-setup.md)
3. [Préparer l’environnement de développement](visual-studio-tools-for-unity-azure-prepare.md)
4. [Créer des classes de modèles de données](visual-studio-tools-for-unity-azure-data.md)
5. [Implémenter Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [Mettre à jour le magasin de certificats de sécurité Unity Mono](visual-studio-tools-for-unity-azure-security.md)
7. [Tester la connexion du client](visual-studio-tools-for-unity-azure-connection.md)
7. [Importer les ressources de l’exemple de jeu](visual-studio-tools-for-unity-azure-game-assets.md)
8. [Tester l’exemple de jeu](visual-studio-tools-for-unity-azure-game.md)
9. [Explication de RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
10. [Explication de HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [Explication de LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>Étape suivante
* [Configurer les tables faciles dans Azure](visual-studio-tools-for-unity-azure-configure.md)
