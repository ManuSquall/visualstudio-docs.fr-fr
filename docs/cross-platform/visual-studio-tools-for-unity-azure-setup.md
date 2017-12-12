---
title: "Procédure pas à pas d’installation Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: FFE17FC6-0B47-4A00-A125-01BD49E3873C
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 447f32c2e736084a08223b56f4188ca7c8abeea5
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="create-easy-tables"></a>Créer des tables faciles

Maintenant que vous avez une application mobile sur Azure avec des tables faciles initialisées, il est temps de générer les tables qui effectueront le suivi des données envoyées à partir d’un jeu Unity.

## <a name="setup-the-crash-heatmap-table"></a>Installer la table de carte thermique des incidents

1. Dans le portail Azure, cliquez sur Toutes les ressources, puis sélectionnez l’application mobile que vous avez configurée pour les tables faciles dans les étapes précédentes.

  ![Sélectionner l’application mobile](media/vstu_azure-setup-table-schema-image1.png)

2. Faites défiler vers le bas jusqu’au titre **MOBILE** et sélectionnez **Tables faciles**. Aucune notification ne doit plus s’afficher sur l’initialisation de votre application pour les tables faciles.  

  ![Sélectionner les tables faciles](media/vstu_azure-setup-table-schema-image2.png)

3. Cliquez sur le bouton **Ajouter**.

  ![Cliquer sur Ajouter](media/vstu_azure-setup-table-schema-image3.png)

4. Nommez la table « **CrashInfo** » et cliquez sur **OK**. Laissez le reste des options avec leurs paramètres par défaut.

  > [!WARNING]
  > Ce nom doit correspondre au nom de la classe du modèle de données créée ultérieurement dans la procédure pas à pas.

  ![Affecter un nom et cliquer sur OK](media/vstu_azure-setup-table-schema-image4.png)

5. Une notification indique quand la table a été créée.

> [!NOTE]
> Avec les tables faciles, le schéma de table est en fait créé dynamiquement par l’ajout de données. Cela signifie que les colonnes de données appropriées n’ont pas à être configurées manuellement au cours de cette étape.

## <a name="setup-the-leaderboard-table"></a>Installer la table de classement

1. Revenez au panneau Tables faciles et cliquez sur **Ajouter** pour ajouter une deuxième table.

  ![Ajouter une deuxième table](media/vstu_azure-setup-table-schema-image10.png)

2. Nommez la nouvelle table « **HighScoreInfo** » et cliquez sur **OK**. Laissez le reste des options avec leurs paramètres par défaut.

  > [!WARNING]
  > Ce nom doit correspondre au nom de la classe du modèle de données créée ultérieurement dans la procédure pas à pas.

  ![Affecter un nom et cliquer sur OK](media/vstu_azure-setup-table-schema-image11.png)

3. Une notification indique quand la table a été créée.


## <a name="next-step"></a>Étape suivante

* [Préparer l’environnement de développement](visual-studio-tools-for-unity-azure-prepare.md)
