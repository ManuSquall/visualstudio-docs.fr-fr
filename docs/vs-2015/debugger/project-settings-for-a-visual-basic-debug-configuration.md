---
title: Paramètres pour une Configuration de débogage Visual Basic du projet | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af9d9976c6aa6743cfda4c69d3b2f8d958ab03bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501659"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Paramètres de projet pour une configuration Debug Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [paramètres de projet pour une Configuration Debug Visual Basic](https://docs.microsoft.com/visualstudio/debugger/project-settings-for-a-visual-basic-debug-configuration).  
  
Vous pouvez modifier les paramètres du projet pour un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] configuration de débogage dans le **Pages de propriétés** fenêtre, comme indiqué dans [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Les tableaux suivants indiquent où trouver les paramètres du débogueur dans le **Pages de propriétés** fenêtre.  
  
> [!WARNING]
>  Cette rubrique ne s'applique pas aux applications Store. Consultez [démarrer une session de débogage (VB, c#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Onglet Déboguer  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Configuration**|Définit le mode de compilation de l'application. Choisissez parmi **Active (Debug)**, **déboguer**, **version**, **toutes les Configurations**.|  
|**Action de démarrage**|Ce groupe de contrôles spécifie l'action exécutée lorsque vous cliquez dans le menu Déboguer sur Démarrer.<br /><br /> -   **Démarrer le projet** est la valeur par défaut, lance le projet de démarrage pour le débogage. Pour plus d’informations, consultez [NIB Comment : définir les projets de démarrage](http://msdn.microsoft.com/en-us/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Démarrer le programme externe** vous permet de démarrer et d’attacher à un programme qui n’est pas dans le cadre d’un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projet. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Démarrer l’URL** vous permet de déboguer une application Web.|  
|**Arguments de ligne de commande**|Spécifie les arguments de la ligne de commande pour le programme à déboguer. Le nom de la commande correspond au nom du programme spécifié dans Démarrer le programme externe. Si Action de démarrage prend la valeur Démarrer l’URL, les arguments de la ligne de commande sont ignorés.|  
|**Répertoire de travail**|Spécifie le répertoire de travail du programme en cours de débogage. En [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], le répertoire de travail est celui à partir duquel l'application est lancée. Le répertoire de travail par défaut est \bin\Debug ou \bin\Release, en fonction de la configuration actuelle.|  
|**Utiliser l’ordinateur distant**|Lorsque la case à cocher est activée, le débogage à distance est activé. Dans la zone de texte, vous pouvez taper le nom d’un ordinateur distant où l’application s’exécutera à des fins de débogage ou un [nom de serveur Msvsmon](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). L’emplacement du fichier EXE sur l’ordinateur distant est spécifié par la propriété Chemin de sortie dans l’onglet Générer. L'emplacement doit être un répertoire pouvant être partagé de l'ordinateur distant.|  
|**Débogage de code non managé**|Vous permet de déboguer les appels au code Win32 natif (non managé) à partir de votre application managée. Cette action revient à sélectionner Mixte comme Type de débogueur dans un projet [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].|  
|**Le débogage SQL Server**|Autorise le débogage d'objets de base de données SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Onglet Compiler : appuyer sur le bouton Options avancées de compilation  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Activer les optimisations**|Cette option doit être désactivée. L'optimisation fait en sorte que le code réellement exécuté soit différent du code source vu dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ce qui rend donc le débogage difficile. Si le code est optimisé, les symboles ne sont pas chargés par défaut lors du débogage si l'option Uniquement mon code est activée.|  
|**Générer des infos de débogage**|Défini par défaut dans les versions Debug et Release, ce paramètre (équivalent à l’option /debug du compilateur) crée des informations de débogage au moment de la génération. Le débogueur utilise ces informations pour afficher les noms de variables ainsi que d'autres informations sous une forme pratique au cours du débogage. Si vous compilez votre programme sans ces informations, la fonctionnalité du débogueur sera limitée. Pour plus d’informations, consultez [/debug](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**Définir la constante DEBUG**|Définition de ce symbole active la compilation conditionnelle des fonctions de sortie à partir de la [classe Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx). Lorsque ce symbole est défini, les méthodes de classe Debug génèrent un résultat vers la [fenêtre sortie](../ide/reference/output-window.md). Sans ce symbole, les méthodes de classe Debug ne sont pas compilées et aucun résultat n'est généré. Ce symbole doit être défini dans la version Debug, mais pas dans la version Release. La définition de ce symbole dans une version Release crée un code superflu qui ralentit votre programme.|  
|**Définir la constante TRACE**|Définition de ce symbole active la compilation conditionnelle des fonctions de sortie à partir de la [classe Trace](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Lorsque ce symbole est défini, les méthodes de classe Trace génèrent un résultat vers la [fenêtre sortie](../ide/reference/output-window.md). Sans ce symbole, les méthodes de classe Trace ne sont pas compilées et aucun résultat Trace n'est généré. Ce symbole est défini par défaut pour les versions Debug et Release.|  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)



