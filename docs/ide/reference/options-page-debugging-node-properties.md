---
title: "Page Options, D&#233;bogage, propri&#233;t&#233;s de nœud | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Page Options, D&#233;bogage, propri&#233;t&#233;s de nœud
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le tableau suivant décrit les pages \(ou les collections de propriétés\) associées à la catégorie **Débogage**, `DTE.Properties("Debugging", <Property Page>)` de la boîte de dialogue **Options**.  
  
## Général  
 `DTE.Properties("Debugging", "General")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|-----------------------------------|------------|-----------------|  
|PromptOnBreakpointDelete|Get\/Set \(booléen\)|Détermine si le débogueur demande confirmation avant de supprimer tous les points d'arrêt d'un projet.|  
|BreakAllProcesses|Get\/Set \(booléen\)|Détermine si le débogueur arrête tous les processus chaque fois qu'un processus s'arrête.|  
|BreakAtBoundaries|Get\/Set \(booléen\)|Détermine si le débogueur arrête l'exécution lorsqu'une exception franchit une frontière entre AppDomains ou entre code managé et code natif.|  
|EnableAddressLevelDebugging|Get\/Set \(booléen\)|Détermine si les fonctionnalités de débogage au niveau de l'adresse sont activées.|  
|ShowDisassemblyIfNoSource|Get\/Set \(booléen\)|Détermine si le débogueur affiche le code machine lorsque le code source n'est pas disponible.|  
|EnableBreakpointFilters|Get\/Set \(booléen\)|Détermine si le filtrage des points d'arrêt est activé.|  
|EnableExceptionAssistant|Get\/Set \(booléen\)|Détermine si l'Assistant Exception est utilisé pour les exceptions managées.|  
|UnwindCallstack|Get\/Set \(booléen\)|Détermine si le débogueur déroule la pile des appels d'une exception non gérée.|  
|EnableJustMyCode|Get\/Set \(booléen\)|Détermine si Uniquement mon code est activé pour le code C\# et le code Visual Basic.|  
|ShowAllMembers|Get\/Set \(booléen\)|Pour les objets non\-utilisateur, détermine si le débogueur affiche tous les membres objets dans les fenêtres de variables.  Cette option n'a aucun effet si la fonctionnalité Uniquement mon code n'est pas activée.|  
|WarnIfNoUserCode|Get\/Set \(booléen\)|Détermine si le débogueur émet un avertissement lorsque l'utilisateur essaie d'attacher un processus qui n'a aucun code utilisateur.  Cette option n'a aucun effet si la fonctionnalité Uniquement mon code n'est pas activée.|  
|EnablePropertyEvaluation|Get\/Set \(booléen\)|Détermine si le débogueur évalue automatiquement des propriétés et des appels de fonction implicite en code managé.|  
|CallStringConversion|Get\/Set \(booléen\)|Détermine si le débogueur appelle implicitement une fonction de conversion de chaînes sur des objets dans les fenêtres de variables.  Cette option s'applique uniquement au code C\# et JScript.|  
|EnableSourceServer|Get\/Set \(booléen\)|Détermine si le débogueur peut accéder au code à partir d'un serveur source.|  
|PrintSourceServerDiagnostics|Get\/Set \(booléen\)|Détermine si la fenêtre Sortie affiche des messages de diagnostic relatifs au serveur source.  Cette option n'a aucun effet si l'accès au serveur source n'est pas activé.|  
|HighlightEntireLine|Get\/Set \(booléen\)|Détermine si le débogueur met en surbrillance une ligne entière pour les points d'arrêt et l'instruction en cours.|  
|RequireSourceToMatch|Get\/Set \(booléen\)|Détermine si le débogueur exige que les fichiers sources correspondent exactement à la version d'origine lorsque vous ouvrez des fichiers pour effectuer un débogage.|  
|RedirectOutputToImmediate|Get\/Set \(booléen\)|Détermine si le résultat de la fenêtre Sortie est redirigé vers la fenêtre Exécution.|  
|ShowRawVariableStructure|Get\/Set \(booléen\)|Détermine si les objets qui figurent dans les fenêtres de variables sont affichés à l'état brut.|  
|SuppressJitOptimization|Get\/Set \(booléen\)|Pour le code managé, détermine si l'optimisation juste\-à\-temps est supprimée par le débogueur.|  
|WarnIfNoSymbols|Get\/Set \(booléen\)|Détermine si le débogueur affiche un avertissement lorsque aucun symbole de débogage n'est disponible au lancement d'un processus.|  
|WarnIfScriptDisabled|Get\/Set \(booléen\)|Détermine si le débogueur affiche un avertissement lorsque le débogage de script n'est pas activé au lancement d'un processus.|  
|ShowMarkersForAllThreads|Get\/Set \(booléen\)|Détermine si le débogueur affiche des marqueurs de thread.|  
|StepOverPropertiesAndOperators|Get\/Set \(booléen\)|Spécifie s'il faut ignorer les propriétés et les opérateurs en code managé uniquement.|  
  
## Modifier & Continuer  
 `DTE.Properties("Debugging", "EditAndContinue")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|-----------------------------------|------------|-----------------|  
|EnableEditAndContinue|Get\/Set \(booléen\)|Détermine si Modifier & Continuer est activé.  Cette option s'applique à tous les langages qui prennent en charge Modifier & Continuer.|  
|InvokedByCommands|Get\/Set \(booléen\)|Détermine si Modifier & Continuer applique automatiquement des modifications au code lorsque l'utilisateur sélectionne une commande de débogage telle que **Étape** ou **Continuer**.  Cette option s'applique uniquement au code natif.|  
|InvokedByCommandsAskFirst|Get\/Set \(booléen\)|Détermine si Modifier & Continuer invite l'utilisateur à confirmer l'application de modifications au code lorsque l'utilisateur sélectionne une commande de débogage telle que **Étape** ou **Continuer**.  Cette option s'applique uniquement au code natif.|  
|WarnAboutStaleCode|Get\/Set \(booléen\)|Détermine si le débogueur émet un message d'avertissement lorsque Modifier & Continuer risque d'exécuter du code obsolète ou périmé.  Cette option s'applique uniquement au code natif.|  
|RelinkChangesOnStop|Get\/Set \(Short\)|Détermine si Visual Studio reconstruit les modifications appliquées au code par Modifier & Continuer lorsque l'exécution de l'application s'arrête.  Cette option s'applique uniquement au code natif.|  
|AllowPrecompiling|Get\/Set \(Short\)|Détermine si Modifier & Continuer est autorisé à charger des en\-têtes précompilés en arrière\-plan.  Cette option s'applique uniquement au code natif.|  
  
## Just\-In\-Time  
 `DTE.Properties("Debugging", "JustInTime")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|-----------------------------------|------------|-----------------|  
|JitManaged|Get\/Set \(booléen\)|Détermine si Débogage juste\-à\-temps est activé pour le code managé.|  
|JitNative|Get\/Set \(booléen\)|Détermine si Débogage juste\-à\-temps est activé pour le code natif.|  
|JitScript|Get\/Set \(booléen\)|Détermine si Débogage juste\-à\-temps est activé pour le code de script.|  
  
## Natif  
 `DTE.Properties("Debugging", "Native")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|-----------------------------------|------------|-----------------|  
|LoadDllExports|Get\/Set \(booléen\)|Détermine si le débogueur charge des tables d'exportation de DLL.|  
|EnableRPC|Get\/Set \(booléen\)|Détermine si le débogueur peut effectuer un pas à pas détaillé dans des appels de procédure distante COM.|  
  
## Voir aussi  
 [Contrôle des paramètres de la boîte de dialogue Options](../Topic/Controlling%20Options%20Settings.md)   
 [Détermination des noms d'éléments de propriété dans les pages Options](../Topic/Determining%20the%20Names%20of%20Property%20Items%20on%20Options%20Pages.md)   
 [Page Options, Polices et couleurs, propriétés de nœud](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Page Options, Éditeur de texte, propriétés de nœud](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md)   
 [Modifier & Continuer, Débogage, boîte de dialogue Options](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)   
 [Juste\-à\-temps, Débogage, boîte de dialogue Options](../../debugger/just-in-time-debugging-options-dialog-box.md)