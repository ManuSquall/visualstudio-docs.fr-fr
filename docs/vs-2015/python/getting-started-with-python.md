---
title: Bien démarrer avec Python | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 08e059955a6552323453e08882bc2bcebd0fc586
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "47591008"
---
# <a name="getting-started-with-python"></a>Mise en route de Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Python dans Visual Studio](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio).  
  
Python Tools pour Visual Studio (PTVS), est un texte libre, [open source](https://github.com/Microsoft/ptvs) plug-in pour Visual Studio rencontrer un puissant environnement de développement Python.  
  
## <a name="python-the-language"></a>Le langage Python
  
Python est un langage de programmation populaire qui est utilisé par nombreuses universités, scientifiques, auteurs de scripts d’application, les développeurs occasionnels et les développeurs professionnels, travaillant sur des applications, des sites web et des services de cloud.

Comme un langage de programmation Python est :
  
- Fiable.
- Généralement utile pour les scripts de programmes rapides, scripts d’application, applications de bureau, serveurs web, services web et calcul scientifique.
- Facile à apprendre et bénéficie d’une conception qui favorise le codage (nombreuses universités l’utiliser pour les cours de programmation introduction).
- Flexible, prenant en charge les styles de programmation impératives, fonctionnelles et orientée objet.
- Gratuit et open source.
- S’exécute correctement sur tous les principaux systèmes d’exploitation.  
- Prise en charge par de nombreuses bibliothèques bien conçues, utiles et gratuits.  
- Prise en charge par un grand nombre de documentation, des exemples et une solide Communauté de développeurs.  

Pour en savoir plus sur le langage, commencez avec [Python for Beginners](https://www.python.org/about/gettingstarted/) sur python.org.

Pour installer Python lui-même, visitez [ https://www.python.org/download/ ](https://www.python.org/download/).
 
  
## <a name="python-tools-for-visual-studio"></a>Outils Python pour Visual Studio
  
Python Tools pour Visual Studio, que vous pouvez installer à partir de [visualstudio.com](https://www.visualstudio.com/en-us/explore/python-vs), fournissent les fonctionnalités suivantes :  
  
- Prise en charge de divers interpréteurs : CPython, IronPython et IPython dans plusieurs versions.  
- Un système de projet qui récupère implicitement une structure de dossiers de code Python et permet également un contrôle explicite afin d’identifier le code d’application, code de test, pages web, JavaScript, scripts de compilation et ainsi de suite.  
- Modèles de projet de type console, web, Azure, science des données et autres.    
- Le SDK Azure pour Python (voir ci-dessous)    
- Fonctionnalités d’édition et de compréhension de code élaborées, dont la coloration syntaxique, la saisie semi-automatique dans l’ensemble du code et des bibliothèques, une aide sur les signatures, un affichage de classes, les fonctions Atteindre la définition et Rechercher toutes les références, la refactorisation, etc.    
- Fenêtre interactive (REPL).
- IPython avec visualisations de données.
- Prise en charge d’IronPython et de .NET/WPF.    
- Débogage élaboré sans projet Visual Studio, possibilité d’effectuer un débogage d’exécutables existants en mode mixte, un débogage à distance pour Windows/Linux/Mac et un débogage dans la fenêtre interactive.   
- Outils de profilage.  
- Outils de test.  
  
Les ressources suivantes vous permettront de démarrer :

- [Guide d’installation](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Petites vidéos de démarrage et d’exploration](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Installation et démonstration des fonctionnalités (27 min)])https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Documentation](https://github.com/Microsoft/PTVS/wiki)  


Notez que Visual Studio ne pas à l’heure actuelle fournit les moyens de créer un exécutable autonome à l’aide de Python, ce qui signifie essentiellement un programme avec un interpréteur Python incorporé. Toutefois, la communauté Python décrit différents moyens de le faire sur [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython prend également en charge l’incorporation dans une application native, comme décrit dans le billet de blog, [Using CPython’s Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) (Utilisation d’un fichier zip incorporable dans CPython).
  
## <a name="building-ui-with-python"></a>Création de l’interface utilisateur avec Python  

L’offre principale pour la création d’une interface utilisateur avec Python est la [Qt Project](https://www.qt.io/qt-for-application-development/), avec des liaisons pour Python appelées [PySide (la liaison officielle)](http://wiki.qt.io/PySide) (voir également [téléchargements PySide](https://download.qt.io/official_releases/pyside/.)) et [PyQt](https://wiki.python.org/moin/PyQt). Pour l’instant, la prise en charge de Python dans Visual Studio n’inclut pas d’outils spécifiques pour le développement d’interface utilisateur.

## <a name="azure-sdk-for-python"></a>Kit de développement logiciel (SDK) Azure pour Python
  
Le Kit SDK Azure pour Python, qui prend en charge Windows, Mac et Linux, facilite l’utilisation et la gestion des services Microsoft Azure. Pour plus d’informations, reportez-vous aux ressources suivantes : 

- Pour installer le kit SDK, utilisez l’[index de packages Python](https://pypi.python.org/pypi/azure) ou suivez les instructions de la rubrique [Installation de Python et du Kit de développement logiciel (SDK)](https://azure.microsoft.com/documentation/articles/python-how-to-install/) dans la documentation Azure. 
- Le [Centre de développement Kit de développement logiciel (SDK) Azure pour Python](https://azure.microsoft.com/develop/python/) propose une aide complète, de l’installation jusqu’à la documentation avec didacticiels.  Voici quelques points clés :  
- Guides pratiques :
  - [Objet blob de stockage](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [File d’attente de stockage](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Table de stockage](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Files d’attente Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Rubriques/abonnements Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Gestion des services](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

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

