---
title: FAQ des Outils R pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: 9fe92fb38d1b03b081cb53fc620f60180daf5b24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="frequently-asked-questions"></a>FAQ

## <a name="visual-studio-support"></a>Prise en charge par Visual Studio

**Q. RTVS fonctionne-t-il sur OS X ou Linux ?**

Un fichier . RTVS repose actuellement sur Visual Studio, qui est une implémentation Windows uniquement. Microsoft étudie la possibilité d’une prise en charge sur Visual Studio Code et Visual Studio pour Mac. Reportez-vous à [Problème #1295 de RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**Q. RTVS fonctionne-t-il avec les éditions Visual Studio Express ?**

Un fichier . Non.

**Q. Puis-je utiliser des extensions Visual Studio avec RTVS ?**

Un fichier . Absolument. Voici quelques exemples que les utilisateurs de R utilisent couramment.

- [VsVim pour les combinaisons de touches vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Éditeur Markdown avec aperçu instantané](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Pour en savoir plus, consultez [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**Q. Étant donné que RTVS se trouve dans Visual Studio, R peut-il être facilement utilisé avec C#, C++ et d’autres langages Microsoft ?**

Un fichier . Non. RTVS est un outil de développement de code R qui utilise les interpréteurs R natifs standard. Aucune interopérabilité entre R et d’autres langages n’est prise en charge actuellement.

**Q. RTVS fonctionne-t-il avec des paramètres régionaux non anglais ?**

Un fichier . La version 1.0 de RTVS est en anglais uniquement. La version 1.1 sera localisée dans les mêmes langues que celles de Visual Studio. En attendant, utilisez le [module linguistique en anglais de Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) ou dans Visual Studio 2017, exécutez le programme d’installation et sélectionnez Anglais dans l’onglet **Modules linguistiques**.

![Paramètres internationaux de Visual Studio 2017](media/FAQ-international-settings.png)

**Q. J’aime vraiment mes paramètres Visual Studio actuels, mais je veux tester les nouveaux paramètres de science des données. Que dois-je faire ?**

Un fichier . Enregistrez vos paramètres Visual Studio actuels en accédant à **Outils > Importer et exporter les paramètres...**, puis remplacez-les par les paramètres de science des données. Pour restaurer les paramètres enregistrés, utilisez à nouveau la commande **Importer et exporter les paramètres...**.

**Q. Puis-je stocker mon projet Visual Studio sur un partage réseau ?**

Un fichier . Non, Visual Studio ne prend pas en charge le chargement des projets à partir d’un partage réseau.

## <a name="r-interpretersintegration"></a>Interpréteurs/intégration de R

**Q. Avec quels interpréteurs R fonctionne RTVS ?**

Un fichier . [CRAN R](https://cran.r-project.org/), [Microsoft R Client et Microsoft Machine Learning Server](/machine-learning-server/)

**Q. Où puis-je télécharger ces interpréteurs ?**

Un fichier . Consultez [Installation](installation.md).

Q : **Qu’est-ce que Microsoft R Server ?**

Un fichier . R Server est l’ancien nom de [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Q. RTVS fonctionne-t-il avec les éditions 32 bits de R ?**

Un fichier . Non, RTVS prend uniquement en charge les éditions 64 bits de R exécutées sur les éditions 64 bits de Windows.

**Q. RTVS fonctionne-t-il avec mon système de gestion de code source ?**

Un fichier . Oui, vous pouvez utiliser n’importe quel système de gestion de code source intégré à Visual Studio.

**Q. Quels sont les paramètres `.gitignore` recommandés pour un projet RTVS ?**

Un fichier . Github conserve un dépôt principal des fichiers `.gitignore` recommandés. Vous le trouverez ici : [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Remote Services

Q. **Qu’est-ce que Remote Services dans Visual Studio ?**

Un fichier . Remote R Services pour Visual Studio vous permet de configurer une machine Windows ou Linux, puis de vous y connecter depuis RTVS. Consultez [Configuration des espaces de travail distants](workspaces-remote-setup.md).

Q. **RTVS peut-il se connecter à Microsoft R Server ?**

Un fichier . Non, car Microsoft R Server est une technologie différente et ne fournit pas le même mécanisme de connectivité nécessité par RTVS.

Q. **RTVS peut-il se connecter à une machine virtuelle créée avec l’image de machine virtuelle Science des données sur Azure ?**

Un fichier . Oui. L’image de [machine virtuelle Science des données - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) est livrée préinstallée avec Remote R Services pour Visual Studio.

Q : **RTVS peut-il se connecter à une machine distante où R est installé ?**

Pour exécuter le code R sur une machine distante, il doit exister un service qui écoute les demandes, reçoit le code et renvoie les résultats à la machine cliente. C’est ce que fait Remote R Services pour Visual Studio. Consultez [Configuration des espaces de travail distants](workspaces-remote-setup.md).

Q. **Qu’est ce qu’une session à distance ?**

Un fichier . Consultez l’article [Exécuter sur un serveur distant](/machine-learning-server/r/how-to-execute-code-remotely) dans la documentation de Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Développement et fonctionnalités de RTVS

**Q. La fonctionnalité X n’existe pas ? Si, dans RStudio !**

Un fichier . RStudio est un IDE fantastique et abouti pour R qui est resté en phase de développement pendant de nombreuses années. Le but de RTVS est d’avoir toutes les fonctionnalités essentielles dont vous avez besoin pour réussir. Aidez-nous à définir les priorités de nos prochains travaux en répondant à l’[enquête RTVS](https://www.surveymonkey.com/r/RTVS1) et décrivez les problèmes sur [GitHub](https://github.com/Microsoft/RTVS/issues/).

**Q. Puis-je contribuer à RTVS ?**

Un fichier . Absolument ! Le code source se trouve sur [Github](https://github.com/microsoft/RTVS). Utilisez le suivi des problèmes pour envoyer des bogues et des commentaires sur ces fichiers.

Vous êtes également invité à contribuer à cette documentation&mdash; sélectionnez simplement la commande **Modifier** en haut à droite de chaque page. Vos commentaires sur la documentation sont également bienvenus. Vous pouvez en ajouter en bas de chaque page.
