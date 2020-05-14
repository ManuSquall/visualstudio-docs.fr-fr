---
title: Installer Visual Studio 2019 pour Mac
description: Instructions sur l’installation de Visual Studio 2019 pour Mac et des composants supplémentaires nécessaires pour le développement multiplateforme.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 45f9756607cbb638d1f69f77bdf8cd2ee30953c5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75851949"
---
# <a name="install-visual-studio-2019-for-mac"></a>Installer Visual Studio 2019 pour Mac

Pour commencer à développer des applications .NET natives multiplateformes sur macOS, installez Visual Studio 2019 pour Mac en suivant les étapes ci-dessous.

 > [!div class="button"]
 > [Télécharger Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Spécifications

- Mac avec macOS High Sierra 10.12 ou ultérieur.

Pour générer des applications Xamarin pour iOS ou macOS, vous devez également disposer des éléments suivants :

- Xcode 10.0 ou ultérieur. La dernière version stable est généralement recommandée.
- un ID Apple. Si vous n’avez pas encore d’identifiant Apple, vous pouvez en créer un sur https://appleid.apple.com. Un ID Apple est nécessaire pour installer et se connecter à Xcode.

## <a name="installation-instructions"></a>Instructions d’installation

1. Téléchargez le programme d’installation à partir de la [page de téléchargement de Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/).
2. Une fois le téléchargement terminé, cliquez sur **VisualStudioforMacInstaller.dmg** pour monter le programme d’installation, puis exécutez-le en double-cliquant sur le logo en forme de flèche :

    [![Cliquez sur la grande flèche pour commencer l’installation](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Un avertissement peut s’afficher pour vous informer que l’application est téléchargée à partir d’Internet. Cliquez sur **Ouvrir**.
4. Patientez pendant que le programme d’installation vérifie votre système :

    [![L’installateur vérifie votre système pour les composants installés](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Une alerte s’affiche pour vous demander d’accepter les termes de la déclaration de confidentialité et du contrat de licence. Suivez les liens pour les lire, puis appuyez sur **Continuer** si vous les acceptez :

    [![Suivez les liens vers la confidentialité et les conditions, puis continuez si vous êtes d’accord](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. La liste des charges de travail disponibles s’affiche. Sélectionnez les composants que vous souhaitez utiliser :

    [![Choisissez les fonctionnalités de charge de travail facultatives que vous souhaitez installer](media/install-selection.png)](media/install-selection.png#lightbox)

   Si vous ne souhaitez pas installer toutes les plateformes, utilisez le guide ci-dessous pour vous aider à choisir les plateformes à installer :


|Type d’application  |Cible  |Sélection  |Notes  |
|---------|---------|---------|---------|
|**Applications utilisant Xamarin**| Xamarin.Forms|Sélectionnez les plateformes **Android** et **iOS** |Vous devrez installer [ **Xcode**](https://developer.apple.com/xcode/) |
||iOS uniquement|Sélectionnez la plate-forme **iOS**|Vous devrez installer [ **Xcode**](https://developer.apple.com/xcode/)|
||Android uniquement|Sélectionnez la plate-forme **Android**|Notez que vous devez également sélectionner les dépendances pertinentes|
||Mac seulement|Sélectionnez la plate-forme **macOS (Cocoa)**|Vous devrez installer [ **Xcode**](https://developer.apple.com/xcode/)|
|**Applications .NET Core**|         |Sélectionnez la plate-forme **.NET Core.**|         |
|**Applications web ASP.NET Core**|         |Sélectionnez la plate-forme **.NET Core.**|         |
|**Azure Functions**|         |Sélectionnez la plate-forme **.NET Core.**|         |
|**Développement de jeux Unity multiplateformes**|         |Aucune plateforme supplémentaire n’a besoin d’être installée au-delà de Visual Studio pour Mac.| Reportez-vous au [guide d’installation Unity](/visualstudio/mac/setup-vsmac-tools-unity) pour plus d’informations sur l’installation de l’extension Unity.|


7. Après avoir effectué vos sélections, appuyez sur le bouton **Installer**.
8. Le programme d’installation affiche la progression du téléchargement et de l’installation de Visual Studio pour Mac et des charges de travail sélectionnées. Vous serez invité à entrer votre mot de passe pour accorder les privilèges nécessaires à l’installation.:

    [![Choisissez les fonctionnalités de charge de travail facultatives que vous souhaitez installer](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Une fois installé, Visual Studio pour Mac vous incitera à personnaliser votre installation en vous connectant et en sélectionnant les fixations clés que vous souhaitez utiliser :

    [![Connectez-vous à l’IDE](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Choisissez les raccourcis clavier que vous souhaitez utiliser](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Si vous rencontrez des problèmes réseau durant l’installation dans un environnement d’entreprise, passez en revue les instructions [d’installation derrière un pare-feu ou un proxy](/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Découvrez-en plus sur les changements dans les [notes de publication](/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Si vous avez choisi de ne pas installer certains outils ou plateformes lors de l’installation d’origine (en les désélectionnant à l’étape 6), vous devez réexécuter le programme d’installation si vous souhaitez ajouter ces composants plus tard.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installer Visual Studio pour Mac derrière un pare-feu ou un serveur proxy

Pour installer Visual Studio pour Mac derrière un pare-feu, certains points de terminaison doivent être rendus accessibles afin d’autoriser les téléchargements des outils requis et des mises à jour pour votre logiciel.

Configurez votre réseau de façon à autoriser l’accès aux emplacements suivants :

- [Points de terminaison de Visual Studio](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Étapes suivantes

L’installation de Visual Studio pour Mac vous permet de commencer à écrire du code pour vos applications. Les guides suivants sont fournis pour vous guider à travers les étapes d’écriture et de déploiement de vos projets.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Approvisionnement d’appareil](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(pour exécuter votre application sur l’appareil).

### <a name="android"></a>Android

1. [Utilisation de Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Émulateur du kit Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Mettre en place un dispositif de développement](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Applications web .NET Core et ASP.NET Core, développement de jeux Unity

Pour les autres charges de travail, reportez-vous à la page [charges de travail](workloads.md).

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Voir aussi

- [Installer Visual Studio (sur Windows)](/visualstudio/install/install-visual-studio)
