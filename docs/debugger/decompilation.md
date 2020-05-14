---
title: Décompiler le code .NET tout en débogage Microsoft Docs
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
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508743"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Générer du code source à partir d’assemblages .NET tout en débogage

Lorsque vous débogagez une application .NET, vous pouvez constater que vous voulez afficher le code source que vous n’avez pas. Par exemple, casser une exception ou utiliser la pile d’appels pour naviguer vers un emplacement source.

> [!NOTE]
> * La génération de code source (décomposition) n’est disponible que pour les applications .NET et est basée sur le projet open source [ILSpy.](https://github.com/icsharpcode/ILSpy)
> * La décomposition n’est disponible que dans Visual Studio 2019 16.5 et plus tard.
> * L’application de l’attribut [SuppressIldasmAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) à un assemblage ou à un module empêche Visual Studio de tenter la décomposition.

## <a name="generate-source-code"></a>Générer du code source

Lorsque vous débugging et aucun code source n’est disponible, Visual Studio affiche le document **Source Non Trouvé,** ou si vous n’avez pas de symboles pour l’assemblage, le document **No Symbols Loaded.** Les deux documents disposent **d’une** option de code source de décomposition qui génère du code C pour l’emplacement actuel. Le code Cmd généré peut ensuite être utilisé comme n’importe quel autre code source. Vous pouvez afficher le code, inspecter les variables, définir les points de rupture, etc.

### <a name="no-symbols-loaded"></a>Aucun symbole chargé

L’illustration suivante montre le message **No Symbols Loaded.**

![Capture d’écran d’aucun document chargé de symbole](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Source non trouvée

L’illustration suivante montre le message **Source Non Trouvé.**

![Capture d’écran de la source non trouvé document](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Générer et intégrer des sources pour un assemblage

En plus de générer du code source pour un emplacement spécifique, vous pouvez générer tout le code source pour un assemblage .NET donné. Pour ce faire, rendez-vous sur la fenêtre **Modules** et dans le menu contextuelle d’un assemblage .NET, puis sélectionnez la commande **de code source Decompile.** Visual Studio génère un fichier de symbole pour l’assemblage, puis intègre la source dans le fichier symbole. Dans une étape ultérieure, vous pouvez [extraire](#extract-and-view-the-embedded-source-code) le code source intégré.

![Capture d’écran du menu contexte d’assemblage dans la fenêtre des modules avec commande source de décomposition.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extraire et afficher le code source intégré

Vous pouvez extraire des fichiers sources qui sont intégrés dans un fichier symbole à l’aide de la commande **de code source d’extraction** dans le menu contextuelle de la fenêtre **Modules.**

![Capture d’écran du menu contexte d’assemblage dans la fenêtre des modules avec la commande de sources d’extrait.](media/decompilation-extract-source-code.png)

Les fichiers source extraits sont ajoutés à la solution sous forme [de fichiers divers.](../ide/reference/miscellaneous-files.md) La fonction fichiers divers est éteinte par défaut dans Visual Studio. Vous pouvez activer cette fonctionnalité à partir des **outils** > **Options** > **Environnement** > **Documents** > Afficher des fichiers divers dans la case à cocher Solution**Explorer.** Sans activer cette fonctionnalité, vous ne serez pas en mesure d’ouvrir le code source extrait.

![Capture d’écran de la page d’option d’outils avec option de fichiers divers activé.](media/decompilation-tools-options-misc-files.png)

Les fichiers source extraits apparaissent dans les fichiers divers de **Solution Explorer**.

![Capture d’écran de l’explorateur de solution avec des fichiers divers.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Limitations connues

### <a name="requires-break-mode"></a>Nécessite un mode de rupture

Générer du code source à l’aide de la décomposition n’est possible que lorsque le débbuggeur est en mode pause et que l’application est mise en pause. Par exemple, Visual Studio entre en mode pause lorsqu’il heurte un point d’arrêt ou une exception. Vous pouvez facilement déclencher Visual Studio pour casser la prochaine fois![que](media/decompilation-break-all.png)votre code s’exécute en utilisant la commande **Break All** ( Break all icon ).

### <a name="decompilation-limitations"></a>Limitations de décomposition

Générer du code source à partir du format intermédiaire (IL) qui est utilisé dans les assemblages .NET a certaines limites inhérentes. En tant que tel, le code source généré ne ressemble pas au code source d’origine. La plupart des différences se trouvent dans des endroits où les informations contenues dans le code source d’origine ne sont pas nécessaires au moment de l’exécution. Par exemple, des informations telles que l’espace blanc, les commentaires et les noms des variables locales ne sont pas nécessaires au moment de l’exécution. Nous vous recommandons d’utiliser la source générée pour comprendre comment le programme est exécuté et non pas comme un remplacement pour le code source d’origine.

### <a name="debug-optimized-or-release-assemblies"></a>Assemblages de débbug optimisés ou de libération

Lorsque vous débogiez le code qui a été décomposé à partir d’un assemblage qui a été compilé à l’aide d’optimisations compilateurs, vous pouvez rencontrer les questions suivantes:
- Les points d’arrêt ne peuvent pas toujours se lier à l’emplacement d’approvisionnement correspondant.
- Le pas peut ne pas toujours marcher à l’endroit correct.
- Les variables locales peuvent ne pas avoir de noms exacts.
- Certaines variables peuvent ne pas être disponibles pour évaluation.

Plus de détails peuvent être trouvés dans le numéro GitHub: [ICSharpCode.Decompiler intégration dans VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Fiabilité de décomposition

Un pourcentage relativement faible de tentatives de décomposition peut entraîner un échec. Ceci est dû à une erreur de référence nulle point de séquence dans ILSpy.  Nous avons atténué l’échec en attrapant ces problèmes et en échouant gracieusement à la tentative de décomposition.

Plus de détails peuvent être trouvés dans le numéro GitHub: [ICSharpCode.Decompiler intégration dans VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Limitations avec code async

Les résultats des modules de décomposition avec des modèles de code async/await peuvent être incomplets ou échouer complètement. La mise en œuvre ILSpy des machines d’État async/await et de rendement n’est que partiellement mise en œuvre. 

Plus de détails peuvent être trouvés dans le numéro GitHub: [PDB Generator Status](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Uniquement mon code

Les paramètres [Just My Code (JMC)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) permettent à Visual Studio de passer au-dessus du système, du cadre, de la bibliothèque et d’autres appels non-utilisateurs. Au cours d’une session de débogage, la fenêtre **Modules** montre quels modules de code le débbuggeur traite comme Mon Code (code utilisateur).

La décomposition des modules optimisés ou de sortie produit du code non utilisateur. Si le débogénaire se casse dans votre code non utilisateur en décomposition, par exemple, la fenêtre **No Source** apparaît. Pour désactiver Just My Code, naviguez vers des > options **d’outils** > **Options** (ou **de déboptées** > **Options**) > **Debugging****General**, puis désélectionner Enable Just **My Code**.

### <a name="extracted-sources"></a>Sources extraites

Le code source extrait d’un assemblage a les limites suivantes :
- Le nom et l’emplacement des fichiers générés ne sont pas configurables.
- Les fichiers sont temporaires et seront supprimés par Visual Studio.
- Les fichiers sont placés dans un seul dossier et toute hiérarchie de dossier que les sources d’origine n’ont pas été utilisées.
- Le nom de fichier de chaque fichier contient un hachage de chèques du fichier.

### <a name="generated-code-is-c-only"></a>Le code généré est C
La décomposition ne génère que des fichiers de code source dans le C. Il n’y a pas d’option pour générer des fichiers dans une autre langue.
