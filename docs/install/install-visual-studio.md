---
title: Installer Visual Studio
titleSuffix: ''
description: Découvrez comment installer Visual Studio, étape par étape.
ms.date: 02/11/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2ceb871dfc8c6c5a07a0a176b8344944edacd893
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58325303"
---
# <a name="install-visual-studio"></a>Installer Visual Studio

Découvrez une nouvelle façon d’installer Visual Studio ! Dans cette version, nous vous avons simplifié la tâche en vous permettant de sélectionner et d’installer uniquement les fonctionnalités nécessaires. Nous avons également réduit l’encombrement minimal de Visual Studio afin qu’il s’installe plus rapidement et avec moins d’impact sur le système qu’auparavant.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Installer Visual Studio pour Mac](/visualstudio/mac/installation).

Vous voulez en savoir plus sur les autres nouveautés de cette version ? Consultez nos [notes de publication](/visualstudio/releasenotes/vs2017-relnotes).

Prêt pour l’installation ? Nous allons vous guider dans les étapes de l’installation.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Étape 1 : Vérifier que votre ordinateur est prêt pour Visual Studio

Avant de commencer l’installation de Visual Studio :

1. Vérifiez la [configuration requise](/visualstudio/productinfo/vs2017-system-requirements-vs). Celle-ci vous permet de savoir si votre ordinateur prend en charge Visual Studio 2017.
2. Appliquez les dernières mises à jour Windows Update. Ces mises à jour permettent de garantir que votre ordinateur dispose à la fois des dernières mises à jour de sécurité et des composants système obligatoires pour Visual Studio.
3. Redémarrez. Le redémarrage garantit que les éventuelles installations et mises à jour en attente n’entravent pas l’installation de Visual Studio.
4. Libérez de l’espace. Supprimez les fichiers et applications inutiles de %SystemDrive%, par exemple en exécutant l’application de nettoyage du disque.

Pour toute question sur l’exécution de versions antérieures de Visual Studio côte à côte avec Visual Studio 2017, consultez la page [Informations sur la compatibilité de Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Étape 2 : Télécharger Visual Studio

Ensuite, téléchargez le fichier du programme d’amorçage de Visual Studio. Pour ce faire, cliquez sur le bouton Suivant, sélectionnez l’édition de Visual Studio 2017 que vous souhaitez, cliquez sur **Enregistrer**, puis cliquez sur **Ouvrir un dossier**.

 > [!div class="button"]
 > [Télécharger Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

## <a name="step-3---install-the-visual-studio-installer"></a>Étape 3 : Installer le programme d’installation de Visual Studio

Ensuite, exécutez le fichier du programme d’amorçage pour installer Visual Studio Installer. Ce nouveau programme d’installation léger inclut tout ce dont vous avez besoin pour installer et personnaliser Visual Studio 2017.

1. Dans votre dossier **Téléchargements**, double-cliquez sur le programme d’amorçage correspondant ou similaire à l’un des fichiers suivants :

   * **vs_enterprise.exe** pour Visual Studio Enterprise
   * **vs_professional.exe** pour Visual Studio Professional
   * **vs_community.exe** pour Visual Studio Community  <br><br>

   Si vous recevez une notification du contrôle de compte d’utilisateur, cliquez sur **Oui**.

2. Vous devez accepter les [Termes du contrat de licence](https://visualstudio.microsoft.com/license-terms/) Microsoft et la [Déclaration de confidentialité](https://privacy.microsoft.com/privacystatement) Microsoft. Cliquez sur **Continuer**.

   ![Termes du contrat de licence et déclaration de confidentialité](media/vs2017-privacy-and-license-terms.PNG "Termes du contrat de licence et déclaration de confidentialité Microsoft")

## <a name="step-4---select-workloads"></a>Étape 4 : Sélectionner les charges de travail

Une fois le programme d’installation installé, vous pouvez l’utiliser pour personnaliser votre installation en sélectionnant les ensembles de fonctionnalités, ou les charges de travail, que vous souhaitez. Voici comment procéder.

1. Recherchez la charge de travail que vous voulez dans l’écran **Installation de Visual Studio**.

   ![Sélectionnez une charge de travail à partir de la boîte de dialogue d’installation de Visual Studio 2017.](../install/media/install-visual-studio-community.png)

     Par exemple, choisissez la charge de travail « Développement .NET Desktop ». Elle comprend l’éditeur principal par défaut, qui inclut une prise en charge de la modification du code de base pour plus de 20 langues, la possibilité d’ouvrir et de modifier le code dans n’importe quel dossier sans projet et un contrôle de code source intégré.

2. Après avoir sélectionné la ou les charges de travail que vous souhaitez, cliquez sur **Installer**.

    Ensuite, des écrans d’état affichent la progression de votre installation de Visual Studio.

3. Une fois les nouveaux composants et charges de travail installés, cliquez sur **Lancer**.

> [!TIP]
> À tout moment après l’installation, vous pouvez installer les charges de travail ou les composants que vous n’avez pas installés au début. Si Visual Studio est ouvert, accédez à **Outils** > **Obtenir les outils et fonctionnalités** pour ouvrir Visual Studio Installer. Vous pouvez également ouvrir **Visual Studio Installer** à partir du menu Démarrer. À partir de là, vous pouvez sélectionner les charges de travail ou les composants que vous souhaitez installer, puis cliquer sur **Modifier**.

## <a name="step-5---select-individual-components-optional"></a>Étape 5 : Sélectionner les différents composants (facultatif)

Si vous ne souhaitez pas utiliser la fonctionnalité Charges de travail pour personnaliser votre installation de Visual Studio, vous pouvez pour cela installer les composants séparément. Pour sélectionner des composants, cliquez sur l’option **Composants individuels** à partir de Visual Studio Installer, sélectionnez ce que vous souhaitez, puis suivez les invites.

  ![Visual Studio 2017 - Installer des composants individuels](media/vs2017-components.PNG "Installer des composants individuels de Visual Studio")

## <a name="step-6---install-language-packs-optional"></a>Étape 6 : Installer les modules linguistiques (facultatif)

Par défaut, le programme d’installation essaie d’installer la langue du système d’exploitation quand vous l’exécutez pour la première fois. Pour installer Visual Studio 2017 dans la langue de votre choix, cliquez sur l’option **Modules linguistiques** dans le programme d’installation de Visual Studio et suivez les invites.

  ![Visual Studio 2017 - Installer des modules linguistiques](media/vs2017-languages.PNG "Installer des modules linguistiques de Visual Studio")

### <a name="change-the-installer-language-from-the-command-line"></a>Changer la langue du programme d’installation à partir de la ligne de commande

Une autre façon de changer la langue par défaut consiste à exécuter le programme d’installation à partir de la ligne de commande. Par exemple, vous pouvez forcer le programme d’installation à s’exécuter en anglais en utilisant la commande suivante : `vs_installer.exe --locale en-US`. Le programme d’installation enregistre ce paramètre pour une prochaine exécution. Le programme d’installation prend en charge les jetons de langue suivants : zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru et tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Étape 7 : Changer l’emplacement d’installation (facultatif)

**Nouveautés de la version 15.7** : Vous pouvez désormais réduire l’encombrement de l’installation de Visual Studio sur votre lecteur système. Vous pouvez choisir de déplacer le cache de téléchargement, les composants partagés, les SDK et les outils vers d’autres lecteurs et de conserver Visual Studio sur le lecteur qui l’exécute le plus rapidement.

  ![Visual Studio 2017 : changer l’emplacement d’installation](media/installation-options-by-location.png "Changer l’emplacement d’installation")

Pour plus d’informations, consultez la page [Changer les emplacements d’installation de Visual Studio](change-installation-locations.md).

## <a name="step-8---start-developing"></a>Étape 8 : Démarrer le développement

1. Une fois l’installation de Visual Studio terminée, cliquez sur le bouton **Lancer** pour commencer le développement avec Visual Studio.

2. Cliquez sur **Fichier**, puis cliquez sur **Nouveau projet**.

3. Sélectionnez un type de projet.

   Par exemple, pour [créer une application C++](../ide/getting-started-with-cpp-in-visual-studio.md), cliquez sur **Installé**, développez **Visual C++**, puis sélectionnez le type de projet C++ que vous souhaitez générer.

   Pour [créer une application C#](../get-started/csharp/tutorial-wpf.md), cliquez sur **Installé**, développez **Visual C#**, puis sélectionnez le type de projet C# que vous souhaitez générer.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Mettre à jour Visual Studio](update-visual-studio.md)
* [Modifier Visual Studio](modify-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Installer Visual Studio pour Mac](/visualstudio/mac/installation)