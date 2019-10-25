---
title: Optimisation et débogage JIT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731622"
---
# <a name="jit-optimization-and-debugging"></a>Optimisation JIT et débogage
Fonctionnement **des optimisations dans .net :** Si vous essayez de déboguer du code, il est plus facile de le faire lorsque ce code n’est **pas** optimisé. En effet, lorsque le code est optimisé, le compilateur et le runtime apportent des modifications au code UC émis afin qu’il s’exécute plus rapidement, mais dispose d’un mappage moins direct au code source d’origine. Cela signifie que les débogueurs ne peuvent souvent pas vous indiquer la valeur des variables locales, et que le code pas à pas et les points d’arrêt peuvent ne pas fonctionner comme prévu.

Normalement, la configuration de build de version crée du code optimisé et la configuration de build Debug ne le fait pas. La `Optimize` propriété MSBuild contrôle si le compilateur est invité à optimiser le code.

Dans l’écosystème .NET, le code est converti des instructions source en processeur en deux étapes : tout d’abord, le C# compilateur convertit le texte que vous tapez en un format binaire intermédiaire appelé MSIL et écrit ce fichier dans les fichiers. dll. Plus tard, le Runtime .NET convertit ce MSIL en instructions de l’UC. Les deux étapes peuvent être optimisées dans une certaine mesure, mais la deuxième étape effectuée par le Runtime .NET effectue les optimisations les plus significatives.

**L’option’supprimer l’optimisation JIT lors du chargement du module (managé uniquement) ' :** Le débogueur expose une option qui contrôle ce qui se produit quand une DLL compilée avec des optimisations activées est chargée au sein du processus cible. Si cette option est désactivée (État par défaut), lorsque le Runtime .NET compile le code MSIL en code UC, les optimisations sont activées. Si l’option est activée, le débogueur demande que les optimisations soient désactivées.

Pour trouver l' **option Supprimer l’optimisation JIT lors du chargement du module (managé uniquement)** , sélectionnez **Outils**  > **options**, puis sélectionnez la page **général** sous le nœud **débogage** .

**Quand devez-vous activer cette option :** Activez cette option lorsque vous avez téléchargé les dll à partir d’une autre source, telle qu’un package NuGet, et que vous souhaitez déboguer le code dans cette DLL. Pour que cela fonctionne, vous devez également rechercher le fichier de symboles (. pdb) pour cette DLL.

Si vous êtes uniquement intéressé par le débogage du code que vous générez localement, il est préférable de ne pas activer cette option, car, dans certains cas, l’activation de cette option ralentit considérablement le débogage. Il y a deux raisons à ce ralentissement :

* Le code optimisé s’exécute plus rapidement. Si vous désactivez des optimisations pour un grand nombre de code, l’impact sur les performances peut s’en ajouter.
* Si vous avez Uniquement mon code activé, le débogueur n’essaiera même pas et ne chargera pas les symboles des dll optimisées. La recherche de symboles peut prendre beaucoup de temps.

**Limitations de cette option :** Il existe deux situations dans lesquelles cette option ne fonctionne **pas** :

1. Dans les situations où vous attachez le débogueur à un processus déjà en cours d’exécution, cette option n’a aucun effet sur les modules qui ont déjà été chargés au moment où le débogueur a été attaché.
2. Cette option n’a aucun effet sur les dll qui ont été précompilées (a. k. a générées avec NGen) en code natif. Toutefois, vous pouvez désactiver l’utilisation du code précompilé en démarrant le processus avec la variable d’environnement « COMPlus_ZapDisable » définie sur « 1 ».

## <a name="see-also"></a>Voir aussi
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)
- [S’attacher à des processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Processus d'exécution managée](/dotnet/standard/managed-execution-process)
