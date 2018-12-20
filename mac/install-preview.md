---
title: Installer une préversion
description: Instructions pour mettre à jour Visual Studio pour Mac et accéder aux préversions, notamment Visual Studio 2019 pour Mac.
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 0E1EF257-9DE4-4653-9DF4-805CE007A1A1
ms.openlocfilehash: b5eea8c2c894b7eeaa13c83ae6698d1297de9297
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896755"
---
# <a name="install-a-preview-release"></a>Installer une préversion

::: zone pivot="vsmac2019"

> [!TIP]
> La préversion de Visual Studio 2019 pour Mac est maintenant disponible. Pour la première fois, vous pouvez l’installer côte à côte avec la dernière version stable de Visual Studio pour Mac.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Spécifications de la préversion de Visual Studio 2019 pour Mac

* Mac avec macOS High Sierra 10.13 ou ultérieur

Pour générer des applications Xamarin pour iOS ou macOS, vous devez également disposer des éléments suivants :

* Xcode 10.0 ou ultérieur. La dernière version stable est généralement recommandée.
* Un identifiant Apple. Si vous n’avez pas encore d’identifiant Apple, vous pouvez en créer un sur https://appleid.apple.com. Un identifiant Apple est nécessaire pour installer et se connecter à Xcode.

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

    Si votre version actuelle de Visual Studio pour Mac 2017 est antérieure à 7.7, vous serez invité à approuver une mise à niveau vers la dernière version stable (celle-ci étant nécessaire pour prendre en charge l’installation côte à côte). Appuyez sur **Continuer** pour approuver la mise à niveau :

    ![Mise à niveau obligatoire de la version stable vers 7.7](media/install-preview-older-upgrade.png)

7. Après avoir effectué vos sélections, appuyez sur le bouton **Installer**.
8. Le programme d’installation affiche la progression du téléchargement et de l’installation de Visual Studio pour Mac et des charges de travail sélectionnées. Vous pouvez être invité à entrer votre mot de passe pour accorder les privilèges nécessaires à l’installation.
9. Utilisez **Visual Studio (préversion)** chaque fois que vous souhaitez tester la préversion ou revenir à la dernière version stable de Visual Studio pour votre travail de production. Les deux icônes sont indiquées ici :

    ![Différence entre l’icône de la version stable et celle de la préversion](media/install-preview-icons-sml.png)

Si vous rencontrez des problèmes réseau durant l’installation dans un environnement d’entreprise, passez en revue les instructions [d’installation derrière un pare-feu ou un proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Découvrez-en plus sur les changements dans les [notes de publication](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

::: zone-end
::: zone pivot="vsmac2017"

## <a name="install-an-update-for-visual-studio-2017-for-mac"></a>Installer une mise à jour pour Visual Studio 2017 pour Mac

Avant la sortie officielle d’une nouvelle version de Visual Studio pour Mac, une préversion est disponible. La préversion vous donne l’occasion de tester les nouvelles fonctionnalités et d’obtenir les derniers correctifs avant leur intégration au produit.

Les préversions de Visual Studio pour Mac sont distribuées sous forme de mises à jour, et non par le biais de téléchargements séparés. Comme décrit dans l’article sur la [mise à jour](update.md) de Visual Studio pour Mac, il existe trois canaux de mise à jour : Stable, Bêta et Alpha.

Si la plupart des préversions sont disponibles dans les canaux **Bêta** et **Alpha**, veillez à toujours consulter les [notes de préversion](/visualstudio/releasenotes/vs2017-mac-preview-relnotes) pour obtenir des informations précises.

Pour installer la préversion de Visual Studio pour Mac, effectuez les étapes suivantes :

1. Accédez à **Visual Studio > Rechercher les mises à jour**.
2. Dans la zone de liste modifiable Canal de mise à jour, sélectionnez **Bêta**.
3. Sélectionnez le bouton **Changer de canal** pour passer au canal sélectionné et démarrer, le cas échéant, le téléchargement de nouvelles mises à jour.
4. Pour lancer l’installation des mises à jour, sélectionnez le bouton **Redémarrer et installer les mises à jour**.

Pour plus d’informations, consultez l’article sur la [mise à jour](update.md) de Visual Studio pour Mac.

::: zone-end