---
title: Paramètres de projet pour une configuration Debug C# | Microsoft Docs
description: Découvrez comment modifier les paramètres du projet pour une configuration Debug C# dans Visual Studio, à l’aide de l’onglet déboguer et de l’onglet générer des pages de propriétés du projet.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3377187412f95e090c7403ddd6f898a18f6cec9f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386499"
---
# <a name="project-settings-for--c-debug-configurations"></a>Paramètres de projet pour des configurations Debug C#

Vous pouvez modifier les paramètres de débogage de projet C# sous l’onglet [Déboguer](#debug-tab) et l' [onglet générer](#build-tab) des pages de propriétés du projet.

Pour ouvrir les pages de propriétés, sélectionnez le projet dans **Explorateur de solutions** puis sélectionnez l’icône **Propriétés** , ou cliquez avec le bouton droit sur le projet et sélectionnez **Propriétés**.

Pour plus d’informations, consultez [Configurations Debug et Release](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Ces paramètres ne s’appliquent pas aux applications .NET Core, ASP.NET ou UWP. Pour configurer les paramètres de débogage pour les applications UWP, consultez [Démarrer une session de débogage pour une application UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Onglet Déboguer

|Paramètre|Description|
|-------------------------------------| - |
| **Configuration** | Définit le mode de génération de l’application. Dans la liste déroulante, sélectionnez **active (débogage)**, **Debug**, **Release** ou **toutes les configurations** . |
| **Action de démarrage** | Spécifie l’action lorsque vous sélectionnez **Démarrer** dans une configuration de débogage.<br />- **Démarrer le projet** est la valeur par défaut et lance le projet de démarrage pour le débogage. Pour plus d’informations, consultez [choisir le projet de démarrage](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Démarrer le programme externe** démarre et se connecte à une application qui ne fait pas partie d’un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution avec le débogueur](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Démarrer le navigateur avec l’URL** vous permet de déboguer une application Web. |
| **Options**  >  de démarrage **Arguments de ligne de commande** | Spécifie les arguments de ligne de commande pour l’application en cours de débogage. Le nom de la commande est le nom de l’application spécifié dans **Démarrer le programme externe**. |
| **Options**  >  de démarrage **Répertoire de travail** | Spécifie le répertoire de travail de l’application en cours de débogage. En C#, le répertoire de travail est *\bin\Debug* par défaut.
| **Options**  >  de démarrage **Utiliser l’ordinateur distant**|Pour le débogage distant, sélectionnez cette option et entrez le nom de la cible de débogage distant, ou un [nom de serveur Msvsmon](../debugger/remote-debugging.md). <br />L’emplacement d’une application sur l’ordinateur distant est spécifié par la propriété **chemin de sortie** sous l’onglet **générer** . L’emplacement doit être un répertoire partageable sur l’ordinateur distant.
| Moteur du débogueur   >  **Activer le débogage de code non managé** | Débogue les appels au code Win32 natif (non managé) à partir de l’application gérée. |
| Moteur du débogueur   >  **Activer le débogage SQL Server** | Débogue SQL Server objets de base de données. |

## <a name="build-tab"></a>Onglet Générer

|Paramètre|Description|
|-------------|-----------------|
|**Général**  >  **Symboles de compilation conditionnelle**|Définissez les constantes DEBUG et TRACE si elles sont sélectionnées.<br /><br /> Ces constantes activent la compilation conditionnelle de la [classe Debug](/dotnet/api/system.diagnostics.debug) et de la [classe Trace](/dotnet/api/system.diagnostics.trace). Avec ces constantes définies, les méthodes de classe Debug et Trace génèrent un résultat dans la fenêtre [Sortie](../ide/reference/output-window.md). Sans ces constantes, les méthodes de classe Debug et Trace ne sont pas compilées et aucun résultat n’est généré.<br /><br />En règle générale, DEBUG est défini dans la version Debug d’une build et non défini dans la version Release. La TRACE est définie à la fois dans les versions Debug et Release.|
|**Général**  >  **Optimiser le code**|Si un bogue n’apparaît que dans le code optimisé, laissez ce paramètre désélectionné pour les versions Debug. Le code optimisé est plus difficile à déboguer, car les instructions ne correspondent pas directement aux instructions dans le code source.|
|**Sortie**  >  **Chemin de sortie**|Est généralement défini sur *bin\Debug* pour le débogage.|
|Bouton **avancé**|Pour plus d’informations sur les options de débogage avancées, consultez [paramètres de build avancés, boîte de dialogue (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Le format portable des fichiers de symboles (*. pdb*) est un format multiplateforme récent pour les applications .net core.

## <a name="see-also"></a>Voir aussi
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)