---
title: Compatibilité de visualiseur personnalisé Visual C/C++
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
ms.assetid: 64af5bed-e38b-420f-b9ce-d64f35100aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 43ac7f0f5506725103d185e575514e821674eb27
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232188"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilité de visualiseur personnalisé Visual C/C++

À partir de Visual Studio 2019, Visual C++ inclut un débogueur amélioré qui utilise un processus 64 bits externe pour l’hébergement de ses composants utilisant beaucoup de mémoire. Dans le cadre de cette mise à jour, certaines extensions de l’évaluateur d’expression de Visual C/C++ doivent être mis à jour pour les rendre compatibles avec le nouveau débogueur.

Si vous consommez actuellement un hérité addin EE de C/C++ ou un visualiseur personnalisé C/C++, vous pouvez désactiver l’utilisation de ce processus externe en accédant à **outils** > **Options**  >   **Débogage**, puis en désactivant **symboles de débogage de charge dans un processus externe (natif uniquement)**. Si vous désélectionnez cette option, une augmentation significative de l’utilisation de la mémoire dans le processus de l’IDE (devenv.exe) se produit. Par conséquent, si vous prévoyez de déboguer des projets volumineux, il est recommandé que vous travaillez avec le propriétaire de l’extension pour le rendre compatible avec cette option de débogage.

Si vous êtes le propriétaire d’un hérité addin EE de C/C++ ou d’un visualiseur personnalisé C/C++, vous trouverez plus d’informations sur optant pour le chargement de votre extension dans un processus de travail sur le [wiki des exemples d’extensibilité Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Vous pouvez également trouver un [exemple de visualiseur personnalisé C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).