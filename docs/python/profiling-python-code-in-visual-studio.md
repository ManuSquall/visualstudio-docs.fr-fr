---
title: Mesurer les performances du code Python
description: Utilisez le profileur Visual Studio pour vérifier les performances du code Python lors de l’utilisation d’interpréteurs CPython.
ms.date: 11/12/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 840ebd6d5341bd38fb8961f4ead15fe5181e1ca3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149625"
---
# <a name="profile-python-code"></a>Profiler du code Python

Vous pouvez profiler une application Python si des interpréteurs CPython sont utilisés. (Consultez [Profilage dans la matrice des fonctionnalités](overview-of-python-tools-for-visual-studio.md#matrix-profiling) pour connaître la disponibilité de cette fonctionnalité dans les différentes versions de Visual Studio.)

## <a name="profiling-for-cpython-based-interpreters"></a>Profilage pour les interpréteurs CPython

La commande de menu **Analyser** > **Lancer le profilage Python** permet de lancer le profilage, ce qui entraîne l’ouverture d’une boîte de dialogue de configuration :

![Boîte de dialogue de configuration du profilage](media/profiling-start.png)

Lorsque vous sélectionnez **OK**, le profileur s’exécute et ouvre un rapport de performances vous permettant de connaître la répartition du temps dans l’application :

![Rapport de performances de profilage](media/profiling-results.png)

> [!Note]
> Actuellement, Visual Studio ne prend en charge que ce niveau de profilage sur l’application tout entière, mais nous serions ravis de recevoir vos commentaires sur les fonctionnalités à venir. Utilisez le bouton **Commentaires sur les produits** en bas de cette page.

## <a name="profiling-for-ironpython"></a>Profilage pour IronPython

IronPython n’étant pas un interpréteur CPython, la fonctionnalité de profilage ci-dessus ne fonctionne pas.

Utilisez plutôt le profileur Visual Studio .NET en lançant *ipy.exe* directement en tant qu’application cible. Utilisez les arguments appropriés pour lancer votre script de démarrage. Ajoutez `-X:Debug` sur la ligne de commande pour s’assurer que l’ensemble de votre code Python peut être débogué et profilé. Cet argument génère un rapport de performances qui inclut le temps passé dans le runtime IronPython et votre code. Votre code est identifié à l’aide de noms tronqués.

IronPython possède également ses fonctionnalités de profilage intégrées, mais à ce jour, aucun visualiseur approprié n’est disponible pour celles-ci. Consultez [An IronPython Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (Un profileur IronPython) (blogs MSDN) pour connaître ce qui est disponible.
