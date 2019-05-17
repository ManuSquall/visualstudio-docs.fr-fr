---
title: Visual C /C++ compatibilité de visualiseur personnalisé
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901164"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C /C++ compatibilité de visualiseur personnalisé

À compter de Visual Studio 2019, Visual C++ inclut un débogueur amélioré qui utilise un processus 64 bits externe pour l’hébergement de ses composants utilisant beaucoup de mémoire. Dans le cadre de cette mise à jour, certaines extensions de Visual C /C++ évaluateur d’expression doit être mis à jour pour les rendre compatibles avec le nouveau débogueur.

Si vous consommez une C hérité /C++ EE addin ou C /C++ visualiseur personnalisé, vous pouvez désactiver l’utilisation de ce processus externe en accédant à **outils** > **Options**  >  **Débogage**, puis en désactivant **symboles de débogage de charge dans un processus externe (natif uniquement)**. Si vous désélectionnez cette option, une augmentation significative de l’utilisation de la mémoire dans le processus de l’IDE (devenv.exe) se produit. Par conséquent, si vous prévoyez de déboguer des projets volumineux, il est recommandé que vous travaillez avec le propriétaire de l’extension pour le rendre compatible avec cette option de débogage.

Si vous êtes le propriétaire d’un C hérité /C++ EE addin ou C /C++ visualiseur personnalisé, vous pouvez trouver plus d’informations sur optant pour le chargement de votre extension dans un processus de travail sur le [wiki des exemples d’extensibilité Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Vous pouvez également trouver un [C /C++ exemple de visualiseur personnalisé](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).