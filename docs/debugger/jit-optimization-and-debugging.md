---
title: JIT optimisation et débogage | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 917c9bab910b8f3153af46dc9d1d1a64ec6e529d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841263"
---
# <a name="jit-optimization-and-debugging"></a>Optimisation JIT et débogage
**Fonctionnement des optimisations dans .NET :** Si vous essayez de déboguer du code, il est plus facile lorsque que le code est **pas** optimisé. Il s’agit, car lors de l’optimisation de code, le compilateur et le runtime apporter des modifications au code UC émis afin qu’il s’exécute plus rapidement, mais a un mappage direct de moins de code source d’origine. Cela signifie que les débogueurs sont souvent impossible de vous indiquer la valeur des variables locales et pas à pas détaillé du code et des points d’arrêt peuvent ne pas fonctionneront comme prévu.

Normalement, la configuration de build Release crée un code optimisé et n’est pas le cas de la configuration de build de débogage. Le `Optimize` propriété MSBuild détermine si le compilateur doit optimiser le code.

Dans l’écosystème .NET, le code est activé à partir de la source pour des instructions de processeur dans un processus en deux étapes : tout d’abord, le C# compilateur convertit le texte que vous tapez dans une forme binaire intermédiaire appelée MSIL et il écrit dans les fichiers .dll. Plus tard, le Runtime .NET convertit cette MSIL pour des instructions de processeur. Les deux étapes peuvent optimiser dans une certaine mesure, mais la deuxième étape effectuée par le Runtime .NET effectue des optimisations plus significatives.

**L’option « Supprimer l’optimisation JIT lors du chargement de module (managé uniquement) » :** Le débogueur expose une option qui contrôle ce qui se passe lors du chargement d’une DLL qui est compilée avec les optimisations activées à l’intérieur du processus cible. Si cette option est désactivée (l’état par défaut), puis lorsque le Runtime .NET compile le code MSIL en code de l’UC, il laisse les optimisations activées. Si l’option est cochée, le débogueur demande ensuite que les optimisations être désactivées.

Pour rechercher le **supprimer l’optimisation JIT lors du chargement de module (managé uniquement)** option, sélectionnez **outils** > **Options**, puis sélectionnez le  **Général** page sous le **débogage** nœud.

**Lorsque vous devez cocher cette option :** Cochez cette option lorsque vous avez téléchargé les DLL à partir d’une autre source, tel qu’un package nuget, et que vous souhaitez déboguer le code dans cette DLL. Pour que cela fonctionne, vous devez également trouver le fichier de symboles (.pdb) pour cette DLL.

Si vous vous intéressez uniquement à déboguer le code que vous créez localement, il est préférable de laisser cette option désactivée, car, dans certains cas, l’activation de cette option sera ralentissent de manière significative le débogage. Il existe deux raison à cela ralentir :

* Code optimisé s’exécute plus rapidement. Si vous désactivez les optimisations pour un grand nombre de code, l’impact sur les performances peut totaliser.
* Si vous avez uniquement mon Code est activée, le débogueur ne même pas essayer et charger les symboles pour les DLL qui sont optimisés. Rechercher des symboles peut prendre un certain temps.

**Limitations de cette option :** Il existe deux situations où cette option sera **pas** fonctionne :

1. Dans les situations où vous attachez le débogueur à un processus déjà en cours d’exécution, cette option n’aura aucun effet sur les modules qui ont été déjà chargés au moment où que le débogueur a été attaché.
2. Cette option n’a aucun effet sur les DLL qui ont été précompilés (générées avec Ngen appelées) en code natif. Toutefois, vous pouvez désactiver l’utilisation de code précompilé en démarrant le processus avec l’environnement que variable 'COMPlus_ZapDisable » défini sur '1'.

## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Attacher à des processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processus d'exécution managée](/dotnet/standard/managed-execution-process)
