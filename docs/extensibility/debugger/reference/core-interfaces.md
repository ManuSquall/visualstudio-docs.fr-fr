---
title: "Interfaces de base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), des interfaces de base"
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Interfaces de base
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Les interfaces suivantes sont les principales interfaces permettant d'étendre le débogueur à l'aide de [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## Discussion  
 ces interfaces sont principalement utilisées pour créer le moteur de débogage \(DE\).  Ils sont organisés ici par catégories :  
  
-   [Points d'arrêt](#Breakpoints)  
  
-   [contextes](#Contexts)  
  
-   [principal serveur](#CoreServer)  
  
-   [moteurs de débogage](#DebugEngines)  
  
-   [Documents](#Documents)  
  
-   [Événements](#Events)  
  
-   [expressions](#Expressions)  
  
-   [Mémoire](#Memory)  
  
-   [Modules](#Modules)  
  
-   [ports](#Ports)  
  
-   [Processus](#Processes)  
  
-   [Programmes](#Programs)  
  
-   [Propriétés](#Properties)  
  
-   [frames de pile](#StackFrames)  
  
-   [Threads](#Threads)  
  
-   [visualiseurs de type](#TypeVisualizers)  
  
 Les entités qui peuvent implémenter des interfaces sont :  
  
-   moteur de débogage \(DE\)  
  
-   fournisseur de port \(PS\)  
  
-   évaluateur d'expression \(EE\)  
  
-   Visual Studio \(VS\)  
  
##  <a name="Breakpoints"></a> Points d'arrêt  
 Ces interfaces sont liées à l'implémentation et au suivi des points d'arrêt.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Représente un point d'arrêt lié à un emplacement mémoire.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Envoyé par le De lorsqu'un point d'arrêt est lié à un emplacement mémoire.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Représente une somme de contrôle document pour une requête de point d'arrêt.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Envoyé par le De lorsqu'un point d'arrêt n'est pas à un emplacement mémoire.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Envoyé par le De lorsqu'un point d'arrêt est atteint.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|représente une demande d'un point d'arrêt ; utilisé en créant un point d'arrêt en attente.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|représente une demande d'un point d'arrêt ; utilisé en créant un point d'arrêt en attente.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|représente les informations utilisées pour lier un point d'arrêt.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Envoyé par le De lorsqu'un point d'arrêt est annulé la liaison d'un emplacement de mémoire.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Représente un point d'arrêt non valide \(retourné par `IDebugBreakpointErrorEvent2`\).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Représente les informations sur la résolution sur un point d'arrêt non valide.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Représente une position dans une fonction où un point d'arrêt.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|représente un point d'arrêt qui doit être lié ; utilisé en créant un point d'arrêt lié.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Représente une énumération sur un ensemble de points d'arrêt liés.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Représente une énumération sur un ensemble de points d'arrêt qui peuvent ne pas être liés à un emplacement mémoire.|  
  
##  <a name="Contexts"></a> contextes  
 Ces interfaces représentent plusieurs genres de contextes dans le programme débogué.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|représente la position de départ d'une instruction de code.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|étend l'interface d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) pour activer la récupération du module et des interfaces de processus.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, PG.PRÉC|représente une position dans un document.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Représente le contexte dans lequel évaluer une expression.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Représente l'emplacement à partir à la mémoire d'une collection d'octets.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Représente un contexte du frame de pile à un point d'arrêt ou une exception.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Représente un contexte du frame de pile à un point d'arrêt ou une exception.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Représente une énumération sur un ensemble de contextes de code.|  
  
##  <a name="CoreServer"></a> principal serveur  
 Ces interfaces représentent l'ordinateur sur lequel un programme est débogué.  Ceux\-ci sont implémentés par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] mais peuvent être appelés dans par les moteurs de débogage.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Fournit l'accès aux ports et aux fournisseurs de port ainsi que des informations concernant l'ordinateur.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|représente [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) qui prend en charge le débogage distant.|  
  
##  <a name="DebugEngines"></a> moteurs de débogage  
 ces interfaces représentent des moteurs de débogage et leurs événements associés.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|représente un moteur de débogage personnalisé.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|représente un moteur de débogage personnalisé qui prend en charge le chargement des symboles, du JustMyCode, et des exceptions.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Envoyé par chaque nouvelle instance De pour indiquer qu'il est prêt à gérer les tâches de débogage.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Représente un moteur de débogage personnalisé qui prend en charge exécuter les programmes.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DROITE, PICOSECONDE|Représente un nœud de programme qui gère plusieurs moteurs de débogage.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Permet que le SDM puisse obtenir une interface au moteur de débogage d'un thread, d'un programme, ou un frame de pile.|  
  
##  <a name="Documents"></a> Documents  
 ces interfaces représentent des documents \(fichiers sources\) et leurs éléments associés.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|envoyé par le De pour demander un document à ouvrir.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|représente un flux de données de l'instruction désassemblée d'un document.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, PG.PRÉC|Représente un document fourni par le De, en spécifiant le nom et l'ID de classe \(CLSID\).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DROITE, EE|Représente un checksum pour un document de débogage et permet de passer la somme de contrôle entre les composants.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, PG.PRÉC|Représente un contexte du document, une position dans un document qui correspond à une instruction particulière et le contexte de code.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, PG.PRÉC|représente une position générale dans un document.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Représente une position dans un fichier source comme un offset de caractère.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, PG.PRÉC|Représente un document texte fourni par le De \(dérivé d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\), en fournissant le texte réel.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Envoyé par le De pour spécifier les modifications apportées à un fichier source en mémoire.|  
  
##  <a name="Events"></a> Événements  
 Ces interfaces représentent tous les événements qui sont échangés entre le De et le gestionnaire de débogage de session \(SDM\).  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|envoyé par le De pour demander un document à ouvrir.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Le moteur \(DE\) de débogage envoie cette interface au gestionnaire de débogage de session \(SDM\) pour définir le message de barre d'état pendant le chargement du symbole.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Envoyé par le De lorsque l'interruption dans le programme a été effectué.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Envoyé par le De lorsqu'un point d'arrêt est lié.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Envoyé par le De lorsqu'un point d'arrêt n'est pas.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Envoyé par le De lorsqu'un point d'arrêt est atteint.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Envoyé par le De lorsqu'un point d'arrêt est annulé la liaison.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Envoyé par le De la pour déterminer s'il doit arrêter à un emplacement particulier.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Envoyé par le De pour spécifier les modifications apportées à un fichier source en mémoire.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Envoyé par chaque nouvelle instance De pour indiquer qu'il est prêt à gérer les tâches de débogage.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Envoyé par le De pour indiquer le programme débogué est prêt à exécuter la première instruction.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Une interface utilisée par d'autres interfaces d'événement, qui peuvent retourner une erreur, pour fournir des messages d'erreur explicites.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DROITE, PICOSECONDE|Interface de base dont toutes les autres interfaces d'événement sont dérivées.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Représente une interface implémentée par le SDM auquel les événements \(exprimées comme un des objets implémentant une interface d'événement particulière\) sont envoyés.|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Envoyé lors De l'exécution lorsqu'une exception s'est produite dans le programme débogué.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Envoyé par le De lorsqu'une évaluation de l'expression asynchrone est terminée.|  
|IDebugFindSymbolEvent2||OBSOLÈTE.  NE SUR UTILISEZ NOT.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Envoyé par le De lorsque le traitement d'une exception interceptée a été effectué.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Envoyé par le De lorsqu'un programme a terminé le chargement.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Envoyé par le De lui donner l'affichage de l'IDE un message d'information à l'utilisateur.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Envoyé par le De lorsqu'un module est chargé ou déchargé.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Signale le débogueur interface utilisateur de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pour avertir l'utilisateur pour lequel des symboles ne peuvent pas être placés pour le fichier exécutable lancé.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Envoyé par le De lui donner l'affichage de l'IDE une chaîne arbitraire.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, PG.PRÉC|envoyé par un port pour communiquer des événements de port à tout écouteur.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DROITE, PICOSECONDE|Envoyé par le De ou le port lorsqu'un processus a été créé.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DROITE, PICOSECONDE|Envoyé par le De ou le port lorsqu'un processus a été détruit.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DROITE, PICOSECONDE|Envoyé par le De ou le port lorsqu'un programme a été créé.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DROITE, PICOSECONDE|Envoyé par le De ou le port lorsqu'un programme a été détruit.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Permet à un moteur de débogage pour remplacer le comportement par défaut de  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]interface utilisateur lorsque vous terminez une session de débogage.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Envoyé du moteur \(DE\) de débogage au gestionnaire de débogage de session \(SDM\) lorsque le nom d'un programme change.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Envoyé par le De lorsqu'une nouvelle propriété \(représentée par l'interface d' `IDebugProperty2` \) a été créée.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Envoyé par le De lorsqu'une propriété a été détruite.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Envoyé par le De lorsque la progression insuffisant ou sur une fonction que la valeur de retour peut être rendue correctement.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Permet aux moteurs de débogage pour lire les paramètres métriques à distance.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Envoyé par le De lorsqu'une étape dans, sur, ou à partir d'une instruction a été effectuée.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Envoyé par le De pour indiquer le succès ou l'échec de chargement de symboles pour un module.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Envoyé par le De lorsqu'un thread a été créé.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Envoyé par le De lorsqu'un thread a été détruit.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Envoyé par le De lorsqu'un thread a modifié son nom.|  
  
##  <a name="Expressions"></a> expressions  
 ces interfaces représentent des expressions à évaluer dans un contexte particulier.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|représente une expression à évaluer.  obtenu à partir de l'interface d' [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|représente un contexte dans lequel une expression est évaluée.  obtenu à partir de l'interface d' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) .|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Envoyé par le De lorsqu'une évaluation de l'expression asynchrone est terminée.|  
  
##  <a name="Memory"></a> Mémoire  
 Ces interfaces représentent des séquences d'octets en mémoire.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Représente une séquence d'octets en mémoire à partir de laquelle peut être lu ou en écriture.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|représente un emplacement à la mémoire d'une séquence d'octets.|  
  
##  <a name="Modules"></a> Modules  
 ces interfaces représentent un module, qui correspond à un fichier exécutable ou au fichier.DLL.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Représente un fichier exécutable ou une DLL unique.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|représente [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui prend en charge des symboles.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Envoyé par le De lorsqu'un module est chargé ou déchargé.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Représente les informations du serveur source contenues dans un fichier PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Représente une énumération sur un ensemble de modules connus par [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a> ports  
 Ces interfaces représentent des ports et les fournisseurs de port.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PICOSECONDE|représente le port par défaut sur l'ordinateur local.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Active un moteur de débogage qui utilise DCOM pour indiquer à [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur pour garantir que le pare\-feu ne se bloque pas le débogage distant.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PICOSECONDE|représente un port.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|envoyé par un port pour communiquer des événements de port à tout écouteur.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Représente un port qui peut démarrer et arrêter des processus.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Utilisé pour enregistrer et d'annuler l'enregistrement des programmes avec un port ; permet au port aux programmes de suivi actuellement en cours.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Représente une interface utilisateur personnalisé pour sélectionner le port.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Représente une demande d'un port à partir duquel un nouveau port est créé ou localisé.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|représente un fournisseur des ports.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Représente un fournisseur des ports qui peuvent persister \(enregistrement sur le disque\) des informations sur les ports qu'il a créés.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Active [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur du texte à l'intérieur de la section de **Les informations de transport** de la boîte de dialogue d' **Attacher au processus** .|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Permet demander des informations sur l'ordinateur cible.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PICOSECONDE|Représente une énumération sur un ensemble de ports.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Représente une énumération sur un ensemble de fournisseurs de port.|  
  
##  <a name="Processes"></a> Processus  
 ces interfaces représentent des processus, un fichier exécutable unique qui contient un ou plusieurs programmes.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PICOSECONDE, PG.PRÉC|Représente un processus qui s'exécute sur un ordinateur.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PICOSECONDE, PG.PRÉC|Représente un processus qui prend en charge active le débogage \(utilisé pour remplacer l'étape, pour continuer, et exécuter des méthodes sur l'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) \).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DROITE, PICOSECONDE|Envoyé par le De ou le port lorsqu'un processus a été créé.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DROITE, PICOSECONDE|Envoyé par le De ou le port lorsqu'un processus a été détruit.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Représente un processus qui doit suivre cette session est attachée à celui\-ci.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Représente une énumération d'un jeu de processus sur un port.|  
  
##  <a name="Programs"></a> Programmes  
 Ces interfaces sont des programmes, les unités logiques d'exécution qui ne correspondent pas nécessairement dans un fichier exécutable ou à un module physique.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Représente [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui doit s'exécuter de concert avec d'autres programmes en cours en même temps.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DROITE, PICOSECONDE|représente une unité logique d'exécution.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DROITE, PICOSECONDE|Envoyé par le De ou le port lorsqu'un programme a été créé.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DROITE, PICOSECONDE|Envoyé par le De ou le port lorsqu'un programme a été détruit.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DROITE, PICOSECONDE|Représente [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui peut être géré par plusieurs moteurs de débogage.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Représente [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui doit pouvoir suivre cette session est attachée à celui\-ci.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DROITE, PICOSECONDE|Représente [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui peut retourner des informations sur le processus dans lequel il s'exécute.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DROITE, PICOSECONDE|Représente un programme qui peut être débogué.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DROITE, PICOSECONDE|Permet un nœud de programme de telle sorte qu'il soit notifié d'une tentative de s'attacher au programme associé.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Permet que le SDM interroge un De sur les programmes contrôlés par ce De.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Utilisé par le DES pour stocker des programmes avec le SDM pour les afficher sont débogués.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DROITE, PICOSECONDE|Représente [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui peut marshaler des interfaces entre le thread ou traite des limites.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DROITE, PICOSECONDE|représente une énumération d'un ensemble de programmes.|  
  
##  <a name="Properties"></a> Propriétés  
 Ces interfaces représentent des propriétés, une valeur associée à un contexte particulier, généralement le résultat d'une évaluation de l'expression.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Représente [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui peut afficher sa valeur d'une manière personnalisée.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Représente une valeur d'un frame de pile, document, ou le résultat d'une évaluation de l'expression.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Représente [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui prend en charge arbitrairement des chaînes longues.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Envoyé par le De lorsqu'une nouvelle propriété \(représentée par l'interface d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) \) a été créée.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Envoyé par le De lorsqu'une propriété a été détruite.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Représente une référence à une propriété qui peut exister hors de tout frame de pile particulier.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Représente une énumération sur un jeu de structures de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui décrivent des variables, des registres, les paramètres, et les expressions.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Représente une énumération sur un jeu de structures de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .|  
  
##  <a name="StackFrames"></a> frames de pile  
 ces interfaces représentent un frame de pile, un contexte dans lequel un point d'arrêt ou une exception s'est produit.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|représente un contexte dans lequel un point d'arrêt ou une exception s'est produit.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Représente [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui peut gérer des exceptions interceptées.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Représente une énumération sur l'ensemble de structures de [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) qui spécifient la séquence d'appel de fonction utilisée pour arriver à un frame de pile particulier.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Représente une énumération sur un jeu de structures de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) , qui décrivent des frames de pile.|  
  
##  <a name="Threads"></a> Threads  
 Ces interfaces représentent des threads et leurs événements associés.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|représente un thread d'exécution.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Envoyé par le De lorsqu'un thread a été créé.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Envoyé par le De lorsqu'un thread a été détruit.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Envoyé par le De lorsqu'un thread a modifié son nom.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Représente une énumération sur un ensemble de thread.|  
  
##  <a name="TypeVisualizers"></a> visualiseurs de type  
 Ces interfaces fournissent une prise en charge des visualiseurs de type.  Ces interfaces sont généralement implémentées par un évaluateur d'expression.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Représente un tableau d'octets à présenter un visualiseur de type.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fournit des méthodes pour accéder aux données d'être passée à un visualiseur de type.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Représente une propriété qui fournit l'accès aux implémentations d' [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .|  
  
## Voir aussi  
 [Référence API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Création d'un moteur de débogage personnalisé](../../../extensibility/debugger/creating-a-custom-debug-engine.md)