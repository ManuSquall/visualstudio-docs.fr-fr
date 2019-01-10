---
title: 'Bien démarrer avec PTVS : Configuration de Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec491c1d-bdb2-4c2b-a390-bd808cec635a
caps.latest.revision: 6
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 6ce34fb08edbad3c01594bfab770dffce1b82922
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852743"
---
# <a name="getting-started-with-ptvs-setting-up-visual-studio"></a>Bien démarrer avec PTVS : Configuration de Visual Studio

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous avez Visual Studio, l'installation de PTVS et des bibliothèques associées est une opération rapide. Si vous ne disposez pas de Visual Studio, vous pouvez obtenir une copie gratuite d'une version de qualité professionnelle.

Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

Les étapes de haut niveau sont les suivantes : installer Visual Studio, installer PTVS, installer les bibliothèques Python et des données (Anaconda, Canopy), puis enfin à vérifier l’installation.

La première chose que vous avez besoin est Visual Studio. Si vous êtes un développeur open source ou individuel, vous pouvez utiliser Visual Studio [Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs), qui est gratuite et fonctionnelle pour les professionnels de le. L’utilisation de la version Community Edition dans une organisation est limitée à la formation en salle de classe, aux travaux de recherche académique et aux contributions à des projets open source. Si vous êtes étudiant ou propriétaire d'une jeune entreprise, examinez les programmes DreamSpark et BizSpark pour voir si vous pouvez bénéficier d'un accès gratuit, ou demandez à votre employeur si vous disposez d'un abonnement MSDN.

Une fois que vous avez Visual Studio, vous devez [installer PTVS](http://pytools.codeplex.com/wikipage?title=PTVS%20Installation). Autonome et gratuite, cette extension est entièrement prise en charge par Microsoft et développée de manière ouverte grâce aux contributions de la communauté.

Vous devez maintenant [installer Python](https://www.python.org/download/). Python est géré par la Communauté, et sa page d’accueil est python.org. Continuum Analytique produit une offre groupée gratuite, appelée Anaconda qui intègre Python et nombreuses bibliothèques utiles (en particulier pour la science et traitement des données) et Enthought produit une offre groupée similaire, nommée Canopy. Vous devez uniquement installer l’une de ces produits. Si vous ne savez pas laquelle choisir, commencez par [Anaconda](https://www.continuum.io/downloads). Celle-ci contient la version la plus récente de Python et la plupart des packages difficiles à installer.

Démarrez Visual Studio et assurez-vous que tout fonctionne correctement. Dans le menu Affichage, sélectionnez Autres fenêtres. La liste contient un élément nommé Environnements Python. Cette fenêtre affiche toutes les installations de Python détectées par PTVS et tous les packages installés. La fenêtre contrôle également l'actualisation des bases de données pour afficher la saisie semi-automatique lorsque vous modifiez du code. Ce processus d’actualisation prend un certain temps, mais une fois terminé, PTVS peut afficher plus d’informations sur les packages.

Si vous voulez utiliser IPython avec PTVS, suivez ces [instructions](http://pytools.codeplex.com/wikipage?title=Using%20IPython%20with%20PTVS).

Vous pouvez regarder ces instructions dans un court [vidéo youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

## <a name="see-also"></a>Voir aussi

[Vidéos sur le démarrage et l’exploration de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
