---
title: Questions fréquentes (FAQ) des Outils R pour Visual Studio
description: Forum Aux Questions (FAQ) sur R dans Visual Studio.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 4eef8e79023bdd3bde03fec33c16a1c8f6d90446
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72306264"
---
# <a name="frequently-asked-questions"></a>Forum aux questions

## <a name="visual-studio-support"></a>Visual Studio

**Q. RTVS fonctionne-t-il sur OS X ou Linux ?**

R. RTVS repose actuellement sur Visual Studio, qui est une implémentation Windows uniquement. Microsoft étudie la possibilité d’une prise en charge sur Visual Studio Code et Visual Studio pour Mac. Reportez-vous à [Problème #1295 de RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**Q. RTVS fonctionne-t-il avec les éditions Visual Studio Express ?**

R. Non.

**Q. Puis-je utiliser des extensions Visual Studio avec RTVS ?**

R. Absolument. Voici quelques exemples que les utilisateurs de R utilisent couramment.

- [VsVim pour les combinaisons de touches vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Éditeur Markdown avec aperçu instantané](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Pour en savoir plus, consultez [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**Q. Étant donné que RTVS est dans Visual Studio, cela signifie-t-il que R peut être facilement utilisé avec C, C et autres langues Microsoft?**

R. Non. RTVS est un outil de développement de code R qui utilise les interpréteurs R natifs standard. Aucune interopérabilité entre R et d’autres langages n’est prise en charge actuellement.

**Q. RTVS fonctionne-t-il avec un local non-anglais?**

R. La version 1.0 de RTVS est en anglais uniquement. La version 1.1 sera localisée dans les mêmes langues que celles de Visual Studio. En attendant, utilisez le [module linguistique en anglais de Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) ou dans Visual Studio 2017, exécutez le programme d’installation et sélectionnez Anglais dans l’onglet **Modules linguistiques**.

![Paramètres internationaux de Visual Studio 2017](media/FAQ-international-settings.png)

**Q. J’aime beaucoup mes paramètres actuels de Visual Studio, mais je veux essayer les nouveaux paramètres data Science. Qu’est-ce que je dois faire ?**

R. Enregistrez vos paramètres visualis actuels en utilisant les paramètres**d’importation et d’exportation d’outils,** **Tools** > puis passez aux paramètres data Science. Pour restaurer les paramètres enregistrés, utilisez à nouveau la commande **Importer et exporter les paramètres**.

**Q. Puis-je stocker mon projet Visual Studio sur une part de réseau?**

R. Non, Visual Studio ne prend pas en charge le chargement des projets à partir d’un partage réseau.

## <a name="r-interpretersintegration"></a>Interpréteurs/intégration de R

**Q. Avec quels interprètes R RTVS travaille-t-il?**

R. [CRAN R](https://cran.r-project.org/), [Microsoft R Client et Microsoft Machine Learning Server](/machine-learning-server/)

**Q. Où puis-je télécharger ces interprètes?**

R. Consultez [Installation](installing-r-tools-for-visual-studio.md).

Q : **Qu’est-ce que Microsoft R Server ?**

R. R Server est l’ancien nom de [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Q. RTVS fonctionne-t-il avec des éditions 32 bits de R?**

R. Non, RTVS prend uniquement en charge les éditions 64 bits de R exécutées sur les éditions 64 bits de Windows.

**Q. Le RTVS fonctionne-t-il avec mon système de contrôle des sources?**

R. Oui, vous pouvez utiliser n’importe quel système de gestion de code source intégré à Visual Studio.

**Q. Quels sont les paramètres *recommandés .gitignore* pour un projet RTVS?**

R. GitHub conserve un dépôt principal des fichiers *.gitignore* recommandés. Vous le trouverez ici : [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Remote Services

Q. **Qu’est-ce que Remote Services dans Visual Studio ?**

R. Remote R Services pour Visual Studio vous permet de configurer une machine Windows ou Linux, puis de vous y connecter depuis RTVS. Consultez [Configurer des espaces de travail distants](setting-up-remote-r-workspaces.md).

Q. **RTVS peut-il se connecter à Microsoft Machine Learning Server ?**

R. Non, car Microsoft ML Server est une technologie différente et ne fournit pas le même mécanisme de connectivité nécessité par RTVS.

Q. **RTVS peut-il se connecter à une machine virtuelle créée avec l’image de machine virtuelle Science des données sur Azure ?**

R. Oui. L’image de [machine virtuelle Science des données - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) est livrée préinstallée avec Remote R Services pour Visual Studio.

Q : **RTVS peut-il se connecter à une machine distante où R est installé ?**

Pour exécuter le code R sur une machine distante, il doit exister un service qui écoute les demandes, reçoit le code et renvoie les résultats à la machine cliente. C’est ce que fait Remote R Services pour Visual Studio. Consultez [Configurer des espaces de travail distants](setting-up-remote-r-workspaces.md).

Q. **Qu’est ce qu’une session à distance ?**

R. Consultez l’article [Exécuter sur un serveur distant](/machine-learning-server/r/how-to-execute-code-remotely) dans la documentation de Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Développement et fonctionnalités de RTVS

**Q. Feature X est manquant, mais RStudio l’a!**

R. RStudio est un IDE fantastique et abouti pour R qui est resté en phase de développement pendant de nombreuses années. Le but de RTVS est d’avoir toutes les fonctionnalités essentielles dont vous avez besoin pour réussir. Aider à prioriser les travaux futurs en déposant des questions sur [GitHub](https://github.com/Microsoft/RTVS/issues/).

**Q. Puis-je contribuer à RTVS?**

R. Absolument ! Le code source se trouve sur [Github](https://github.com/microsoft/RTVS). Utilisez le suivi des problèmes pour envoyer des bogues et des commentaires sur ces fichiers.

Vous êtes également invité à contribuer à cette documentation&mdash; sélectionnez simplement la commande **Modifier** en haut à droite de chaque page. Vos commentaires sur la documentation sont également bienvenus. Vous pouvez en ajouter en bas de chaque page.
