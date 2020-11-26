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
ms.openlocfilehash: 8c89f1d59405fb7475e827cac9624c6623d7041e
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189093"
---
# <a name="frequently-asked-questions"></a>Forum aux questions

## <a name="visual-studio-support"></a>Visual Studio

**Question. RTVS fonctionne-t-il sur OS X ou Linux ?**

R. RTVS repose actuellement sur Visual Studio, qui est une implémentation Windows uniquement. Microsoft étudie la possibilité d’une prise en charge sur Visual Studio Code et Visual Studio pour Mac. Reportez-vous à [Problème #1295 de RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**Question. RTVS fonctionne-t-il avec les éditions Visual Studio Express ?**

R. Non.

**Question. Puis-je utiliser les extensions Visual Studio avec RTVS ?**

R. Absolument. Voici quelques exemples que les utilisateurs de R utilisent couramment.

- [VsVim pour les combinaisons de touches vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Éditeur Markdown avec aperçu instantané](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Pour en savoir plus, consultez [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**Question. Étant donné que RTVS est dans Visual Studio, cela signifie-t-il que R peut être facilement utilisé avec C#, C++ et d’autres langages Microsoft ?**

R. Non. RTVS est un outil de développement de code R qui utilise les interpréteurs R natifs standard. Aucune interopérabilité entre R et d’autres langages n’est prise en charge actuellement.

**Question. RTVS fonctionne-t-il avec des paramètres régionaux non anglais ?**

R. La version 1.0 de RTVS est en anglais uniquement. La version 1.1 sera localisée dans les mêmes langues que celles de Visual Studio. En attendant, utilisez le [module linguistique en anglais de Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) ou dans Visual Studio 2017, exécutez le programme d’installation et sélectionnez Anglais dans l’onglet **Modules linguistiques**.

![Paramètres internationaux de Visual Studio 2017](media/FAQ-international-settings.png)

**Question. J’aime vraiment mes paramètres Visual Studio actuels, mais je souhaite essayer les nouveaux paramètres de science des données. Que dois-je faire ?**

R. Enregistrez vos paramètres Visual Studio actuels à l’aide des **Outils**  >  **Importer et exporter des paramètres**, puis basculez vers les paramètres de science des données. Pour restaurer les paramètres enregistrés, utilisez à nouveau la commande **Importer et exporter les paramètres**.

**Question. Puis-je stocker mon projet Visual Studio sur un partage réseau ?**

R. Non, Visual Studio ne prend pas en charge le chargement des projets à partir d’un partage réseau.

## <a name="r-interpretersintegration"></a>Interpréteurs/intégration de R

**Question. Avec quels interpréteurs R RTVS fonctionne-t-il ?**

R. [CRAN R](https://cran.r-project.org/), [Microsoft R Client et Microsoft Machine Learning Server](/machine-learning-server/)

**Question. Où puis-je télécharger ces interpréteurs ?**

R. Consultez [Installation](installing-r-tools-for-visual-studio.md).

Q : **Qu’est-ce que Microsoft R Server ?**

R. R Server est l’ancien nom de [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Question. RTVS fonctionne-t-il avec les éditions 32 bits de R ?**

R. Non, RTVS prend uniquement en charge les éditions 64 bits de R exécutées sur les éditions 64 bits de Windows.

**Question. RTVS fonctionne-t-il avec mon système de contrôle de code source ?**

R. Oui, vous pouvez utiliser n’importe quel système de gestion de code source intégré à Visual Studio.

**Question. Quels sont les paramètres *. gitignore* recommandés pour un projet RTVS ?**

R. GitHub gère un référentiel de fichiers *. gitignore* recommandés. Vous le trouverez ici : [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

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

**Q. la fonctionnalité X est manquante, mais RStudio en a !**

R. RStudio est un IDE fantastique et abouti pour R qui est resté en phase de développement pendant de nombreuses années. Le but de RTVS est d’avoir toutes les fonctionnalités essentielles dont vous avez besoin pour réussir. Aidez à hiérarchiser le travail futur en établissant des problèmes sur [GitHub](https://github.com/Microsoft/RTVS/issues/).

**Question. Puis-je contribuer à RTVS ?**

R. Absolument ! Le code source se trouve sur [Github](https://github.com/microsoft/RTVS). Utilisez le suivi des problèmes pour envoyer des bogues et des commentaires sur ces fichiers.

Vous êtes également invité à contribuer à cette documentation&mdash; sélectionnez simplement la commande **Modifier** en haut à droite de chaque page. Vos commentaires sur la documentation sont également bienvenus. Vous pouvez en ajouter en bas de chaque page.
