---
title: "Param&#232;tres de projet pour des configurations Debug&#160;C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "versions debug, paramètres de projet"
  - "configurations de débogage, C#"
  - "configurations de débogage, J#"
  - "déboguer (C#), paramètres du débogueur"
  - "déboguer (J#), paramètres du débogueur"
  - "configurations de projet, déboguer"
  - "paramètres du projet (Visual Studio), configurations de débogage"
  - "projets (Visual Studio), configurations de débogage"
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Param&#232;tres de projet pour des configurations Debug&#160;C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez modifier les paramètres de projet d'une configuration Debug C\# dans la fenêtre **Pages de propriétés**, comme indiqué dans [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  Les tableaux suivants indiquent où se trouvent les paramètres du débogueur dans la fenêtre **Pages de propriétés**.  
  
> [!WARNING]
>  Cette rubrique ne s'applique pas aux applications Windows Store.  [Démarrer une session de débogage \(VB, C\#, C\+\+ et XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Onglet Déboguer  
  
|**Paramètre**|**Description**|  
|-------------------|---------------------|  
|**Configuration**|Définit le mode de compilation de l'application.  Choisissez parmi **Active \(Debug\)**, **Debug**, **Release** ou **Toutes les configurations**.|  
|**Action de démarrage**|Ce groupe de contrôles spécifie l'action exécutée lorsque vous cliquez dans le menu Déboguer sur Démarrer.<br /><br /> -   **Démarrer le projet**, qui est l'option par défaut, lance le projet de démarrage pour le débogage.  Pour plus d'informations, consultez [Choix du projet de démarrage](http://msdn.microsoft.com/fr-fr/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Démarrer le programme externe** permet de démarrer et d'attacher un programme qui ne fait pas partie d'un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations, consultez [Attachement à un programme en cours d'exécution](http://msdn.microsoft.com/fr-fr/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Démarrer l'URL** vous permet de déboguer une application Web.|  
|**Arguments de la ligne de commande**|Spécifie les arguments de la ligne de commande pour le programme à déboguer.  Le nom de la commande correspond au nom du programme spécifié dans Démarrer le programme externe.  Si Action de démarrage a la valeur Démarrer l'URL, les arguments de la ligne de commande ne peuvent pas être spécifiés.|  
|**Répertoire de travail**|Spécifie le répertoire de travail du programme en cours de débogage.  En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], le répertoire de travail est celui à partir duquel l'application est lancée : \\bin\\debug par défaut.|  
|**Utiliser l'ordinateur distant**|Nom d'un ordinateur distant où l'application s'exécutera pour des raisons liées au débogage ou [nom de serveur Msvsmon](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  L'emplacement du fichier EXE sur l'ordinateur distant est spécifié par la propriété Chemin de sortie dans le dossier Propriétés de configuration, catégorie Générer.  L'emplacement doit être un répertoire pouvant être partagé de l'ordinateur distant.|  
|**Activer le débogage de code non managé**|Vous permet de déboguer les appels au code Win32 natif \(non managé\) à partir de votre application managée.|  
|**Activer le débogage SQL Server**|Autorise le débogage d'objets de base de données SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Onglet Générer  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Symboles de compilation conditionnelle :**|Les constantes DEBUG et TRACE sont définies ici.<br /><br /> Ces constantes activent la compilation conditionnelle de la [classe Debug](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx) et de la [classe Trace](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx).  Lorsque ces constantes sont définies, les méthodes de classe Debug et Trace génèrent un résultat vers la [fenêtre Sortie](../ide/reference/output-window.md).  Sans ces constantes, les méthodes de classe Debug et Trace ne sont pas compilées et aucun résultat n'est généré.<br /><br /> -   Debug est normalement défini dans la version Debug d'un programme, mais n'est pas défini dans la version Release.<br />-   Trace est normalement défini dans les versions Debug et Release.|  
|**Optimiser le code**|À moins que vous ne trouviez un bogue qui n'apparaît que dans le code optimisé, il est conseillé de laisser ce paramètre désactivé dans la version Debug.  Le code optimisé est plus difficile à déboguer, car les instructions ne correspondent pas directement à celles de vos fenêtres sources.|  
|**Chemin de sortie :**|La valeur est généralement bin\\Debug pour le débogage.|  
  
## Voir aussi  
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)