---
title: JIT optimisation et débogage | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 9a9b18ab38c7c19fa5208d34439bd3133099e8bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="jit-optimization-and-debugging"></a>Optimisation JIT et débogage
**Fonctionnement des optimisations dans .NET :** si vous tentez de déboguer du code, il est plus facile lorsque que le code est **pas** optimisé. Il s’agit, car lors de l’optimisation de code, le compilateur et le runtime modifier le code de l’UC émis afin qu’il s’exécute plus rapidement, mais possède un mappage direct moins de code source d’origine. Cela signifie que les débogueurs sont souvent impossible de vous indiquent la valeur des variables locales et pas à pas détaillé du code et points d’arrêt peuvent ne pas fonctionneront comme prévu.

Normalement, la configuration de build Release crée un code optimisé et n’est pas le cas de la configuration de build Debug. Le `Optimize` propriété MSBuild contrôle si le compilateur doit optimiser le code.

Dans l’écosystème .NET, le code est activé à partir de la source pour obtenir des instructions de processeur dans un processus en deux étapes : tout d’abord, le compilateur c# convertit le texte que vous tapez dans une forme binaire intermédiaire appelée MSIL et il écrit pour les fichiers .dll. Une version ultérieure, le Runtime .NET convertit ce MSIL pour obtenir des instructions de processeur. Les deux étapes peuvent optimiser dans une certaine mesure, mais la deuxième étape, effectuée par le Runtime .NET effectue les optimisations plus importantes.

**L’option « Supprimer l’optimisation JIT lors du chargement du module (managé uniquement) » :** le débogueur expose une option qui contrôle ce qui se passe lors de la charge d’une DLL qui est compilée avec les optimisations activées à l’intérieur du processus cible. Si cette option est désactivée (l’état par défaut), puis lorsque le Runtime .NET compile le code MSIL en code UC, elle laisse les optimisations activées. Si l’option est activée, le débogueur demande que les optimisations être désactivé.

Le **supprimer l’optimisation JIT lors du chargement du module (managé uniquement)** option se trouvent sur le **général** page sous le **débogage** nœud dans la **Options** boîte de dialogue.

**Lorsque vous devez cocher cette option :** Activez cette option lorsque vous avez téléchargé les DLL à partir d’une autre source, tel qu’un package nuget, et que vous souhaitez déboguer le code dans cette DLL. Pour que cela fonctionne, vous devez également trouver le fichier de symboles (.pdb) pour cette DLL.

Si vous êtes uniquement intéressé par le code que vous créez localement le débogage, il est préférable de laisser cette option est désactivée, car, dans certains cas, l’activation de cette option sera considérablement ralentir le débogage. Il existe deux raisons ralentir :

* Le code optimisé est plus rapide. Si vous désactivez les optimisations d’une quantité de code, l’impact sur les performances peut s’ajouter.
* Si vous avez uniquement mon Code est activé, le débogueur même pas essayer et charger des symboles pour les DLL qui sont optimisées. Rechercher des symboles peut prendre beaucoup de temps.

**Limitations de cette option :** il existe deux situations où cette option sera **pas** de travail :

1. Dans les situations où vous attachez le débogueur à un processus déjà en cours d’exécution, cette option n’aura aucun effet sur les modules qui ont été déjà chargé au moment où que le débogueur est attaché.
2. Cette option n’a aucun effet sur les DLL qui ont été précompilé (générées avec Ngen de connu) en code natif. Toutefois, vous pouvez désactiver l’utilisation de code précompilé en démarrant le processus avec l’environnement de que variable 'COMPlus_ZapDisable' la valeur '1'.

## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processus d'exécution managée](/dotnet/standard/managed-execution-process)
