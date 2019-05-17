---
title: Installer Visual Studio 2019 pour Mac
description: Instructions sur l’installation de Visual Studio 2019 pour Mac et des composants supplémentaires nécessaires pour le développement multiplateforme.
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 92b8fdceb1f4cfcfc54f9e37aea3a93f765976a3
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615456"
---
# <a name="install-visual-studio-2019-for-mac"></a>Installer Visual Studio 2019 pour Mac

Pour commencer à développer des applications .NET natives multiplateformes sur macOS, installez Visual Studio 2019 pour Mac en suivant les étapes ci-dessous.

## <a name="requirements"></a>Spécifications

- Mac avec macOS High Sierra 10.12 ou ultérieur.

Pour générer des applications Xamarin pour iOS ou macOS, vous devez également disposer des éléments suivants :

- Xcode 10.0 ou ultérieur. La dernière version stable est généralement recommandée.
- un ID Apple. Si vous n’avez pas encore d’identifiant Apple, vous pouvez en créer un sur https://appleid.apple.com. Un ID Apple est nécessaire pour installer et se connecter à Xcode.

## <a name="installation-instructions"></a>Instructions d’installation

1. Téléchargez le programme d’installation à partir de la [page de téléchargement de Visual Studio pour Mac](https://aka.ms/vsmac).
2. Une fois le téléchargement terminé, cliquez sur **VisualStudioforMacInstaller.dmg** pour monter le programme d’installation, puis exécutez-le en double-cliquant sur le logo en forme de flèche :

    [![Cliquer sur la grande flèche pour commencer l’installation](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Un avertissement peut s’afficher pour vous informer que l’application est téléchargée à partir d’Internet. Cliquez sur **Ouvrir**.
4. Patientez pendant que le programme d’installation vérifie votre système :

    [![Le programme d’installation vérifie les composants installés sur votre système](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Une alerte s’affiche pour vous demander d’accepter les termes de la déclaration de confidentialité et du contrat de licence. Suivez les liens pour les lire, puis appuyez sur **Continuer** si vous les acceptez :

    [![Suivre les liens vers les termes de la déclaration de confidentialité et du contrat de licence, puis continuer si vous les acceptez](media/install-privacy-sml.png)](media/install-privacy.png#lightbox)

6. La liste des charges de travail disponibles s’affiche. Sélectionnez celles que vous souhaitez utiliser :

    [![Choisir les fonctionnalités facultatives de la charge de travail à installer](media/install-selection-sml.png)](media/install-selection.png#lightbox)

7. Après avoir effectué vos sélections, appuyez sur le bouton **Installer**.
8. Le programme d’installation affiche la progression du téléchargement et de l’installation de Visual Studio pour Mac et des charges de travail sélectionnées. Vous pouvez être invité à entrer votre mot de passe pour accorder les privilèges nécessaires à l’installation.

Si vous rencontrez des problèmes réseau durant l’installation dans un environnement d’entreprise, passez en revue les instructions [d’installation derrière un pare-feu ou un proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Découvrez-en plus sur les changements dans les [notes de publication](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Si vous avez choisi de ne pas installer certains outils ou plateformes lors de l’installation d’origine (en les désélectionnant à l’étape 6), vous devez réexécuter le programme d’installation si vous souhaitez ajouter ces composants plus tard.

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

Pour les autres charges de travail, reportez-vous à la page [charges de travail](workloads.md).

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Voir aussi

- [Installer Visual Studio (sur Windows)](/visualstudio/install/install-visual-studio)
