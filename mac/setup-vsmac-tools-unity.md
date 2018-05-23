---
title: Installation des outils Visual Studio pour Mac pour Unity
description: Configuration et installation des outils Unity à utiliser dans Visual Studio pour Mac
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: f9a6da6c30132d6303705019919dfcad9f8cd484
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Installation des outils Visual Studio pour Mac pour Unity

Cette section explique comment préparer l’utilisation des outils Visual Studio pour Mac pour Unity.

## <a name="install-visual-studio-for-mac"></a>Installer Visual Studio pour Mac

Téléchargez et installez Visual Studio pour Mac. Toutes les éditions de Visual Studio pour Mac prennent en charge les outils Visual Studio pour Mac pour Unity, notamment l’édition Community gratuite :

* Téléchargez Visual Studio pour Mac à partir de [visualstudio.com](https://www.visualstudio.com/).
* Les outils Visual Studio pour Mac pour Unity sont installés automatiquement lors du processus d’installation.
* Pour obtenir de l’aide supplémentaire sur l’installation, suivez les étapes du [guide d’installation](installation.md) .

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Vérifiez que l’extension Outils Visual Studio pour Mac pour Unity est activée.

L’extension Outils Visual Studio pour Mac pour Unity doit normalement être activée par défaut, vous pouvez néanmoins le vérifier, ainsi que le numéro de la version installée :

1.  Dans le menu Visual Studio, sélectionnez **Extensions...**.

  ![Sélectionner Extensions](media/setup-vsmac-tools-unity-image1.png)

2.  Développez la section Développement de jeux et vérifiez qu’il existe bien une entrée Outils Visual Studio pour Mac pour Unity.

  ![Afficher l’entrée Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>Installer Unity

Visual Studio pour Mac pour Unity nécessite Unity 5.6.1 ou ultérieur. Tous les forfaits Unity fonctionnent avec Visual Studio Tools pour Unity, notamment le forfait personnel gratuit. Téléchargez Unity à partir de [store.unity.com](https://store.unity.com/).

> [!NOTE]
> Pour vérifier que les outils Visual Studio pour Unity sont activés dans votre version de Unity, sélectionnez **À propos de Unity** dans le menu Unity et recherchez le texte « Microsoft Visual Studio Tools pour Unity activé » dans la partie inférieure gauche de la boîte de dialogue.
>
>   ![À propos de Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Configurer Unity pour une utilisation avec Visual Studio pour Mac

Visual Studio doit être défini comme éditeur de script externe dans Unity :

1.  Sélectionnez **Préférences...** dans le menu Unity.

  ![Sélectionner Préférences](media/setup-vsmac-tools-unity-image4.png)

2.  Dans la boîte de dialogue Préférences, sélectionnez l’onglet **Outils externes**.

3.  Dans la liste déroulante Éditeur de script externe, choisissez **Visual Studio** s’il est répertorié, sinon sélectionnez **Parcourir...**.

  ![Sélectionner Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4.  Si vous avez sélectionné **Parcourir...**, accédez au répertoire Applications, sélectionnez Visual Studio puis cliquez sur **Ouvrir**.

  ![Sélectionner Ouvrir](media/setup-vsmac-tools-unity-image6.png)

5.  Une fois que Visual Studio est sélectionné dans la liste **Éditeur de script externe**, fermez la boîte de dialogue Préférences pour terminer le processus de configuration.
