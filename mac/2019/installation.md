---
title: Installer la préversion de Visual Studio 2019 pour Mac
description: Instructions sur l’installation de la préversion de Visual Studio 2019 pour Mac et des composants supplémentaires nécessaires au développement multiplateforme.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 17acdd63b5632cf141cc5407ce8e09be3e3a69a0
ms.sourcegitcommit: a260df15214b3198a28ca4e312263942cf6f4ce7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2019
ms.locfileid: "54443778"
---
# <a name="install-visual-studio-2019-for-mac-preview"></a>Installer la préversion de Visual Studio 2019 pour Mac

> [!NOTE]
> La préversion de Visual Studio 2019 pour Mac est installable côte à côte avec la dernière version stable de Visual Studio pour Mac. Lors de l’installation, vous devrez mettre à jour Visual Studio s’il ne s’agit pas de la dernière version stable.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Spécifications de la préversion de Visual Studio 2019 pour Mac

- Mac avec macOS High Sierra 10.13 ou ultérieur

Pour générer des applications Xamarin pour iOS ou macOS, vous devez également disposer des éléments suivants :

- Xcode 10.0 ou ultérieur. La dernière version stable est généralement recommandée.
- un ID Apple. Si vous n’avez pas encore d’identifiant Apple, vous pouvez en créer un sur https://appleid.apple.com. Un ID Apple est nécessaire pour installer et se connecter à Xcode.

## <a name="installing-the-preview"></a>Installation de la préversion

1. Téléchargez le programme d’installation de la préversion à partir de la [page Préversion de Visual Studio pour Mac](https://aka.ms/vs4mac-preview).
2. Une fois le téléchargement terminé, cliquez sur **VisualStudioforMacPreviewInstaller.dmg** pour monter le programme d’installation, puis exécutez-le en double-cliquant sur le logo d’une flèche :

    [![Cliquer sur la grande flèche pour commencer l’installation](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. Un avertissement peut s’afficher pour vous informer que l’application est téléchargée à partir d’Internet. Cliquez sur **Ouvrir**.
4. Patientez pendant que le programme d’installation vérifie votre système :

    [![Le programme d’installation vérifie les composants installés sur votre système](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Une alerte s’affiche pour vous demander d’accepter les termes de la déclaration de confidentialité et du contrat de licence. Suivez les liens pour les lire, puis appuyez sur **Continuer** si vous les acceptez :

    [![Suivre les liens vers les termes de la déclaration de confidentialité et du contrat de licence, puis continuer si vous les acceptez](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. La liste des charges de travail disponibles s’affiche. Sélectionnez celles que vous souhaitez utiliser :

    [![Choisir les fonctionnalités facultatives de la charge de travail à installer](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Si votre version actuelle de Visual Studio 2017 pour Mac est antérieure à 7.7, vous devrez approuver une mise à niveau vers la dernière version stable (nécessaire pour prendre en charge l’installation côte à côte). Appuyez sur **Continuer** pour approuver la mise à niveau :

    ![Mise à niveau obligatoire de la version stable vers 7.7](media/install-preview-older-upgrade.png)

7. Après avoir effectué vos sélections, appuyez sur le bouton **Installer**.
8. Le programme d’installation affiche la progression du téléchargement et de l’installation de Visual Studio pour Mac et des charges de travail sélectionnées. Vous pouvez être invité à entrer votre mot de passe pour accorder les privilèges nécessaires à l’installation.
9. Utilisez **Visual Studio (préversion)** chaque fois que vous souhaitez tester la préversion ou revenir à la dernière version stable de Visual Studio pour votre travail de production. Les deux icônes sont indiquées ici :

    ![Différence entre l’icône de la version stable et celle de la préversion](media/install-preview-icons-sml.png)

Si vous rencontrez des problèmes réseau durant l’installation dans un environnement d’entreprise, passez en revue les instructions [d’installation derrière un pare-feu ou un proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Découvrez-en plus sur les changements dans les [notes de publication](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

> [!NOTE]
> Si vous avez choisi de ne pas installer certains outils ou plateformes lors de l’installation d’origine (en les désélectionnant à l’étape 6), vous devrez réexécuter le programme d’installation si vous souhaitez ajouter ces composants plus tard.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installer Visual Studio pour Mac derrière un pare-feu ou un serveur proxy

Pour installer Visual Studio pour Mac derrière un pare-feu, certains points de terminaison doivent être rendus accessibles afin d’autoriser les téléchargements des outils requis et des mises à jour pour votre logiciel.

Configurez votre réseau de façon à autoriser l’accès aux emplacements suivants :

- [Points de terminaison de Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

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

Pour les autres charges de travail, reportez-vous à la page [charges de travail](/visualstudio/mac/workloads).

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Voir aussi

- [Installer Visual Studio 2017 (sur Windows)](/visualstudio/install/install-visual-studio)
