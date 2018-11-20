---
title: Utilisation des outils Visual Studio pour Mac pour Unity
description: Ce guide explique comment utiliser l’extension Outils Visual Studio pour Mac pour Unity
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: b53de918f51abd03d28173bf00d83d98503e86bd
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348928"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Utilisation des outils Visual Studio pour Mac pour Unity

Dans cette section, vous allez apprendre à utiliser les fonctionnalités d’intégration et de productivité des outils Visual Studio pour Mac pour Unity, ainsi qu’à utiliser le débogueur Visual Studio pour Mac pour le développement Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Ouverture de scripts Unity dans Visual Studio pour Mac

Une fois que Visual Studio pour Mac est [défini comme éditeur de scripts externe pour Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), l’ouverture d’un script à partir de l’éditeur Unity lance automatiquement Visual Studio pour Mac (ou bascule sur la fenêtre ouverte) avec le script choisi ouvert.

Visual Studio pour Mac peut aussi être ouvert sans ouvrir de script dans l’éditeur de code source, en sélectionnant **Ouvrir un projet C#** dans le menu **Ressources** dans Unity.

![Ouvrir un projet C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Accès à la documentation Unity

Les outils Visual Studio pour Mac pour Unity offrent un raccourci pour accéder à la documentation de l’API Unity. Pour accéder à la documentation de l’API Unity à partir de Visual Studio pour Mac, placez le curseur sur l’API Unity pour laquelle vous souhaitez obtenir des informations, puis appuyez sur **Commande ⌘ + ‘**.

## <a name="intellisense-for-unity-messages"></a>IntelliSense pour les messages Unity
Le moteur Unity diffuse des messages aux scripts MonoBehaviour, ce qui permet aux développeurs d’écrire du code qui réagit aux messages comme OnMouseDown, OnTriggerEnter, etc. Parce qu’il ne s’agit pas de méthodes virtuelles dans la classe de base MonoBehaviour, certains IDE comme MonoDevelop n’ont pas de fonctionnalité de complétion du code pour les messages Unity.

Toutefois, les outils Visual Studio pour Mac pour Unity étendent leur fonctionnalité IntelliSense aux messages Unity. De cette façon, l’implémentation des messages Unity dans les scripts MonoBehaviour est plus facile, de même que l’apprentissage de l’API Unity. Pour utiliser IntelliSense pour les messages Unity :

1. Placez le curseur sur une nouvelle ligne dans le corps d’une classe qui dérive de MonoBehaviour.

2. Commencez à taper le nom d’un message Unity, par exemple, `OnTriggerEnter`.

3. Une fois que les lettres « **ont** » ont été tapées, une liste de suggestions IntelliSense s’affiche.

   ![Using IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Vous pouvez changer la sélection dans la liste de trois façons :

   * Avec les flèches **Haut** et **Bas**.

   * En cliquant avec la souris sur l’élément souhaité.

   * En continuant de taper le nom de l’élément souhaité.

5. IntelliSense peut insérer le message Unity sélectionné, y compris tous les paramètres nécessaires :

   * En appuyant sur **Tab**.

   * En appuyant sur **Entrée**.

   * En double-cliquant sur l’élément sélectionné.

   ![Insérer un message Unity à partir d’IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Ajout de nouveaux fichiers et dossiers Unity

Tandis que vous pouvez toujours ajouter de nouveaux fichiers à un projet Unity dans l’éditeur Unity, Visual Studio pour Mac permet de créer facilement des scripts, nuanceurs et dossiers Unity à partir de Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Ajouter un nouveau script C# MonoBehaviour

Pour ajouter un nouveau script C# MonoBehaviour, **cliquez avec le bouton droit sur le dossier Ressources** ou sur l’un de ses sous-répertoires dans le panneau Solutions, puis sélectionnez **Ajouter > Nouveau MonoBehaviour**.

![Ajouter un nouveau MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Ajouter un nouveau nuanceur Unity

Pour ajouter un nouveau nuanceur Unity, **cliquez avec le bouton droit sur le dossier Ressources** ou sur un sous-répertoire dans le panneau Solutions, puis sélectionnez **Ajouter > Nouveau nuanceur**.

### <a name="add-a-new-folder"></a>Ajouter un nouveau dossier

Pour ajouter un nouveau dossier, **cliquez avec le bouton droit sur le dossier Ressources** ou sur un sous-répertoire dans le panneau Solutions, puis sélectionnez **Ajouter -> Nouveau dossier**.

Ces ajouts sont répercutés dans la fenêtre Projet de l’éditeur Unity.

### <a name="to-rename-a-file-or-folder"></a>Pour renommer un fichier ou un dossier
**Cliquez avec le bouton droit** sur l’élément à renommer dans le panneau Solutions et sélectionnez **Renommer...**.

> [!NOTE]
> Si vous avez un nouveau projet Unity sans script et que le dossier Ressources ne s’affiche pas dans le panneau Solutions dans Visual Studio pour Mac, ajoutez un script C# initial à partir de l’éditeur Unity.

## <a name="unity-debugging"></a>Débogage Unity

Les projets Unity peuvent être débogués avec Visual Studio pour Mac.

### <a name="start-debugging"></a>Démarrer le débogage

Pour démarrer le débogage :

1. Connectez Visual Studio à Unity en cliquant sur le bouton **Lire**, ou appuyez sur **Commande + Entrée** ou **F5**.

   ![Cliquer sur Lire dans Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Basculez sur Unity et cliquez sur le bouton **Lire** pour exécuter le jeu dans l’éditeur.

   ![Cliquer sur Lire dans Unity](media/using-vsmac-tools-unity-image6.png)

3. Quand le jeu s’exécute dans l’éditeur Unity, tout en étant connecté à Visual Studio, les points d’arrêt rencontrés suspendent l’exécution du jeu et affichent la ligne de code où le jeu a rencontré le point d’arrêt dans Visual Studio pour Mac.

### <a name="stop-debugging"></a>Arrêter le débogage

Pour arrêter le débogage :

1. Cliquez sur le bouton **Arrêter** dans Visual Studio pour Mac ou appuyez sur **MAJ + Commande + Entrée**.

   ![Cliquer sur Arrêter dans Visual Studio](media/using-vsmac-tools-unity-image7.png)

Pour en savoir plus sur le débogage dans Visual Studio pour Mac, consultez [Utilisation du débogueur](debugging.md).
