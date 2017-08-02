---
title: Mesure des performances de code Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
caps.latest.revision: 1
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 8d52ad780eb8aa29132626644d581d3a5b6e66b4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---

# <a name="profiling-python-code"></a>Profilage de code Python

Visual Studio prend en charge le profilage d’une application Python lorsque des interpréteurs CPython sont utilisés.

La commande de menu **Analyser > Launch Python Profiling** (Lancer le profilage Python) permet de lancer le profilage et ouvre une boîte de dialogue de configuration :

![Boîte de dialogue de configuration du profilage](~/docs/python/media/profiling-start.png)

Lorsque vous sélectionnez **OK**, le profileur s’exécute et ouvre un rapport de performances vous permettant de connaître la répartition du temps dans l’application :

![Rapport de performances de profilage](~/docs/python/media/profiling-results.png)

Pour une vue d’ensemble, consultez ce qui suit.

Pour une démonstration de la procédure pas à pas, visionnez la vidéo [Profiling with Python Tools for Visual Studio](http://www.youtube.com/watch?v=K-KqkFkp55k) (Profilage avec Python Tools pour Visual Studio ; 8 min52 s).

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>Profilage pour IronPython

IronPython n’étant pas un interpréteur CPython, la fonctionnalité de profilage ci-dessus ne fonctionnera pas.

Utilisez plutôt le profileur Visual Studio .NET en lançant `ipy.exe` directement en tant qu’application cible, avec les arguments appropriés pour lancer votre script de démarrage. Ajoutez `-X:Debug` sur la ligne de commande pour forcer l’ensemble de votre code Python à être débogué et profilé. Un rapport de performances est ainsi généré, incluant le temps passé dans le runtime d’IronPython et votre code. Votre code est identifié à l’aide de noms tronqués.

IronPython possède également ses fonctionnalités de profilage intégrées, mais à ce jour, aucun visualiseur approprié n’est disponible pour celles-ci. Consultez [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Un profileur IronPython) (blogs MSDN) pour connaître ce qui est disponible.
