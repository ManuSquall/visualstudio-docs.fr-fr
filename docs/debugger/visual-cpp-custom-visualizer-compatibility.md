---
title: Compatibilité du visualiseur personnalisé Visual C/C++
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72430617"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilité du visualiseur personnalisé Visual C/C++

À compter de Visual Studio 2019, C++ intègre un débogueur amélioré qui utilise un processus externe 64 bits pour héberger ses composants gourmands en mémoire. Dans le cadre de cette mise à jour, certaines extensions de l’évaluateur d’expression C/C++ doivent être mises à jour pour qu’elles soient compatibles avec le nouveau débogueur.

Si vous consommez actuellement un complément hérité c/c++ EE ou un visualiseur personnalisé c/c++, vous pouvez désactiver l’utilisation de ce processus externe en accédant à **Outils**  >  **options**  >  **débogage**, puis en désélectionnant **charger les symboles de débogage dans le processus externe (natif uniquement)**. Si vous désélectionnez cette option, une augmentation significative de l’utilisation de la mémoire dans le processus de l’IDE (devenv.exe) aura lieu. Par conséquent, si vous envisagez de déboguer des projets volumineux, il est recommandé de travailler avec le propriétaire de l’extension pour le rendre compatible avec cette option de débogage.

Si vous êtes le propriétaire d’un complément hérité C/C++ EE ou d’un visualiseur personnalisé C/C++, vous trouverez plus d’informations sur l’activation du chargement de votre extension dans un processus de travail sur le [wiki des exemples d’extensibilité Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Vous trouverez également un [exemple de visualiseur personnalisé C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).