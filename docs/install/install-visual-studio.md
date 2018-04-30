---
title: Installer Visual Studio 2017 │ Microsoft Docs
description: Découvrez comment installer Visual Studio, étape par étape.
ms.custom: ''
ms.date: 12/04/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c39496b09c72c6c5eb72fb1c5bedb59285d01347
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="install-visual-studio-2017"></a>Installer Visual Studio 2017

Découvrez une nouvelle façon d’installer Visual Studio ! Dans notre toute nouvelle version, nous avons facilité la sélection et l’installation des seules fonctionnalités nécessaires. Nous avons également réduit l’encombrement minimal de Visual Studio afin qu’il s’installe plus rapidement et avec moins d’impact sur le système qu’auparavant.

Vous voulez en savoir plus sur les autres nouveautés de cette version ? Consultez nos [notes de publication](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Prêt pour l’installation ? Nous allons vous guider dans les étapes de l’installation.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Étape 1 : Vérifier que votre ordinateur est prêt pour Visual Studio

Avant de commencer l’installation de Visual Studio :

1. Vérifiez la [configuration requise](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). Celle-ci vous permet de savoir si votre ordinateur prend en charge Visual Studio 2017.
2. Appliquez les dernières mises à jour Windows Update. Ces mises à jour permettent de garantir que votre ordinateur dispose à la fois des dernières mises à jour de sécurité et des composants système obligatoires pour Visual Studio.
3. Redémarrez. Le redémarrage garantit que les éventuelles installations et mises à jour en attente n’entravent pas l’installation de Visual Studio.
4. Libérez de l’espace. Supprimez les fichiers et applications inutiles de %SystemDrive%, par exemple en exécutant l’application de nettoyage du disque.

Pour toute question sur l’exécution de versions antérieures de Visual Studio côte à côte avec Visual Studio 2017, consultez la page [Informations sur la compatibilité de Visual Studio](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Étape 2 : Télécharger Visual Studio

Ensuite, téléchargez le fichier du programme d’amorçage de Visual Studio. Pour ce faire, cliquez sur le bouton Suivant, sélectionnez l’édition de Visual Studio 2017 que vous souhaitez, cliquez sur **Enregistrer**, puis cliquez sur **Ouvrir un dossier**.

 > [!div class="button"]
 > [Télécharger Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
<br/>

|         |         |
|---------|---------|
|  ![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regarder une vidéo")  |    [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) sur la façon de télécharger le fichier du programme d’amorçage de Visual Studio et de sélectionner l’édition de Visual Studio qui vous convient. |

## <a name="step-3---install-the-visual-studio-installer"></a>Étape 3 : Installer le programme d’installation de Visual Studio

Ensuite, exécutez le fichier du programme d’amorçage pour installer Visual Studio Installer. Ce nouveau programme d’installation léger inclut tout ce dont vous avez besoin pour installer et personnaliser Visual Studio 2017.

1. Dans votre dossier **Téléchargements**, double-cliquez sur le programme d’amorçage correspondant ou similaire à l’un des fichiers suivants :

  * **vs_enterprise.exe** pour Visual Studio Enterprise
  * **vs_professional.exe** pour Visual Studio Professional
  * **vs_community.exe** pour Visual Studio Community  <br><br>

  Si vous recevez une notification du contrôle de compte d’utilisateur, cliquez sur **Oui**.

2. Vous devez accepter les [Termes du contrat de licence](https://www.visualstudio.com/license-terms/) Microsoft et la [Déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkID=824704) Microsoft. Cliquez sur **Continuer**.  

   ![Termes du contrat de licence et déclaration de confidentialité](media/vs2017-privacy-and-license-terms.PNG "Termes du contrat de licence et déclaration de confidentialité Microsoft")

## <a name="step-4---select-workloads"></a>Étape 4 : Sélectionner les charges de travail

Une fois le programme d’installation installé, vous pouvez l’utiliser pour personnaliser votre installation en sélectionnant les ensembles de fonctionnalités, ou les charges de travail, que vous souhaitez. Voici comment procéder.

1. Recherchez la charge de travail que vous voulez dans l’écran **Installation de Visual Studio**.

 ![Sélectionnez une charge de travail à partir de la boîte de dialogue d’installation de Visual Studio 2017.](../install/media/install-visual-studio-enterprise.png)

     Par exemple, choisissez la charge de travail « Développement .NET Desktop ». Elle comprend l’éditeur principal par défaut, qui inclut une prise en charge de la modification du code de base pour plus de 20 langues, la possibilité d’ouvrir et de modifier le code dans n’importe quel dossier sans projet et un contrôle de code source intégré.  

2. Après avoir sélectionné la ou les charges de travail que vous souhaitez, cliquez sur **Installer**.

    Ensuite, des écrans d’état affichent la progression de votre installation de Visual Studio.

3. Une fois les nouveaux composants et charges de travail installés, cliquez sur **Lancer**.  

> [!TIP]
> À tout moment après l’installation, vous pouvez installer les charges de travail ou les composants que vous n’avez pas installés au début. Si Visual Studio est ouvert, accédez à **Outils** > **Obtenir les outils et fonctionnalités** pour ouvrir Visual Studio Installer. Vous pouvez également ouvrir **Visual Studio Installer** à partir du menu Démarrer. À partir de là, vous pouvez sélectionner les charges de travail ou les composants que vous souhaitez installer, puis cliquer sur **Modifier**.  

|         |         |
|---------|---------|
|  ![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regarder une vidéo")  |    [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) sur la façon d’installer Visual Studio Installer, puis d’installer une charge de travail. |

## <a name="step-5---select-individual-components-optional"></a>Étape 5 : Sélectionner les différents composants (facultatif)

Si vous ne souhaitez pas utiliser la fonctionnalité Charges de travail pour personnaliser votre installation de Visual Studio, vous pouvez pour cela installer les composants séparément. Pour sélectionner des composants, cliquez sur l’option **Composants individuels** à partir de Visual Studio Installer, sélectionnez ce que vous souhaitez, puis suivez les invites.

  ![Visual Studio 2017 - Installer des composants individuels](media/vs2017-components.PNG "Installer des composants individuels de Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regarder une vidéo")  |   [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) sur l’installation d’un composant individuel à l’aide de Visual Studio Installer. |

## <a name="step-6---install-language-packs-optional"></a>Étape 6 : Installer les modules linguistiques (facultatif)

Par défaut, le programme d’installation essaie d’installer la langue du système d’exploitation quand vous l’exécutez pour la première fois. Pour installer Visual Studio 2017 dans la langue de votre choix, cliquez sur l’option **Modules linguistiques** dans le programme d’installation de Visual Studio et suivez les invites.

  ![Visual Studio 2017 - Installer des modules linguistiques](media/vs2017-languages.PNG "Installer des modules linguistiques de Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regarder une vidéo")  |   [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) sur l’installation d’un module linguistique à l’aide de Visual Studio Installer. |

### <a name="change-the-installer-language-from-the-command-line"></a>Changer la langue du programme d’installation à partir de la ligne de commande

Une autre façon de changer la langue par défaut consiste à exécuter le programme d’installation à partir de la ligne de commande. Par exemple, vous pouvez forcer le programme d’installation à s’exécuter en anglais en utilisant la commande suivante : `vs_installer.exe --locale en-US`. Le programme d’installation enregistre ce paramètre pour une prochaine exécution. Le programme d’installation prend en charge les jetons de langue suivants : zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru et tr-tr.

## <a name="step-7---start-developing"></a>Étape 7 : Démarrer le développement

1. Lorsque l’installation de Visual Studio est terminée, cliquez sur le bouton **Lancer** pour [bien démarrer avec le développement Visual Studio](../ide/get-started-developing-with-visual-studio.md).

2. Cliquez sur **Fichier**, puis cliquez sur **Nouveau projet**.

3. Sélectionnez un type de projet. <br><br>
   Par exemple, pour [créer une application C++](../ide/getting-started-with-cpp-in-visual-studio.md), cliquez sur **Installé**, développez **Visual C++**, puis sélectionnez le type de projet C++ que vous souhaitez générer. <br><br>
   Pour [créer une application C#](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), cliquez sur **Installé**, développez **Visual C#**, puis sélectionnez le type de projet C# que vous souhaitez générer.

## <a name="get-support"></a>Obtenir de l’aide

Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :

* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit et obtenir des réponses dans la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter](https://gitter.im/Microsoft/VisualStudio). (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Modifier Visual Studio 2017](modify-visual-studio.md)
* [Désinstaller Visual Studio 2017](uninstall-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Guide de l’administrateur Visual Studio 2017](visual-studio-administrator-guide.md)
  * [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Installer les outils de génération dans un conteneur](build-tools-container.md)
