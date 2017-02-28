---
title: "Installer Visual Studio 2017 RC │ Microsoft Docs"
description: "Découvrez comment installer Visual Studio, étape par étape."
ms.custom: 
ms.date: 11/18/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio Preview
- install Visual Studio
- installing Visual Studio
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
translationtype: Human Translation
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 997a1e0966c5e08314c616dba76842120ab50d63
ms.lasthandoff: 02/22/2017

---
# <a name="install-visual-studio-2017-rc"></a>Installer Visual Studio 2017 RC
Découvrez une nouvelle façon d’installer Visual Studio ! Dans notre dernière version, nous avons simplifié la sélection et l’installation des fonctionnalités dont vous avez besoin, et nous avons réduit l’empreinte minimale de Visual Studio pour qu’il s’installe plus rapidement et avec moins d’impact système qu’auparavant.  

 Vous voulez en savoir plus sur les autres nouveautés de la version RC ? Consultez nos [notes de publication](https://www.visualstudio.com/news/releasenotes/vs15-relnotes). Pour des informations plus détaillées sur la nouvelle conception de l’expérience d’installation, consultez nos billets de blog, « [Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/) » (Programme d’installation Visual Studio plus rapide et plus léger) et « [Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/) » (Anatomie d’une installation de Visual Studio à faible impact).  

 Prêt pour l’installation ? Nous allons vous guider dans les étapes de l’installation. Allons-y.  

## <a name="install-the-installer"></a>Installer le programme d’installation  
 Quand vous téléchargez Visual Studio 2017 RC, vous obtenez un fichier de programme d’amorçage qui installe à son tour notre nouveau programme d’installation allégé. Ce nouveau programme d’installation inclut tout ce dont vous avez besoin pour personnaliser votre installation.  

> [!IMPORTANT]
> Si vous avez installé une préversion de Visual Studio 2017 sur votre ordinateur, vous êtes invité à la supprimer avant d’installer Visual Studio 2017 RC.

1.  [Téléchargez Visual Studio Enterprise 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) et cliquez sur **Enregistrer**.  Ensuite, dans votre dossier **Téléchargements**, exécutez le fichier `vs_Enterprise.exe`.  

     Si vous recevez une notification du contrôle de compte d’utilisateur, cliquez sur **Oui**.  

2.  Vous devez accepter les [Termes du contrat de licence](https://www.visualstudio.com/support/legal/mt591984) Microsoft et la [Déclaration de confidentialité](https://www.visualstudio.com/dn948229) Microsoft. Cliquez sur **Installer** pour continuer.  

  ![Termes du contrat de licence et déclaration de confidentialité](media/01-installingdev15prev4-licensetermsandprivacystatement.png "Termes du contrat de licence et déclaration de confidentialité Microsoft")  

3.  Plusieurs écrans d’état montrant la progression de l’installation s’affichent. Une fois que le programme d’installation a terminé l’installation, vous pouvez choisir les ensembles de fonctionnalités (ou charges de travail) qui vous intéressent.

## <a name="install-workloads"></a>Installer les charges de travail  
 À présent, vous pouvez personnaliser votre installation à l’aide des charges de travail. Sélectionnez une ou plusieurs charges de travail. Chaque charge de travail contient les fonctionnalités dont vous avez besoin pour la plateforme ou le langage de programmation de votre choix.  

 Voici comment les obtenir.  

1.  Recherchez la charge de travail que vous voulez dans l’écran **Installation de Visual Studio**.  

  ![Boîte de dialogue d’installation de Visual Studio 2017 RC](../ide/media/willow1.png "Installation de Visual Studio 2017")

     Par exemple, choisissez la charge de travail du développement .NET Desktop. Elle comprend l’éditeur principal par défaut, qui inclut une prise en charge de la modification du code de base pour plus de 20 langues, la possibilité d’ouvrir et de modifier le code dans n’importe quel dossier sans projet et un contrôle de code source intégré.  

2.  Après avoir sélectionné la ou les charges de travail que vous souhaitez, cliquez sur **Installer**.  

    Ensuite, des écrans d’état affichent la progression de votre installation de Visual Studio.

3.  Une fois les nouveaux composants et charges de travail installés, cliquez sur **Lancer**.

## <a name="install-individual-components"></a>Installer des composants individuels

Si vous ne voulez pas utiliser la fonctionnalité pratique Charges de travail pour personnaliser votre installation de Visual Studio, cliquez sur l’option **Composants individuels** dans le programme d’installation de Visual Studio, sélectionnez les composants que vous voulez, puis suivez les invites.

  ![Visual Studio 2017 - Installer des composants individuels](media/vs2017install-IndividualComponents.PNG "Installer des composants individuels de Visual Studio")

## <a name="install-language-packs"></a>Installer des modules linguistiques

Pour installer Visual Studio 2017 RC dans la langue de votre choix, cliquez sur l’option **Modules linguistiques** dans le programme d’installation de Visual Studio et suivez les invites.

  ![Visual Studio 2017 - Installer des modules linguistiques](media/vs2017install-LanguagePacks.PNG "Installer des modules linguistiques de Visual Studio")

### <a name="change-the-installer-language"></a>Modifier la langue du programme d’installation

Par défaut, le programme d’installation essaie d’installer la langue du système d’exploitation quand vous l’exécutez pour la première fois. Le programme d’installation enregistre ce paramètre. Vous pouvez modifier ce paramètre en exécutant le programme d’installation à partir de la ligne de commande. Par exemple, vous pouvez forcer le programme d’installation à s’exécuter en anglais en exécutant `vs_installer.exe --locale en-US`. Ce paramètre est mémorisé pour la prochaine exécution du programme d’installation. Le programme d’installation prend en charge les jetons de langue suivants : zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES et tr-TR.


  > [!IMPORTANT]
  > Alors que Visual Studio 2017 RC est généralement pris en charge pour une utilisation dans un environnement de production, les charges de travail et les composants qui sont marqués « Préversion » dans l’interface utilisateur de l’installation ne le sont pas.

## <a name="see-also"></a>Voir aussi  
* [Modifier Visual Studio 2017 RC](modify-visual-studio.md)
* [Désinstaller Visual Studio 2017 RC](uninstall-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Guide pratique pour signaler un problème avec Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

