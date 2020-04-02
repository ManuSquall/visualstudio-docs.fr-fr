---
title: Démarrer avec Python (fr) Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543972"
---
# <a name="getting-started-with-python"></a>Mise en route de Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le Python Tools for Visual Studio (PTVS), est un [plug-in open-source](https://github.com/Microsoft/ptvs) gratuit pour Visual Studio qu’une puissante expérience de développement Python.  
  
## <a name="python-the-language"></a>Le langage Python
  
Python est un langage de programmation populaire qui est utilisé par de nombreuses universités, scientifiques, scripteurs d’applications, développeurs occasionnels et développeurs professionnels, travaillant sur des applications, des sites Web et des services cloud.

En tant que langage de programmation, Python est :
  
- Fiable.
- Généralement utile pour scripter des programmes rapides, script d’applications, applications de bureau, serveurs Web, services Web et informatique scientifique.
- Facile à maîtriser, il bénéficie d’une conception qui favorise le codage (de nombreuses universités l’utilisent pour les cours d’initiation à la programmation).
- Styles de programmation flexibles, supporteurs, fonctionnels et orientés objet.
- Gratuit et open source.
- Fonctionne bien sur tous les principaux systèmes d’exploitation.  
- Soutenu par de nombreuses bibliothèques gratuites, utiles et bien conçues.  
- Soutenu par beaucoup de documentation, des échantillons, et une communauté de développeurs forte.  

Pour en savoir plus sur la langue, commencez par [Python pour débutants](https://www.python.org/about/gettingstarted/) sur python.org.

Pour installer Python [https://www.python.org/download/](https://www.python.org/download/)lui-même, visitez .

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Les outils Python pour Studio Visuel, que vous pouvez installer à partir de [visualstudio.com](https://www.visualstudio.com/explore/python-vs), fournissent les caractéristiques suivantes:  
  
- Prise en charge de divers interpréteurs : CPython, IronPython et IPython dans plusieurs versions.  
- Système de projet qui récupère implicitement une structure de dossiers de code Python et qui autorise par ailleurs un contrôle explicite permettant d’identifier le code d’application, le code de test, les pages web, JavaScript, les scripts de build, etc.  
- Modèles de projet de type console, web, Azure, science des données et autres.    
- L’Azure SDK pour Python (voir ci-dessous)    
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
- Installation et démo (27 min)) (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Documentation](https://github.com/Microsoft/PTVS/wiki)  

Notez que Visual Studio ne fournit pas actuellement les moyens de créer un exécutable autonome à l’aide de Python, ce qui signifie essentiellement un programme avec un interprète Python intégré. Toutefois, la communauté Python décrit différents moyens de le faire sur [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython prend également en charge l’incorporation dans une application native, comme décrit dans le billet de blog, [Using CPython’s Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Utilisation d’un fichier zip incorporable dans CPython).
  
## <a name="building-ui-with-python"></a>Construire l’interface utilisateur avec Python  

L’offre principale pour la construction d’une interface utilisateur avec Python est le [projet Qt](https://www.qt.io/qt-for-application-development/), avec des fixations pour Python connu sous le nom [PySide (la liaison officielle)](https://wiki.qt.io/PySide) (voir également [téléchargements PySide](https://download.qt.io/official_releases/pyside/.)) et [PyQt](https://wiki.python.org/moin/PyQt). Pour l’instant, la prise en charge de Python dans Visual Studio n’inclut pas d’outils spécifiques pour le développement d’interface utilisateur.

## <a name="azure-sdk-for-python"></a>Kit SDK Azure pour Python
  
Le Kit SDK Azure pour Python, qui prend en charge Windows, Mac et Linux, facilite l’utilisation et la gestion des services Microsoft Azure. Pour plus d’informations, reportez-vous aux ressources suivantes : 

- Pour installer le kit SDK, utilisez l’[index de packages Python](https://pypi.python.org/pypi/azure) ou suivez les instructions de la rubrique [Installation de Python et du Kit de développement logiciel (SDK)](/azure/developer/python/azure-sdk-install) dans la documentation Azure. 
- Le [Centre de développement Kit de développement logiciel (SDK) Azure pour Python](https://azure.microsoft.com/develop/python/) propose une aide complète, de l’installation jusqu’à la documentation avec didacticiels.  Voici quelques points clés :  
- Guides pratiques :
  - [Stockage Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [File d’attente de stockage](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Table de stockage](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Files d’attente d’autobus de service](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Sujets/Abonnements d’autobus de service](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Gestion des services](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Calcul scientifique

En plus de toutes les bibliothèques à destination des scientifiques de données Python, Python Tools pour Visual Studio prend en charge IPython et les bloc-notes IPython, qui peuvent être hébergés dans Azure.

Nous vous recommandons de vous procurer IPython et les bibliothèques de calcul scientifique (matplotlib, scipy, numpy, etc.) auprès de l’[Université de Californie, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Voir aussi  

[Démarrer avec PTVS: Mise en place de studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
visuel[Getting Started avec PTVS: Start Coding (Projets)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Getting Started with PTVS: Editing Code](../python/getting-started-with-ptvs-editing-code.md)
[Getting Started with PTVS: Debugging](../python/getting-started-with-ptvs-debugging.md)
[Getting Started with PTVS: Interactive Python](../python/getting-started-with-ptvs-interactive-python.md)
[Getting Started with PTVS: Building a Website in Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
