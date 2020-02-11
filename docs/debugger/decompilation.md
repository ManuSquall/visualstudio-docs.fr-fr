---
title: Décompiler du code .NET pendant le débogage | Microsoft Docs
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: ffd5f2e4bfc13f79b519fbdf9b3cf517793cd324
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091932"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Générer du code source à partir d’assemblys .NET pendant le débogage

Lors du débogage d’une application .NET, il se peut que vous souhaitiez afficher le code source dont vous n’avez pas besoin. Par exemple, l’arrêt sur une exception ou l’utilisation de la pile des appels pour naviguer jusqu’à un emplacement source.

> [!NOTE]
> * La génération de code source (décompilation) est uniquement disponible pour les applications .NET et est basée sur le projet [ILSpy](https://github.com/icsharpcode/ILSpy) Open source.
> * La décompilation est disponible uniquement dans Visual Studio 2019 16,5 et versions ultérieures.

## <a name="generate-source-code"></a>Générer le code source

Lorsque vous effectuez un débogage et qu’aucun code source n’est disponible, Visual Studio affiche le document **source introuvable** ou, si vous n’avez pas de symboles pour l’assembly, le document **aucun symbole n'** a été chargé. Les deux documents ont une option **décompiler le code source** qui génère C# du code pour l’emplacement actuel. Le code C# généré peut ensuite être utilisé comme tout autre code source. Vous pouvez afficher le code, inspecter les variables, définir des points d’arrêt, etc.

### <a name="no-symbols-loaded"></a>Aucun symbole chargé

L’illustration suivante montre le message **aucun symbole chargé** .

![Capture d’écran de document aucun symbole chargé](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Source introuvable

L’illustration suivante montre le message **source introuvable** .

![Capture d’écran du document source introuvable](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Générer et incorporer des sources pour un assembly

En plus de générer le code source d’un emplacement spécifique, vous pouvez générer tout le code source d’un assembly .NET donné. Pour ce faire, accédez à la fenêtre **modules** et, dans le menu contextuel d’un assembly .net, puis sélectionnez la commande **décompiler le code source** . Visual Studio génère un fichier de symboles pour l’assembly, puis incorpore la source dans le fichier de symboles. Dans une étape ultérieure, vous pouvez [extraire](#extract-and-view-the-embedded-source-code) le code source incorporé.

![Capture d’écran du menu contextuel de l’assembly dans la fenêtre modules avec la commande source Decompile.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extraire et afficher le code source incorporé

Vous pouvez extraire les fichiers sources incorporés dans un fichier de symboles à l’aide de la commande **extraire le code source** dans le menu contextuel de la fenêtre **modules** .

![Capture d’écran du menu contextuel de l’assembly dans la fenêtre modules avec la commande extraire les sources.](media/decompilation-extract-source-code.png)

Les fichiers sources extraits sont ajoutés à la solution en tant que [fichiers divers](../ide/reference/miscellaneous-files.md). La fonctionnalité fichiers divers est désactivée par défaut dans Visual Studio. Vous pouvez activer cette fonctionnalité à partir de la case à cocher **outils** > **Options** > **environnement** > **Documents** > **afficher les fichiers divers dans Explorateur de solutions** . Si vous n’activez pas cette fonctionnalité, vous ne pourrez pas ouvrir le code source extrait.

![Capture d’écran de la page d’options outils avec l’option fichiers divers activée.](media/decompilation-tools-options-misc-files.png)

Les fichiers sources extraits apparaissent dans les fichiers divers de **Explorateur de solutions**.

![Capture d’écran de l’Explorateur de solutions avec fichiers divers.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Limitations connues

### <a name="requires-break-mode"></a>Nécessite le mode arrêt

La génération du code source à l’aide de la décompilation est possible uniquement lorsque le débogueur est en mode arrêt et que l’application est suspendue. Par exemple, Visual Studio passe en mode arrêt lorsqu’il atteint un point d’arrêt ou une exception. Vous pouvez facilement déclencher l’arrêt de Visual Studio lors de la prochaine exécution de votre code à l’aide de la commande **arrêter tout** (![icône arrêter tout](media/decompilation-break-all.png)).

### <a name="decompilation-limitations"></a>Limitations de décompilation

La génération de code source à partir du format intermédiaire (IL) utilisé dans les assemblys .NET présente des limitations inhérentes. Par conséquent, le code source généré ne ressemble pas au code source d’origine. La plupart des différences résident dans les endroits où les informations du code source d’origine ne sont pas nécessaires au moment de l’exécution. Par exemple, les informations telles que les espaces blancs, les commentaires et les noms des variables locales ne sont pas nécessaires au moment de l’exécution. Nous vous recommandons d’utiliser la source générée pour comprendre comment le programme s’exécute et non en remplacement du code source d’origine.

### <a name="debug-optimized-or-release-assemblies"></a>Déboguer des assemblys optimisés ou de version

Lors du débogage du code qui a été décompilé à partir d’un assembly qui a été compilé à l’aide des optimisations du compilateur, vous pouvez rencontrer les problèmes suivants :
- Les points d’arrêt ne sont pas toujours liés à l’emplacement de l’approvisionnement correspondant.
- L’exécution pas à pas ne passe pas toujours à l’emplacement correct.
- Les variables locales peuvent ne pas avoir de noms exacts.

Pour plus d’informations, consultez le problème GitHub : [IChsarpCompiler. décompilateur Integration dans vs Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="extracted-sources"></a>Sources extraites

Le code source extrait d’un assembly présente les limitations suivantes :
- Le nom et l’emplacement des fichiers générés ne sont pas configurables.
- Les fichiers sont temporaires et seront supprimés par Visual Studio.
- Les fichiers sont placés dans un dossier unique et toute hiérarchie de dossiers dont les sources d’origine n’avaient pas été utilisées.
- Le nom de fichier de chaque fichier contient un hachage de somme de contrôle du fichier.

### <a name="generated-code-is-c-only"></a>Le code généré C# est uniquement
La décompilation génère uniquement des fichiers de C#code source dans. Il n’existe aucune option pour générer des fichiers dans d’autres langues.