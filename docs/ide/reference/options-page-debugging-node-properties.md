---
title: "Page Options, Débogage, propriétés de nœud | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba6bb51d32ea249ba573733babcb7c9ed0cf0dde
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="options-page-debugging-node-properties"></a>Page Options, Débogage, propriétés de nœud
Les tableaux suivants décrivent les pages (ou collections de propriétés) associées à la catégorie **Débogage**, `DTE.Properties("Debugging", <Property Page>)`, de la boîte de dialogue **Options**.  
  
## <a name="general"></a>Général  
 `DTE.Properties("Debugging", "General")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|------------------------|-----------|-----------------|  
|PromptOnBreakpointDelete|Get/Set (booléen)|Détermine si le débogueur demande l’autorisation avant de supprimer tous les points d’arrêt dans un projet.|  
|BreakAllProcesses|Get/Set (booléen)|Détermine si le débogueur interrompt tous les processus quand un processus s’arrête.|  
|BreakAtBoundaries|Get/Set (booléen)|Détermine si le débogueur interrompt l’exécution quand une exception franchit une limite entre des domaines d’application ou entre un code managé et un code natif.|  
|EnableAddressLevelDebugging|Get/Set (booléen)|Détermine si les fonctionnalités de débogage au niveau des adresses sont activées.|  
|ShowDisassemblyIfNoSource|Get/Set (booléen)|Détermine si le débogueur affiche le code de désassemblage quand le code source n’est pas disponible.|  
|EnableBreakpointFilters|Get/Set (booléen)|Détermine si le filtrage de point d’arrêt est activé.|  
|EnableExceptionAssistant|Get/Set (booléen)|Détermine si l’Assistant Exception est utilisé pour les exceptions managées.|  
|UnwindCallstack|Get/Set (booléen)|Détermine si le débogueur déroule la pile des appels pour une exception non prise en charge.|  
|EnableJustMyCode|Get/Set (booléen)|Détermine si Uniquement mon code est activé pour le code C# et Visual Basic.|  
|ShowAllMembers|Get/Set (booléen)|Pour les objets non-utilisateur, détermine si le débogueur affiche tous les membres de l’objet dans les fenêtres de variables. Cette option n’a d’effet que si Uniquement mon code est activé.|  
|WarnIfNoUserCode|Get/Set (booléen)|Détermine si le débogueur émet un avertissement quand l’utilisateur tente de s’attacher à un processus qui n’a aucun code utilisateur. Cette option n’a d’effet que si Uniquement mon code est activé.|  
|EnablePropertyEvaluation|Get/Set (booléen)|Détermine si le débogueur évalue automatiquement les propriétés et les appels de fonction implicites dans le code managé.|  
|CallStringConversion|Get/Set (booléen)|Détermine si le débogueur appelle implicitement une fonction de conversion de chaîne sur des objets dans les fenêtres de variables. Cette option s’applique au code C# et JScript uniquement.|  
|EnableSourceServer|Get/Set (booléen)|Détermine si le débogueur peut accéder au code à partir d’un serveur source.|  
|PrintSourceServerDiagnostics|Get/Set (booléen)|Détermine si la fenêtre Sortie affiche les messages de diagnostic relatifs au serveur source. Cette option n’a d’effet que si l’accès au serveur source est activé.|  
|HighlightEntireLine|Get/Set (booléen)|Détermine si le débogueur met en surbrillance une ligne entière pour les points d’arrêt et l’instruction actuelle.|  
|RequireSourceToMatch|Get/Set (booléen)|Détermine si le débogueur requiert que les fichiers sources correspondent exactement à la version d’origine quand vous ouvrez des fichiers à des fins de débogage.|  
|RedirectOutputToImmediate|Get/Set (booléen)|Détermine si la fenêtre Sortie est redirigée vers la fenêtre Exécution.|  
|ShowRawVariableStructure|Get/Set (booléen)|Détermine si les objets dans les fenêtres de variables sont affichés sous une forme brute.|  
|SuppressJitOptimization|Get/Set (booléen)|Pour le code managé, détermine si l’optimisation juste-à-temps est supprimée par le débogueur.|  
|WarnIfNoSymbols|Get/Set (booléen)|Détermine si le débogueur affiche un avertissement si aucun symbole de débogage n’est disponible quand un processus est exécuté.|  
|WarnIfScriptDisabled|Get/Set (booléen)|Détermine si le débogueur affiche un avertissement si le débogage de script n’est pas activé quand un processus est exécuté.|  
|ShowMarkersForAllThreads|Get/Set (booléen)|Détermine si le débogueur affiche des marqueurs de thread.|  
|StepOverPropertiesAndOperators|Get/Set (booléen)|Spécifie si un pas à pas principal doit être effectué sur les propriétés et les opérateurs dans le code managé uniquement.|  
  
## <a name="edit-and-continue"></a>Modifier & Continuer  
 `DTE.Properties("Debugging", "EditAndContinue")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|------------------------|-----------|-----------------|  
|EnableEditAndContinue|Get/Set (booléen)|Détermine si Modifier & Continuer est activé. Cette option s’applique à tous les langages qui prennent en charge Modifier & Continuer.|  
|InvokedByCommands|Get/Set (booléen)|Détermine si Modifier & Continuer applique automatiquement les modifications du code quand l’utilisateur sélectionne une commande de débogage comme **Exécuter pas à pas** ou **Continuer**. Cette option s’applique uniquement au code natif.|  
|InvokedByCommandsAskFirst|Get/Set (booléen)|Détermine si Modifier & Continuer demande à l’utilisateur la permission d’appliquer les modifications du code quand il sélectionne une commande de débogage comme **Exécuter pas à pas** ou **Continuer**. Cette option s’applique uniquement au code natif.|  
|WarnAboutStaleCode|Get/Set (booléen)|Détermine si le débogueur émet un message d’avertissement si Modifier & Continuer est susceptible d’entraîner l’exécution d’un code obsolète ou périmé. Cette option s’applique uniquement au code natif.|  
|RelinkChangesOnStop|Get/Set (Short)|Détermine si Visual Studio reconstruit les modifications de code appliquées par Modifier & Continuer quand l’exécution de l’application s’arrête. Cette option s’applique uniquement au code natif.|  
|AllowPrecompiling|Get/Set (Short)|Détermine si Modifier & Continuer est autorisé à charger des en-têtes précompilés en arrière-plan. Cette option s’applique uniquement au code natif.|  
  
## <a name="just-in-time"></a>Juste-à-temps  
 `DTE.Properties("Debugging", "JustInTime")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|------------------------|-----------|-----------------|  
|JitManaged|Get/Set (booléen)|Détermine si le débogage juste-à-temps est activé pour le code managé.|  
|JitNative|Get/Set (booléen)|Détermine si le débogage juste-à-temps est activé pour le code natif.|  
|JitScript|Get/Set (booléen)|Détermine si le débogage juste-à-temps est activé pour le code de script.|  
  
## <a name="native"></a>Natif  
 `DTE.Properties("Debugging", "Native")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|------------------------|-----------|-----------------|  
|LoadDllExports|Get/Set (booléen)|Détermine si le débogueur charge les tables d’exportation de DLL.|  
|EnableRPC|Get/Set (booléen)|Détermine si le débogueur peut accéder aux appels de procédure distante COM.|  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle des paramètres de la boîte de dialogue Options](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Détermination des noms d’éléments de propriété dans les pages Options](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Page Options, Propriétés du nœud Polices et couleurs](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Page Options, Propriétés du nœud Éditeur de texte](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md)   
 [Modifier & Continuer, Débogage, Boîte de dialogue Options](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)   
 [Juste-à-temps, Débogage, boîte de dialogue Options](../../debugger/just-in-time-debugging-options-dialog-box.md)