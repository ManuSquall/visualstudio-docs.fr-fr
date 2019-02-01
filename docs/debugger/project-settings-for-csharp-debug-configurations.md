---
title: Paramètres de projets pour un C# déboguer config | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 77fa0d60c4c702e2594121d5db54bf6c5e7cc6f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005967"
---
# <a name="project-settings-for--c-debug-configurations"></a>Paramètres de projet pour des configurations Debug C#

Vous pouvez modifier C# projet des paramètres de débogage dans le [onglet débogage](#debug-tab) et [onglet Build](#build-tab) des pages de propriétés de projet. 

Pour ouvrir les pages de propriétés, sélectionnez le projet dans **l’Explorateur de solutions** , puis sélectionnez le **propriétés** icône, ou cliquez sur le projet et sélectionnez **propriétés**.

Pour plus d’informations, consultez [Configurations Debug et Release](how-to-set-debug-and-release-configurations.md). 

>[!IMPORTANT]
>Ces paramètres ne s’appliquent aux applications .NET Core, ASP.NET ou UWP. Pour configurer les paramètres de débogage pour les applications UWP, consultez [démarrer une session de débogage pour une application UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
## <a name="debug-tab"></a>Onglet Déboguer  
  
|Paramètre|Description|
|-------------------------------------| - |
| **Configuration** | Définit le mode de création de l’application. Sélectionnez **Active (Debug)**, **déboguer**, **version**, ou **toutes les Configurations** dans la liste déroulante. |
| **Action de démarrage** | Spécifie l’action lorsque vous sélectionnez **Démarrer** dans une configuration Debug.<br />- **Démarrer le projet**, qui est l’option par défaut, lance le projet de démarrage pour le débogage. Pour plus d’informations, consultez [choisir le projet de démarrage](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Démarrer le programme externe** démarre et s’attache à une application qui n’est pas dans le cadre d’un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet. Pour plus d’informations, consultez [attacher au processus en cours d’exécution avec le débogueur](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Démarrer le navigateur avec URL** vous permet de déboguer une application web. |
| **Options de démarrage** > **des arguments de ligne de commande** | Spécifie les arguments de ligne de commande pour l’application en cours de débogage. Le nom de commande est le nom d’application spécifié dans **démarrer le programme externe**. |
| **Options de démarrage** > **répertoire de travail** | Spécifie le répertoire de travail de l’application en cours de débogage. Dans C#, le répertoire de travail est *\bin\debug* par défaut.
| **Options de démarrage** > **utiliser l’ordinateur distant**|Pour le débogage distant, sélectionnez cette option et entrez le nom de la cible de débogage à distance, ou un [nom de serveur Msvsmon](../debugger/remote-debugging.md). <br />L’emplacement d’une application sur l’ordinateur distant est spécifié par le **chemin de sortie** propriété sur le **Build** onglet. L'emplacement doit être un répertoire pouvant être partagé de l'ordinateur distant. 
| **Moteur du débogueur** > **activer le débogage de code non managé** | Débogue les appels pour le code Win32 natif (non managé) à partir de l’application gérée. |
| **Moteur du débogueur** > **débogage activer SQL Server** | Débogue les objets de base de données SQL Server. |
  
## <a name="build-tab"></a>Onglet Générer  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Général** > **symboles de compilation conditionnelle**|Définissez les constantes DEBUG et TRACE si sélectionné.<br /><br /> Ces constantes activent la compilation conditionnelle de la [classe Debug](/dotnet/api/system.diagnostics.debug) et de la [classe Trace](/dotnet/api/system.diagnostics.trace). Avec ces constantes définies, les méthodes de classe Debug et Trace génèrent un résultat dans la fenêtre [Sortie](../ide/reference/output-window.md). Sans ces constantes, les méthodes de classe Debug et Trace ne sont pas compilées et aucun résultat n’est généré.<br /><br />En règle générale, DEBUG est défini dans la version Debug d’une build et non défini dans la version Release. TRACE est défini dans les versions Debug et Release.|  
|**Général** > **optimiser le code**|Sauf si un bogue s’affiche uniquement dans le code optimisé, laissez ce paramètre désélectionnées pour les versions Debug. Code optimisé est plus difficile à déboguer, car les instructions ne correspondent pas directement aux instructions dans le code source.|  
|**Sortie** > **chemin de sortie**|La valeur est généralement *bin\Debug* pour le débogage.|
|**Advanced** bouton|Pour plus d’informations sur les options de débogage avancées, consultez [boîte de dialogue Paramètres de génération avancés (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Le format portable pour le symbole (*.pdb*) fichiers est un format inter-plateformes récentes pour les applications .NET Core. 
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)