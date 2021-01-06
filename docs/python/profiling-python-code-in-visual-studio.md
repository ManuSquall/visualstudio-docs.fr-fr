---
title: Mesurer les performances du code Python
description: Utilisez le profileur Visual Studio pour vérifier les performances du code Python lors de l’utilisation d’interpréteurs CPython.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e6a37301477b43063169143456fc21a3c783968
ms.sourcegitcommit: 4976419fae731860295dbcd072e6778832f7255d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917925"
---
# <a name="profile-python-code"></a>Profiler du code Python

Vous pouvez profiler une application Python si des interpréteurs CPython sont utilisés. (Consultez [Profilage dans la matrice des fonctionnalités](overview-of-python-tools-for-visual-studio.md#matrix-profiling) pour connaître la disponibilité de cette fonctionnalité dans les différentes versions de Visual Studio.)

## <a name="profiling-for-cpython-based-interpreters"></a>Profilage pour les interpréteurs CPython

Le profilage est démarré par le biais de la commande de menu **Déboguer**  >  **lancer le profilage python** , qui ouvre une boîte de dialogue de configuration :

![Boîte de dialogue de configuration du profilage](media/profiling-start.png)

Lorsque vous sélectionnez **OK**, le profileur s’exécute et ouvre un rapport de performances vous permettant de connaître la répartition du temps dans l’application :

![Rapport de performances de profilage](media/profiling-results.png)

> [!Note]
> Lorsque vous profilez une application Python, Visual Studio collecte des données pendant la durée de vie du processus. À l’heure actuelle, il n’est pas possible de suspendre le profilage. Nous souhaitons connaître vos commentaires sur les futures fonctionnalités. Utilisez le bouton **Commentaires sur les produits** en bas de cette page.

## <a name="profiling-for-ironpython"></a>Profilage pour IronPython

IronPython n’étant pas un interpréteur CPython, la fonctionnalité de profilage ci-dessus ne fonctionne pas.

Utilisez plutôt le profileur Visual Studio .NET en lançant *ipy.exe* directement en tant qu’application cible. Utilisez les arguments appropriés pour lancer votre script de démarrage. Ajoutez `-X:Debug` sur la ligne de commande pour s’assurer que l’ensemble de votre code Python peut être débogué et profilé. Cet argument génère un rapport de performances qui inclut le temps passé dans le runtime IronPython et votre code. Votre code est identifié à l’aide de noms tronqués.

IronPython possède également ses fonctionnalités de profilage intégrées, mais à ce jour, aucun visualiseur approprié n’est disponible pour celles-ci. Consultez [An IronPython Profiler](/archive/blogs/curth/an-ironpython-profiler) (Un profileur IronPython) (blogs MSDN) pour connaître ce qui est disponible.