---
title: Installation des outils Visual Studio pour Mac pour Unity
description: Configuration et installation des outils Unity à utiliser dans Visual Studio pour Mac
author: dantogno
ms.author: v-davian
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 3409bca77605bd55d0de15b38eb4812743af813e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836344"
---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Installation des outils Visual Studio pour Mac pour Unity

Cette section explique comment préparer l’utilisation des outils Visual Studio pour Mac pour Unity.

## <a name="install-visual-studio-for-mac"></a>Installer Visual Studio pour Mac

### <a name="unity-bundled-installation"></a>Installation collective de Unity

À partir de Unity 2018.1, Visual Studio pour Mac est l’IDE C# par défaut pour Unity, et est inclus dans l’Assistant Téléchargement Unity, ainsi que dans l’outil d’installation Unity Hub. Téléchargez Unity à partir de [store.unity.com](https://store.unity.com/).

Lors de l’installation, vérifiez que Visual Studio pour Mac est coché dans la liste des composants à installer avec Unity :

#### <a name="unity-hub"></a>Unity Hub

![installation de unity hub](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Assistant Téléchargement de Unity

![installation de l’assistant téléchargement de Unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Vérifier les mises à jour de Visual Studio pour Mac

La version de Visual Studio pour Mac fournie avec l’installation de Unity n’est peut-être pas la dernière version. Nous vous recommandons de rechercher les mises à jour pour être sûr d’avoir accès aux tout derniers outils et fonctionnalités.

* [Mise à jour de Visual Studio pour Mac](update.md)

### <a name="manual-installation"></a>Installation manuelle

Si vous avez déjà Unity 5.6.1 ou version ultérieure, mais que vous n’avez pas Visual Studio pour Mac, vous pouvez installer manuellement Visual Studio pour Mac. Toutes les éditions de Visual Studio pour Mac sont fournies avec les outils Visual Studio pour Mac pour Unity, notamment l’édition Community gratuite :

* Téléchargez Visual Studio pour Mac à partir de [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
* Les outils Visual Studio pour Mac pour Unity sont installés automatiquement lors du processus d’installation.
* Pour obtenir de l’aide supplémentaire sur l’installation, suivez les étapes du [guide d’installation](installation.md) .

> [!NOTE]
> Visual Studio pour Mac pour Unity nécessite Unity 5.6.1 ou ultérieur. Pour vérifier que les outils Visual Studio pour Unity sont activés dans votre version de Unity, sélectionnez **À propos de Unity** dans le menu Unity et recherchez le texte « Microsoft Visual Studio Tools pour Unity activé » dans la partie inférieure gauche de la boîte de dialogue.
>
> ![À propos de Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Vérifiez que l’extension Outils Visual Studio pour Mac pour Unity est activée.

L’extension Outils Visual Studio pour Mac pour Unity doit normalement être activée par défaut, vous pouvez néanmoins le vérifier, ainsi que le numéro de la version installée :

1. Dans le menu Visual Studio, sélectionnez **Extensions...**.

   ![Sélectionner Extensions](media/setup-vsmac-tools-unity-image1.png)

2. Développez la section Développement de jeux et vérifiez qu’il existe bien une entrée Outils Visual Studio pour Mac pour Unity.

   ![Afficher l’entrée Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Configurer Unity pour une utilisation avec Visual Studio pour Mac

À partir de Unity 2018.1, Visual Studio doit être l’éditeur de script externe par défaut dans Unity. Vous pouvez vérifier cela ou choisir Visual Studio comme éditeur de script externe :

1. Sélectionnez **Préférences...** dans le menu Unity.

   ![Sélectionner Préférences](media/setup-vsmac-tools-unity-image4.png)

2. Dans la boîte de dialogue Préférences, sélectionnez l’onglet **Outils externes**.

3. Dans la liste déroulante Éditeur de script externe, choisissez **Visual Studio** s’il est répertorié, sinon sélectionnez **Parcourir...**.

   ![Sélectionner Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Si vous avez sélectionné **Parcourir...**, accédez au répertoire Applications, sélectionnez Visual Studio puis cliquez sur **Ouvrir**.

   ![Sélectionner Ouvrir](media/setup-vsmac-tools-unity-image6.png)

5. Une fois que Visual Studio est sélectionné dans la liste **Éditeur de script externe**, fermez la boîte de dialogue Préférences pour terminer le processus de configuration.
