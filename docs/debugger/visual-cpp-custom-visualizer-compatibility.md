---
title: Compatibilité avec leC++ visualiseur Visual C/personnalisé
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
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430617"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilité avec leC++ visualiseur Visual C/personnalisé

À compter de Visual Studio 2019 C++ , intègre un débogueur amélioré qui utilise un processus externe 64 bits pour héberger ses composants gourmands en mémoire. Dans le cadre de cette mise à jour, certaines extensions deC++ l’évaluateur d’expression C/doivent être mises à jour pour qu’elles soient compatibles avec le nouveau débogueur.

Si vous consommez actuellement un complément C/C++ EE hérité ou un visualiseurC++ c/personnalisé, vous pouvez désactiver l’utilisation de ce processus externe en accédant à **outils** > **options** > **débogage**, puis en désélectionnant **charger le débogage. symboles dans le processus externe (natif uniquement)** . Si vous désélectionnez cette option, une augmentation significative de l’utilisation de la mémoire dans le processus IDE (devenv. exe) se produit. Par conséquent, si vous envisagez de déboguer des projets volumineux, il est recommandé de travailler avec le propriétaire de l’extension pour le rendre compatible avec cette option de débogage.

Si vous êtes le propriétaire d’un complément C/C++ EE ou d’un visualiseurC++ c/personnalisé hérité, vous trouverez plus d’informations sur l’activation du chargement de votre extension dans un processus de travail sur le [wiki des exemples d’extensibilité Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Vous trouverez également un [exemple de visualiseurC++ C/personnalisé](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).