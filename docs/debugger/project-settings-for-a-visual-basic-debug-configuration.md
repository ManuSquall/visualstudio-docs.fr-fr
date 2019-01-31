---
title: Paramètres de projet pour VB debug config | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2f8315717b91a257d09b5de671698796f732543
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004732"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Paramètres de projet pour une configuration Debug Visual Basic
Vous pouvez modifier les paramètres de projet d’une configuration Debug [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] dans la fenêtre **Pages de propriétés**, comme indiqué dans [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Les tableaux suivants indiquent où se trouvent les paramètres du débogueur dans la fenêtre **Pages de propriétés**.  
  
> [!WARNING]
>  Cette rubrique ne s’applique pas aux applications UWP. Consultez [démarrer une session de débogage (VB, C#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Onglet Déboguer  
  
| Paramètre | Description |
|------------------------------| - |
| **Configuration** | Définit le mode de compilation de l'application. Choisissez parmi **Active (Debug)**, **Debug**, **Release** ou **Toutes les configurations**. |
| **Action de démarrage** | Ce groupe de contrôles spécifie l'action exécutée lorsque vous cliquez dans le menu Déboguer sur Démarrer.<br /><br /> -   **Démarrer le projet**, qui est l’option par défaut, lance le projet de démarrage pour le débogage. <br />-   **Démarrer le programme externe** permet de démarrer et d’attacher un programme qui ne fait pas partie d’un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Démarrer le navigateur avec l’URL** vous permet de déboguer une application web. |
| **Arguments de la ligne de commande** | Spécifie les arguments de la ligne de commande pour le programme à déboguer. Le nom de la commande correspond au nom du programme spécifié dans Démarrer le programme externe. Si Action de démarrage prend la valeur Démarrer l’URL, les arguments de la ligne de commande sont ignorés. |
| **Répertoire de travail** | Spécifie le répertoire de travail du programme en cours de débogage. En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], le répertoire de travail est celui à partir duquel l'application est lancée. Le répertoire de travail par défaut est \bin\Debug ou \bin\Release, en fonction de la configuration actuelle. |
| **Utiliser l’ordinateur distant** | Lorsque la case à cocher est activée, le débogage à distance est activé. Dans la zone de texte, vous pouvez taper le nom d’un ordinateur distant où l’application s’exécutera pour des raisons liées au débogage ou un [nom de serveur Msvsmon](../debugger/remote-debugging.md). L’emplacement du fichier EXE sur l’ordinateur distant est spécifié par la propriété Chemin de sortie dans l’onglet Générer. L'emplacement doit être un répertoire pouvant être partagé de l'ordinateur distant. |
| **Débogage de code non managé** | Vous permet de déboguer les appels au code Win32 natif (non managé) à partir de votre application managée. Cette action revient à sélectionner Mixte comme Type de débogueur dans un projet [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. |
| **Débogage SQL Server** | Autorise le débogage d'objets de base de données SQL Server. |
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Onglet Compiler : appuyer sur le bouton Options avancées de compilation  
  
| Paramètre | Description |
|---------------------------| - |
| **Activer les optimisations** | Cette option doit être désactivée. L'optimisation fait en sorte que le code réellement exécuté soit différent du code source vu dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ce qui rend donc le débogage difficile. Si le code est optimisé, les symboles ne sont pas chargés par défaut lors du débogage si l'option Uniquement mon code est activée. |
| **Générer des infos de débogage** | Défini par défaut dans les versions Debug et Release, ce paramètre (équivalent à l’option /debug du compilateur) crée des informations de débogage au moment de la génération. Le débogueur utilise ces informations pour afficher les noms de variables ainsi que d'autres informations sous une forme pratique au cours du débogage. Si vous compilez votre programme sans ces informations, la fonctionnalité du débogueur sera limitée. Pour plus d’informations, consultez [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **Définir la constante DEBUG** | La définition de ce symbole active la compilation conditionnelle des fonctions de sortie à partir de la [classe Debug](/dotnet/api/system.diagnostics.debug). Quand ce symbole est défini, les méthodes de classe Debug génèrent un résultat vers la [fenêtre Sortie](../ide/reference/output-window.md). Sans ce symbole, les méthodes de classe Debug ne sont pas compilées et aucun résultat n'est généré. Ce symbole doit être défini dans la version Debug, mais pas dans la version Release. La définition de ce symbole dans une version Release crée un code superflu qui ralentit votre programme. |
| **Définir la constante TRACE** | La définition de ce symbole active la compilation conditionnelle des fonctions de sortie à partir de la [classe Trace](/dotnet/api/system.diagnostics.trace). Quand ce symbole est défini, les méthodes de classe Trace génèrent un résultat vers la [fenêtre Sortie](../ide/reference/output-window.md). Sans ce symbole, les méthodes de classe Trace ne sont pas compilées et aucun résultat Trace n'est généré. Ce symbole est défini par défaut pour les versions Debug et Release. |
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)