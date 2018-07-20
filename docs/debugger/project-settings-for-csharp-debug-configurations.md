---
title: Paramètres pour les Configurations Debug c# du projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 043bd6e2c97ad3785ab783456fc911334d3d6cd0
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153687"
---
# <a name="project-settings-for--c-debug-configurations"></a>Paramètres de projet pour des configurations Debug C#
Vous pouvez modifier les paramètres du projet pour une configuration debug c# dans le **Pages de propriétés** fenêtre, comme indiqué dans [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md). Les tableaux suivants indiquent où trouver les paramètres du débogueur dans le **Pages de propriétés** fenêtre.  
  
> [!WARNING]
>  Cette rubrique ne s’applique pas aux applications UWP. Consultez [démarrer une session de débogage (VB, c#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Onglet déboguer  
  
|**Paramètre**|**Description**|  
|-----------------|---------------------|  
|**Configuration**|Définit le mode de compilation de l'application. Choisissez parmi **Active (Debug)**, **déboguer**, **version**, **toutes les Configurations**.|  
|**Action de démarrage**|Ce groupe de contrôles spécifie l'action exécutée lorsque vous cliquez dans le menu Déboguer sur Démarrer.<br /><br /> -   **Démarrer le projet** est la valeur par défaut, lance le projet de démarrage pour le débogage. Pour plus d’informations, consultez [choisir le projet de démarrage](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Démarrer le programme externe** vous permet de démarrer et d’attacher à un programme qui n’est pas dans le cadre d’un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet. Pour plus d’informations, consultez [attachement à un programme en cours d’exécution](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Démarrer l’URL** vous permet de déboguer une application Web.|  
|**Arguments de la ligne de commande**|Spécifie les arguments de la ligne de commande pour le programme à déboguer. Le nom de la commande correspond au nom du programme spécifié dans Démarrer le programme externe. Si Action de démarrage a la valeur Démarrer l’URL, les arguments de la ligne de commande ne peuvent pas être spécifiés.|  
|**Répertoire de travail**|Spécifie le répertoire de travail du programme en cours de débogage. En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], le répertoire de travail est celui à partir duquel l'application est lancée : \bin\debug par défaut.|  
|**Utiliser l’ordinateur distant**|Le nom d’un ordinateur distant où l’application s’exécutera à des fins de débogage ou un [nom de serveur Msvsmon](../debugger/remote-debugging.md). L’emplacement du fichier EXE sur l’ordinateur distant est spécifié par la propriété Chemin de sortie dans le dossier Propriétés de configuration, catégorie Générer. L'emplacement doit être un répertoire pouvant être partagé de l'ordinateur distant.|
|**Activer le débogage de code non managé**|Vous permet de déboguer les appels au code Win32 natif (non managé) à partir de votre application managée.|  
|**Activer le débogage SQL Server**|Autorise le débogage d'objets de base de données SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Onglet Générer  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Symboles de compilation conditionnelle :**|Les constantes DEBUG et TRACE sont définies ici.<br /><br /> Ces constantes activent la compilation conditionnelle de la [classe Debug](/dotnet/api/system.diagnostics.debug) et [classe Trace](/dotnet/api/system.diagnostics.trace). Avec ces constantes sont définies, déboguer et méthodes de classe Trace génèrent un résultat vers la [fenêtre sortie](../ide/reference/output-window.md). Sans ces constantes, les méthodes de classe Debug et Trace ne sont pas compilées et aucun résultat n'est généré.<br /><br /> -Debug est normalement défini dans la version Debug d’un programme et non défini dans la version Release.<br />-Trace est normalement défini dans les versions Debug et Release.|  
|**Optimiser le code**|À moins que vous ne trouviez un bogue qui n'apparaît que dans le code optimisé, il est conseillé de laisser ce paramètre désactivé dans la version Debug. Le code optimisé est plus difficile à déboguer, car les instructions ne correspondent pas directement à celles de vos fenêtres sources.|  
|**Chemin de sortie :**|La valeur est généralement bin\Debug pour le débogage.|

> [!NOTE]
> Pour plus d’informations sur les options de débogage vous trouver dans le **avancé** bouton, consultez [boîte de dialogue Paramètres de génération avancés (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Le format portable pour les fichiers de symboles (.pdb) est le format inter-plateformes plus récent pour .NET Core. 
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)