---
title: Installer Visual Studio pour Mac
description: Instructions sur l’installation de Visual Studio pour Mac et des composants supplémentaires nécessaires pour le développement multiplateforme.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 5ad3154390494c3d949ceba1cc84ded87d33a3fd
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294992"
---
# <a name="set-up-and-install-visual-studio-for-mac"></a>Installer et configurer Visual Studio pour Mac

## <a name="setup"></a>Installation

Pour commencer à développer des applications multiplateformes natives quand vous téléchargez Visual Studio pour Mac, vous devez installer et configurer un certain nombre de choses.

Pour travailler avec iOS dans Visual Studio, vous avez besoin des éléments suivants :

* un Mac avec macOS Sierra 10.12 ou ultérieur
* Xcode 8.3 ou ultérieur. La dernière version stable est généralement recommandée.
* un ID Apple. Si vous n’avez pas encore d’identifiant Apple, vous pouvez en créer un sur https://appleid.apple.com. Un ID Apple est nécessaire pour installer et se connecter à Xcode.

## <a name="install"></a>Installez

1. Télécharger Visual Studio pour Mac à partir de [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com/)

2. Une fois le package d’installation téléchargé, cliquez sur le fichier **VisualStudioInstaller.dmg** pour monter le programme d’installation puis exécutez-le en double-cliquant sur le logo, comme illustré dans l’image suivante :

   ![Boîte de dialogue Programme d’installation](media/installer-image1.png)

3. Une boîte de dialogue d’alerte similaire à celle de l’image suivante peut s’afficher. Dans ce cas, cliquez sur **Ouvrir** :

   ![Boîte de dialogue d’alerte](media/installer-image2.png)

4. Le programme d’installation inspecte votre système pour vérifier quels composants doivent être installés ou mis à jour :

   ![Évaluation de votre système](media/installer-image3.png)

5. Une boîte de dialogue d’alerte vous est alors présentée, vous demandant d’accepter les termes du contrat de licence et de confidentialité. Cliquez sur le bouton **Continuer** pour accepter les termes du contrat :

   ![Boîte de dialogue Licence](media/installer-image4.png)

6. Le programme d’installation affiche une liste des composants nécessaires manquants, et qui doivent être téléchargés et installés. Sélectionnez les produits que vous voulez télécharger ici :

   ![Sélectionner des éléments](media/installer-image5.png)

   Si vous ne souhaitez pas installer toutes les plateformes, utilisez le guide ci-dessous pour vous aider à choisir les plateformes à installer :

   * **Applications utilisant Xamarin** :
      - Xamarin.Forms – Sélectionnez les plateformes **Android** et **iOS**.
      - iOS uniquement – Sélectionnez la plateforme **iOS** (notez que vous devrez installer [ **Xcode**](https://developer.apple.com/xcode/)).
      - Android uniquement – Sélectionnez la plateforme **Android** (notez que vous devez également sélectionner les dépendances correspondantes).
      - Mac uniquement – Sélectionnez la plateforme **macOS** (notez que vous devrez installer [ **Xcode**](https://developer.apple.com/xcode/)).
      - Applications Xamarin entièrement multiplateformes – Sélectionnez les plateformes **Android**, **iOS** et **macOS**.
   * **Applications .NET Core** – Sélectionnez la plateforme **.NET Core**.
   * **Applications web ASP.NET Core** – Sélectionnez la plateforme **.NET Core**.
   * **Développement de jeux Unity multiplateformes** – aucune plateforme supplémentaire ne doit être installée en plus de Visual Studio pour Mac. Reportez-vous au [guide d’installation Unity](setup-vsmac-tools-unity.md) pour plus d’informations sur l’installation de l’extension Unity.

   Cet écran d’installation affiche la version et la taille de chaque composant. Vous pouvez cliquer sur chaque composant pour afficher une liste des dépendances pour ce composant (pour Android), voir les packages supplémentaires qu’il télécharge (pour .NET Core), ou afficher les applications supplémentaires nécessaires (pour iOS et macOS) :

   ![Dépendances supplémentaires d’Android](media/installer-image6.png)

7. Une fois que vous êtes satisfait de votre sélection, sélectionnez le bouton **Installer et mettre à jour** pour démarrer le processus d’installation.

8. Le programme d’installation démarre le processus de téléchargement et d’installation des éléments sélectionnés :

   ![Démarrage de l’installation](media/installer-image7.png)

   ![Téléchargement de Xamarin.Mac](media/installer-image8.png)

   ![Fin de l’installation](media/installer-image9.png)

9. Vous pouvez être invité à élever les autorisations nécessaires pour des composants individuels nécessaires pour terminer l’installation. Entrez vos informations d’identification d’administrateur ici pour continuer le processus d’installation :

   ![Entrer les autorisations pour continuer avec le programme d’installation](media/installer-image10.png)

10. Une fois l’installation terminée, vous pouvez démarrer le développement d’applications dans Visual Studio en cliquant sur **Démarrer** :

    ![Ouvrir Visual Studio](media/installer-image11.png)

> [!NOTE]
> Si vous avez choisi pas installer un outil ou une plateforme lors de l’installation d’origine (en la désélectionnant à l’étape 6), vous devez réexécuter le [programme d’installation](https://visualstudio.microsoft.com/vs/) si vous voulez ajouter les composants plus tard.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installer Visual Studio pour Mac derrière un pare-feu ou un serveur proxy

Pour installer Visual Studio pour Mac derrière un pare-feu, certains points de terminaison doivent être rendus accessibles afin d’autoriser les téléchargements des outils requis et des mises à jour pour votre logiciel.

Configurez votre réseau de façon à autoriser l’accès aux emplacements suivants :

* [Points de terminaison de Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Étapes suivantes

L’installation de Visual Studio pour Mac vous permet de commencer à écrire du code pour vos applications. Les guides suivants sont fournis pour vous guider à travers les étapes d’écriture et de déploiement de vos projets.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Approvisionnement d’appareil](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(pour exécuter votre application sur l’appareil).

### <a name="android"></a>Android

1. [Utilisation de Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Émulateur SDK Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Configuration de l’appareil pour le développement](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Applications web .NET Core et ASP.NET Core, développement de jeux Unity

Pour les autres charges de travail, reportez-vous à la page [charges de travail](workloads.md).

## <a name="see-also"></a>Voir aussi

- [Installer Visual Studio 2017 (sur Windows)](/visualstudio/install/install-visual-studio)