---
title: "Installer Visual Studio 2017 │ Microsoft Docs"
description: "Découvrez comment installer Visual Studio, étape par étape."
ms.custom: 
ms.date: 05/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 9f7c1d33191adf3fb54cf59cd98ae5fffe14eee4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/31/2017

---
# <a name="install-visual-studio-2017"></a>Installer Visual Studio 2017
Découvrez une nouvelle façon d’installer Visual Studio ! Dans notre dernière version, nous avons simplifié la sélection et l’installation des fonctionnalités dont vous avez besoin, et nous avons réduit l’empreinte minimale de Visual Studio pour qu’il s’installe plus rapidement et avec moins d’impact système qu’auparavant.

Vous voulez en savoir plus sur les autres nouveautés ? Consultez nos [notes de publication](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes). Pour des informations plus détaillées sur la nouvelle conception de l’expérience d’installation, consultez nos billets de blog, « [Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/) » (Programme d’installation Visual Studio plus rapide et plus léger) et « [Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/) » (Anatomie d’une installation de Visual Studio à faible impact).  

Prêt pour l’installation ? Nous allons vous guider dans les étapes de l’installation.

## <a name="check-system-requirements"></a>Configuration système requise
Avant de commencer, vérifiez la [configuration requise](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs) pour vous assurer que votre ordinateur est prêt pour l’installation de Visual Studio 2017.

## <a name="download-visual-studio"></a>Télécharger Visual Studio
Pour démarrer, vous devez télécharger Visual Studio. Pour ce faire, cliquez sur le bouton suivant, sur **Enregistrer**, puis sur **Ouvrir le dossier**.

 > [!div class="button"]
 > [Télécharger Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="install-the-installer"></a>Installer le programme d’installation  
Quand vous téléchargez Visual Studio 2017, vous obtenez un fichier de programme d’amorçage qui installe à son tour notre nouveau programme d’installation allégé. Ce nouveau programme d’installation inclut tout ce dont vous avez besoin pour personnaliser votre installation.  

> [!IMPORTANT]
> Si vous avez installé une préversion de Visual Studio 2017 sur votre ordinateur, vous êtes invité à la supprimer avant d’installer Visual Studio 2017.

1.  Dans votre dossier **Téléchargements**, double-cliquez sur le fichier programme d’amorçage correspondant ou similaire à l’un des éléments suivants :

  * **vs_enterprise.exe** pour Visual Studio Enterprise
  * **vs_professional.exe** pour Visual Studio Professional
  * **vs_community.exe** pour Visual Studio Community  <br><br>

  Si vous recevez une notification du contrôle de compte d’utilisateur, cliquez sur **Oui**.  

2.  Vous devez accepter les [Termes du contrat de licence](https://www.visualstudio.com/license-terms/) Microsoft et la [Déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkID=824704) Microsoft. Cliquez sur **Continuer**.  

   ![Termes du contrat de licence et déclaration de confidentialité](~/docs/install/media/vs2017-privacy-and-license-terms.PNG "Termes du contrat de licence et déclaration de confidentialité Microsoft")  

Plusieurs écrans d’état montrant la progression de l’installation s’affichent. Une fois que le programme d’installation a terminé l’installation, vous pouvez choisir les ensembles de fonctionnalités (ou charges de travail) qui vous intéressent.

## <a name="install-workloads"></a>Installer les charges de travail  
 Vous pouvez personnaliser votre installation à l’aide de charges de travail. Sélectionnez une ou plusieurs charges de travail. Chaque charge de travail contient les fonctionnalités dont vous avez besoin pour la plateforme ou le langage de programmation de votre choix.  

 Voici comment les obtenir :  

1.  Recherchez la charge de travail que vous voulez dans l’écran **Installation de Visual Studio**.  

  ![Boîte de dialogue d’installation de Visual Studio 2017](~/docs/install/media/vs2017-workloads.PNG "Installer les charges de travail de Visual Studio")

     Par exemple, choisissez la charge de travail du développement .NET Desktop. Elle comprend l’éditeur principal par défaut, qui inclut une prise en charge de la modification du code de base pour plus de 20 langues, la possibilité d’ouvrir et de modifier le code dans n’importe quel dossier sans projet et un contrôle de code source intégré.  

2.  Après avoir sélectionné la ou les charges de travail que vous souhaitez, cliquez sur **Installer**.  

    Ensuite, des écrans d’état affichent la progression de votre installation de Visual Studio.

3.  Une fois les nouveaux composants et charges de travail installés, cliquez sur **Lancer**.

## <a name="install-individual-components"></a>Installer des composants individuels

Si vous ne voulez pas utiliser la fonctionnalité pratique Charges de travail pour personnaliser votre installation de Visual Studio, cliquez sur l’option **Composants individuels** dans le programme d’installation de Visual Studio, sélectionnez les composants que vous voulez, puis suivez les invites.

  ![Visual Studio 2017 - Installer des composants individuels](~/docs/install/media/vs2017-components.PNG "Installer des composants individuels de Visual Studio")

## <a name="install-language-packs"></a>Installer des modules linguistiques

Pour installer Visual Studio 2017 dans la langue de votre choix, cliquez sur l’option **Modules linguistiques** dans le programme d’installation de Visual Studio et suivez les invites.

  ![Visual Studio 2017 - Installer des modules linguistiques](~/docs/install/media/vs2017-languages.PNG "Installer des modules linguistiques de Visual Studio")

### <a name="change-the-installer-language"></a>Modifier la langue du programme d’installation

Par défaut, le programme d’installation essaie d’installer la langue du système d’exploitation quand vous l’exécutez pour la première fois. Le programme d’installation enregistre ce paramètre. Vous pouvez modifier ce paramètre en exécutant le programme d’installation à partir de la ligne de commande. Par exemple, vous pouvez forcer le programme d’installation à s’exécuter en anglais en utilisant la commande suivante : `vs_installer.exe --locale en-US`. Le programme d’installation enregistre ce paramètre pour une prochaine exécution. Le programme d’installation prend en charge les jetons de langue suivants : zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES et tr-TR.

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md) pour obtenir des conseils de dépannage.

## <a name="see-also"></a>Voir aussi  
* [Modifier Visual Studio 2017](modify-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Désinstaller Visual Studio 2017](uninstall-visual-studio.md)
* [Guide de l’administrateur Visual Studio 2017](visual-studio-administrator-guide.md)
* [Guide pratique pour signaler un problème avec Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

