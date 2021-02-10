---
title: Optimisation et débogage JIT | Microsoft Docs
description: Le code optimisé est plus difficile à déboguer que le code qui ne l’est pas. En savoir plus sur l’optimisation JIT et sur le moment et la façon de le supprimer.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 558a54f6ddcf4945da4937f75b8aa133949349a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931082"
---
# <a name="jit-optimization-and-debugging"></a>Optimisation JIT et débogage
Si vous essayez de déboguer du code, il est plus facile de le faire lorsque ce code n’est **pas** optimisé. Lorsque le code est optimisé, le compilateur et le runtime apportent des modifications au code UC émis afin qu’il s’exécute plus rapidement, mais dispose d’un mappage moins direct au code source d’origine. Si le mappage est moins direct, les débogueurs sont souvent incapables de vous indiquer la valeur des variables locales, et le code pas à pas et les points d’arrêt peuvent ne pas fonctionner comme prévu.

> [!NOTE]
> Pour plus d’informations sur le débogage JIT (juste à temps), consultez [cette documentation](../debugger/debug-using-the-just-in-time-debugger.md).

## <a name="how-optimizations-work-in-net"></a>Fonctionnement des optimisations dans .NET 
Normalement, la configuration de build de version crée du code optimisé et la configuration de build Debug ne le fait pas. La `Optimize` propriété MSBuild contrôle si le compilateur est invité à optimiser le code.

Dans l’écosystème .NET, le code est converti des instructions source en processeur en deux étapes : tout d’abord, le compilateur C# convertit le texte que vous tapez en un format binaire intermédiaire appelé MSIL et écrit le code MSIL dans les fichiers. dll. Plus tard, le Runtime .NET convertit ce MSIL en instructions de l’UC. Les deux étapes peuvent être optimisées dans une certaine mesure, mais la deuxième étape effectuée par le Runtime .NET effectue les optimisations les plus significatives.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>Option « Supprimer l’optimisation JIT lors du chargement du module (managé uniquement) »
Le débogueur expose une option qui contrôle ce qui se produit quand une DLL compilée avec des optimisations activées est chargée au sein du processus cible. Si cette option est désactivée (État par défaut), lorsque le Runtime .NET compile le code MSIL en code UC, les optimisations sont activées. Si l’option est activée, le débogueur demande que les optimisations soient désactivées.

Pour trouver l’option **Supprimer l’optimisation JIT lors du chargement du module (managé uniquement)** , sélectionnez **Outils**  >  **options**, puis sélectionnez la page **général** sous le nœud **débogage** .

![Supprimer l’optimisation JIT](../debugger/media/suppress-jit-tool-options.png "Supprimer l’optimisation JIT")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>Quand devez-vous activer l’option « Supprimer l’optimisation JIT » ?
Activez cette option lorsque vous avez téléchargé les dll à partir d’une autre source, telle qu’un package NuGet, et que vous souhaitez déboguer le code dans cette DLL. Pour que la suppression fonctionne, vous devez également rechercher le fichier de symboles (. pdb) pour cette DLL.

Si vous êtes uniquement intéressé par le débogage du code que vous générez localement, il est préférable de ne pas activer cette option, car, dans certains cas, l’activation de cette option ralentit considérablement le débogage. Deux raisons peuvent expliquer ce ralentissement :

* Le code optimisé s’exécute plus rapidement. Si vous désactivez des optimisations pour un grand nombre de code, l’impact sur les performances peut s’en ajouter.
* Si vous avez Uniquement mon code activé, le débogueur n’essaiera même pas de charger les symboles pour les dll qui sont optimisées. La recherche de symboles peut prendre beaucoup de temps.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Limitations de l’option « Supprimer l’optimisation JIT » 
Il existe deux situations dans lesquelles l’activation de cette option ne fonctionne **pas** :

1. Dans les situations où vous attachez le débogueur à un processus déjà en cours d’exécution, cette option n’a aucun effet sur les modules qui ont déjà été chargés au moment où le débogueur a été attaché.
2. Cette option n’a aucun effet sur les dll qui ont été précompilées (a. k. a générées avec NGen) en code natif. Toutefois, vous pouvez désactiver l’utilisation du code précompilé en démarrant le processus avec la variable d’environnement **'COMPlus_ReadyToRun'** définie sur **' 0 '**. Cela indique au Runtime .NET Core de désactiver l’utilisation d’images précompilées, en forçant le runtime à compiler le code d’infrastructure juste-à-temps. 

    > [!IMPORTANT]
    > Si vous ciblez .NET Framework ou une version antérieure de .NET Core (2. x ou inférieure), ajoutez également la variable d’environnement « COMPlus_ZapDisable » et affectez-lui la valeur « 1 ».

    **Pour définir une variable d’environnement pour un projet .NET Core dans Visual Studio :**
    1. Dans le **Explorateur de solutions**, **cliquez avec le bouton droit sur** le fichier projet et sélectionnez **Propriétés**.
    2. Accédez à l’onglet **Déboguer** et sous **variables d’environnement**, cliquez sur le bouton **Ajouter** .
    3. Définissez nom (clé) sur **COMPlus_ReadyToRun** et définissez la valeur sur **0**.

    ![Définir COMPlus_ReadyToRun variable d’environnement](../debugger/media/environment-variables-debug-menu.png "Définir COMPlus_ReadyToRun variable d’environnement")

## <a name="see-also"></a>Voir aussi
- [Comment déboguer une source de .NET Framework](../debugger/how-to-debug-dotnet-framework-source.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)
- [Joindre aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Processus d’exécution managée](/dotnet/standard/managed-execution-process)
