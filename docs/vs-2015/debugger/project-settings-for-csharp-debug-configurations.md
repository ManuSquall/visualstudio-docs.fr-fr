---
title: Paramètres de projet pour les configurations de débogage C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f1ec1c18fe92409a72994e4544215da01325d209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687518"
---
# <a name="project-settings-for--c-debug-configurations"></a>Paramètres de projet pour des configurations Debug C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier les paramètres du projet pour une configuration Debug C# dans la fenêtre **pages de propriétés** , comme indiqué dans [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Les tableaux suivants indiquent où se trouvent les paramètres du débogueur dans la fenêtre **Pages de propriétés**.  
  
> [!WARNING]
> Cette rubrique ne s'applique pas aux applications Windows Store. Consultez [Démarrer une session de débogage (VB, C#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
## <a name="debug-tab"></a><a name="BKMK_Debug_tab"></a> Onglet débogage  
  
|**Paramètre**|**Description**|  
|-----------------|---------------------|  
|**Configuration**|Définit le mode de compilation de l'application. Choisissez parmi **Active (Debug)**, **Debug**, **Release** ou **Toutes les configurations**.|  
|**Action de démarrage**|Ce groupe de contrôles spécifie l'action exécutée lorsque vous cliquez dans le menu Déboguer sur Démarrer.<br /><br /> -   **Démarrer le projet**, qui est l’option par défaut, lance le projet de démarrage pour le débogage. Pour plus d’informations, consultez [choix du projet de démarrage](https://msdn.microsoft.com/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Démarrer le programme externe** permet de démarrer et d’attacher un programme qui ne fait pas partie d’un projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pour plus d’informations, consultez [attachement à un programme en cours d’exécution](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Démarrer le navigateur avec l’URL** vous permet de déboguer une application web.|  
|**Arguments de ligne de commande**|Spécifie les arguments de la ligne de commande pour le programme à déboguer. Le nom de la commande correspond au nom du programme spécifié dans Démarrer le programme externe. Si Action de démarrage a la valeur Démarrer l'URL, les arguments de la ligne de commande ne peuvent pas être spécifiés.|  
|**Répertoire de travail**|Spécifie le répertoire de travail du programme en cours de débogage. En [!INCLUDE[csprcs](../includes/csprcs-md.md)], le répertoire de travail est celui à partir duquel l'application est lancée : \bin\debug par défaut.|  
|**Utiliser l’ordinateur distant**|Nom d’un ordinateur distant sur lequel l’application sera exécutée à des fins de débogage ou un [nom de serveur Msvsmon](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). L'emplacement du fichier EXE sur l'ordinateur distant est spécifié par la propriété Chemin de sortie dans le dossier Propriétés de configuration, catégorie Générer. L'emplacement doit être un répertoire pouvant être partagé de l'ordinateur distant.|  
|**Activer le débogage de code non managé**|Vous permet de déboguer les appels au code Win32 natif (non managé) à partir de votre application managée.|  
|**Activer le débogage SQL Server**|Autorise le débogage d'objets de base de données SQL Server.|  
  
## <a name="build-tab"></a><a name="BKMK_Build_tab"></a> Onglet générer  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Symboles de compilation conditionnelle :**|Les constantes DEBUG et TRACE sont définies ici.<br /><br /> Ces constantes activent la compilation conditionnelle de la [classe Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) et de la [classe Trace](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Avec ces constantes définies, les méthodes de classe Debug et Trace génèrent un résultat dans la fenêtre [Sortie](../ide/reference/output-window.md). Sans ces constantes, les méthodes de classe Debug et Trace ne sont pas compilées et aucun résultat n'est généré.<br /><br /> -Debug est normalement défini dans la version Debug d’un programme et n’est pas défini dans la version Release.<br />-Trace est normalement défini à la fois dans les versions Debug et Release.|  
|**Optimiser le code**|À moins que vous ne trouviez un bogue qui n'apparaît que dans le code optimisé, il est conseillé de laisser ce paramètre désactivé dans la version Debug. Le code optimisé est plus difficile à déboguer, car les instructions ne correspondent pas directement à celles de vos fenêtres sources.|  
|**Chemin de sortie :**|La valeur est généralement bin\Debug pour le débogage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
