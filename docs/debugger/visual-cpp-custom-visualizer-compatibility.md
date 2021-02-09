---
title: Compatibilité du visualiseur personnalisé Visual C/C++
description: Une nouvelle fonctionnalité de Visual Studio 2019 peut ne pas être compatible avec les compléments d’évaluateur d’expression C/C++ hérités et les visualiseurs personnalisés. Pour plus d’informations, voir cet article.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32ad6b4b699f9cfe02739f341a4f9ddf29360f37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884310"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilité du visualiseur personnalisé Visual C/C++

À compter de Visual Studio 2019, C++ intègre un débogueur amélioré qui utilise un processus externe 64 bits pour héberger ses composants gourmands en mémoire. Dans le cadre de cette mise à jour, certaines extensions de l’évaluateur d’expression C/C++ doivent être mises à jour pour qu’elles soient compatibles avec le nouveau débogueur.

Si vous utilisez actuellement un complément c/c++ EE ou un visualiseur personnalisé c/c++ hérité, vous pouvez désactiver l’utilisation de ce processus externe en accédant à **Outils**  >  **options**  >  **débogage**, puis en désélectionnant **charger les symboles de débogage dans le processus externe (natif uniquement)**. Si vous désélectionnez cette option, une augmentation significative de l’utilisation de la mémoire dans le processus de l’IDE (devenv.exe) aura lieu. Par conséquent, si vous envisagez de déboguer des projets volumineux, il est recommandé de travailler avec le propriétaire de l’extension pour le rendre compatible avec cette option de débogage.

Si vous êtes le propriétaire d’un complément hérité C/C++ EE ou d’un visualiseur personnalisé C/C++, vous trouverez plus d’informations sur l’activation du chargement de votre extension dans un processus de travail sur le [wiki d’exemples d’extensibilité Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Vous trouverez également un [exemple de visualiseur personnalisé C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).