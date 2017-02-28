---
title: "Bien démarrer avec Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 1/3/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d0b0b0b12b9d65f26b67d6f797abc0cf7a0c2c9
ms.openlocfilehash: e7cc978dabb401a8e9bab6791988aa737edb76b0
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-python-in-visual-studio"></a>Bien démarrer avec Python dans Visual Studio

Python ([http://python.org/download/](http://python.org/download/)) est un langage de programmation très apprécié parce qu’il est fiable, souple, facile à apprendre et gratuit. Il est soutenu par une solide communauté de développeurs et offre de nombreuses bibliothèques gratuites. Python fonctionne sur tous les principaux systèmes d’exploitation et répond à de nombreux besoins : applications web, services web, applications de bureau, création de scripts, calcul scientifique, etc. Il est de ce fait utilisé par un grand nombre d’universités, de scientifiques et de développeurs aussi bien occasionnels que professionnels.

Pour en savoir plus sur le langage, commencez par consulter la page [Python for Beginners](https://www.python.org/about/gettingstarted/) (python.org).

## <a name="python-tools-for-visual-studio"></a>Outils Python pour Visual Studio

Python Tools pour Visual Studio (PTVS) est une extension open source gratuite pour Visual Studio qui propose une expérience de développement Python performante, avec un système et des modèles de projet, des fonctionnalités d’édition élaborées, IntelliSense, un débogage complet, ainsi que divers autres outils.

L’extension offre les fonctionnalités suivantes :

- Prise en charge de divers interpréteurs : CPython, IronPython et IPython dans plusieurs versions.
- Système de projet qui récupère implicitement une structure de dossiers de code Python et qui autorise par ailleurs un contrôle explicite permettant d’identifier le code d’application, le code de test, les pages web, JavaScript, les scripts de build, etc.
- Modèles de projet de type console, web, Azure, science des données et autres.
- Fonctionnalités d’édition et de compréhension de code élaborées, dont la coloration syntaxique, la saisie semi-automatique dans l’ensemble du code et des bibliothèques, une aide sur les signatures, un affichage de classes, les fonctions Atteindre la définition et Rechercher toutes les références, la refactorisation, etc.
- Fenêtre interactive (REPL).
- Débogage élaboré sans projet Visual Studio, possibilité d’effectuer un débogage d’exécutables existants en mode mixte, un débogage à distance pour Windows/Linux/Mac et un débogage dans la fenêtre interactive.

- IPython avec visualisations de données.
- Prise en charge d’IronPython et de .NET/WPF.
- Outils de profilage.
- Outils de test.
- [Kit SDK Azure pour Python](#azure-sdk-for-python)

Les ressources suivantes vous permettront de démarrer :

- [Installer Python Tools pour Visual Studio](https://www.visualstudio.com/vs/python/).
- [Guide d’installation](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)
- [Petites vidéos de démarrage et d’exploration](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
- Démonstration de l’installation et des fonctionnalités (27 min)](https://www.youtube.com/watch?v=JNNAOypc6Ek)
- [Documentation](https://github.com/Microsoft/PTVS/wiki)
- [Code source](https://github.com/Microsoft/ptvs)


## <a name="azure-sdk-for-python"></a>Kit SDK Azure pour Python

Le Kit SDK Azure pour Python, qui prend en charge Windows, Mac et Linux, facilite l’utilisation et la gestion des services Microsoft Azure. Pour plus d’informations, reportez-vous aux ressources suivantes :

- Pour installer le kit SDK, utilisez l’[index de packages Python](https://pypi.python.org/pypi/azure) ou suivez les instructions de la rubrique [Installation de Python et du Kit de développement logiciel (SDK)](https://azure.microsoft.com/documentation/articles/python-how-to-install/) dans la documentation Azure.
- Le [Centre de développement Kit de développement logiciel (SDK) Azure pour Python](http://azure.microsoft.com/en-us/develop/python/) propose une aide complète, de l’installation jusqu’à la documentation avec didacticiels.  Voici quelques points clés :
- Guides pratiques :
  - [Objet blob de stockage](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)
  - [File d’attente de stockage](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)
  - [Table de stockage](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)
  - [Files d’attente de Service Bus](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)   - [Rubriques/abonnements Service Bus](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)
  - [Gestion des services](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)
- Le [dépôt GitHub du kit SDK](https://github.com/Azure/azure-sdk-for-python) propose des [tests unitaires](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests) qui constituent également une bonne source d’information sur les API.


## <a name="scientific-computing"></a>Calcul scientifique
En plus de toutes les bibliothèques à destination des scientifiques de données Python, Python Tools pour Visual Studio prend en charge IPython et les bloc-notes IPython, qui peuvent être hébergés dans Azure.

Nous vous recommandons de vous procurer IPython et les bibliothèques de calcul scientifique (matplotlib, scipy, numpy, etc.) auprès de l’[Université de Californie, Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).

## <a name="see-also"></a>Voir aussi
 [Bien démarrer avec PTVS : configuration de Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
 [Bien démarrer avec PTVS : commencer à développer (projets)](../python/getting-started-with-ptvs-start-coding-projects.md)
 [Bien démarrer avec PTVS : modification de code](../python/getting-started-with-ptvs-editing-code.md)
 [Bien démarrer avec PTVS : débogage](../python/getting-started-with-ptvs-debugging.md)
 [Bien démarrer avec PTVS : Interactive Python](../python/getting-started-with-ptvs-interactive-python.md)
 [Bien démarrer avec PTVS : création d’un site web dans Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
