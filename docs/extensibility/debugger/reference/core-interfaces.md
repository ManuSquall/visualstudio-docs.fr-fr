---
title: Interfaces de base | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 367917032b836ce6a7d07cf3eba85db14464a957
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="core-interfaces"></a>Interfaces de base
Les interfaces suivantes sont les interfaces de base pour l’extension de débogueur à l’aide de la [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Discussion  
 Ces interfaces sont principalement utilisées pour créer le moteur de débogage (DE). Elles sont organisées ici par catégories :  
  
-   [Points d’arrêt](#Breakpoints)  
  
-   [Contextes](#Contexts)  
  
-   [Installation minimale](#CoreServer)  
  
-   [Moteurs de débogage](#DebugEngines)  
  
-   [Documents](#Documents)  
  
-   [Événements](#Events)  
  
-   [Expressions](#Expressions)  
  
-   [Mémoire](#Memory)  
  
-   [Modules](#Modules)  
  
-   [Ports](#Ports)  
  
-   [Processus](#Processes)  
  
-   [Programmes](#Programs)  
  
-   [Propriétés](#Properties)  
  
-   [Frames de pile](#StackFrames)  
  
-   [Threads](#Threads)  
  
-   [Visualiseurs de type](#TypeVisualizers)  
  
 Les entités qui peuvent implémenter les interfaces sont :  
  
-   Déboguer le moteur (DE)  
  
-   Fournisseur de port (PS)  
  
-   Évaluateur d’expression (EE)  
  
-   Visual Studio (Visual Studio)  
  
##  <a name="Breakpoints"></a>Points d’arrêt  
 Ces interfaces sont liées à l’implémentation et le suivi des points d’arrêt.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Représente un point d’arrêt lié à un emplacement de mémoire.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt est lié à un emplacement de mémoire.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Représente une somme de contrôle du document pour une demande de point d’arrêt.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt ne peut pas être lié à un emplacement de mémoire.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt est atteint.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Représente une demande pour un point d’arrêt ; utilisé pour la création d’un point d’arrêt en attente.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Représente une demande pour un point d’arrêt ; utilisé pour la création d’un point d’arrêt en attente.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Représente les informations utilisées pour lier un point d’arrêt.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt est détachée à partir d’un emplacement de mémoire.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Représente un point d’arrêt non valide (retourné par `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Représente les informations de résolution sur un point d’arrêt non valide.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Représente une position dans une fonction où un point d’arrêt est défini.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Représente un point d’arrêt qui doit être lié ; utilisé pour la création d’un point d’arrêt lié.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Représente une énumération sur un ensemble de points d’arrêt liés.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Représente une énumération sur un ensemble de points d’arrêt qui n’a pas pu être lié à un emplacement de mémoire.|  
  
##  <a name="Contexts"></a>Contextes  
 Ces interfaces représentent les différents types de contextes dans le programme en cours de débogage.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Représente la position de départ d’une instruction de code.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Étend la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interface pour permettre l’extraction des interfaces de module et de processus.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Représente une position dans un document.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Représente le contexte dans lequel évaluer l’expression.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Représente l’emplacement de départ dans la mémoire d’une collection d’octets.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Représente un contexte de frame de pile à un point d’arrêt ou une exception.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Représente un contexte de frame de pile à un point d’arrêt ou une exception.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Représente une énumération sur un ensemble de contextes de code.|  
  
##  <a name="CoreServer"></a>Installation minimale  
 Ces interfaces représentent l’ordinateur sur lequel un programme est en cours de débogage. Celles-ci sont implémentées par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] mais peut être appelé par les moteurs de débogage.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Fournit l’accès aux ports et fournisseurs de port ainsi que des informations sur l’ordinateur.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Représente un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) qui prend en charge le débogage distant.|  
  
##  <a name="DebugEngines"></a>Moteurs de débogage  
 Ces interfaces représentent des moteurs de débogage et les événements associés.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Représente un moteur de débogage personnalisé.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Représente un moteur de débogage personnalisé qui prend en charge le chargement de symboles, JustMyCode et d’exceptions.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Envoyé par chaque nouvelle instance de la DE pour indiquer qu’il est prêt à gérer les tâches de débogage.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Représente un moteur de débogage personnalisé qui prend en charge le lancement des programmes.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Représente un nœud de programme qui gère plusieurs moteurs de débogage.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Fournit un moyen pour le SDM obtenir une interface pour le moteur de débogage à partir d’un thread, un programme ou un frame de pile.|  
  
##  <a name="Documents"></a>Documents  
 Ces interfaces représentent des documents (fichiers sources) et leurs éléments associés.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Envoyé par le DE demander un document à ouvrir.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Représente un flux d’instructions désassemblés à partir d’un document.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Représente un document fourni par le DE, en spécifiant un nom et un ID de classe (CLSID).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Représente une somme de contrôle pour un document de débogage et permet le transfert de la somme de contrôle entre les composants.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Représente un contexte de document, une position dans un document correspondant à un contexte d’instruction et de code particulier.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Représente une position générale dans un document.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Représente une position dans un fichier source par un offset de caractère.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Représente un document de texte fourni par le DE (dérivée de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), en fournissant le texte.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Envoyé par le DE pour spécifier les modifications apportées à un fichier source qui est en mémoire.|  
  
##  <a name="Events"></a> Événements  
 Ces interfaces représentent tous les événements qui sont envoyées entre les périphériques et le Gestionnaire de session de débogage (SDM).  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Envoyé par le DE demander un document à ouvrir.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Le moteur de débogage (DE) envoie cette interface pour le Gestionnaire de session de débogage (SDM) pour définir l’état de message barre symbole de charge.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Envoyé par le DE quand un saut dans le programme a été effectué.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt est lié.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt ne peut pas être lié.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt est atteint.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt est détachée.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Envoyé par le DE pour déterminer si elle doit s’arrêter à un emplacement particulier.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Envoyé par le DE pour spécifier les modifications apportées à un fichier source qui est en mémoire.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Envoyé par chaque nouvelle instance de la DE pour indiquer qu’il est prêt à gérer les tâches de débogage.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Envoyé par le DE pour indiquer le programme débogué est prêt à exécuter la première instruction.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Interface qui est utilisée par d’autres interfaces d’événements, qui peuvent retourner une erreur, pour fournir des messages d’erreur explicite.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE, PS|Interface de base à partir de quel événement autres toutes les interfaces sont dérivés.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Représente une interface implémentée par le SDM à laquelle sont envoyés les événements (exprimé en tant qu’objets implémentant une interface d’événement particulier).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Envoyé par le DE lorsqu’une exception s’est produite dans le programme en cours de débogage.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Envoyé par le DE quand une évaluation d’expression asynchrone est terminée.|  
|IDebugFindSymbolEvent2||OBSOLÈTE. N’UTILISEZ PAS.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Envoyé par le DE fin de traitement pour une exception interceptée.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Envoyé par le DE lorsqu’un programme a terminé le chargement.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Envoyé par le DE à l’IDE affiche un message d’information à l’utilisateur.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Envoyé par le DE quand un module est chargé ou déchargé.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Signale la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur pour l’avertir que les symboles ne peut pas être localisés pour l’exécutable lancé du débogueur.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Envoyé par le DE pour afficher le IDE une chaîne arbitraire.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, DE|Envoyé par un port pour communiquer les événements de port à n’importe quel écouteur.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Envoyé par le port ou DE création d’un processus.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Envoyé par le port ou DE quand un processus a été détruit.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Envoyé par le port ou DE création d’un programme.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Envoyé par le port ou DE quand un programme a été détruit.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Permet à un moteur de débogage substituer le comportement par défaut de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur lorsque vous arrêtez une session de débogage.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Envoyé à partir du moteur de débogage (DE) pour le Gestionnaire de session de débogage (SDM) lorsque le nom d’un programme change.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Envoyé par le DE lorsqu’une nouvelle propriété (représenté par la `IDebugProperty2` interface) a été créé.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Envoyé par le DE quand une propriété a été détruite.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Envoyé par le DE lors de l’exécution pas à pas d’ou sur une fonction afin que la valeur de retour peut être affichée correctement.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Active les moteurs pour lire les paramètres de mesure de débogage à distance.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Envoyé par le DE quand une étape détaillé, principal ou en dehors d’une instruction a été effectuée.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Envoyé par le DE pour indiquer la réussite ou l’échec de chargement des symboles pour un module.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Envoyé par le DE lorsqu’un thread a été créé.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Envoyé par le DE quand un thread a été détruit.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Envoyé par le DE quand un thread a changé son nom.|  
  
##  <a name="Expressions"></a>Expressions  
 Ces interfaces représentent des expressions à évaluer dans un contexte particulier.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Représente une expression à évaluer. Obtenu à partir de la [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Représente un contexte dans lequel l’expression est évaluée. Obtenu à partir de la [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interface.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Envoyé par le DE quand une évaluation d’expression asynchrone est terminée.|  
  
##  <a name="Memory"></a>Mémoire  
 Ces interfaces représentent des séquences d’octets en mémoire.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Représente une séquence d’octets en mémoire qui peuvent être lues ou écrites dans.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Représente un emplacement dans la mémoire d’une séquence d’octets.|  
  
##  <a name="Modules"></a> Modules  
 Ces interfaces représentent un module, ce qui correspond à un fichier exécutable ou. Fichier DLL.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Représente un seul exécutable ou DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Représente un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui prend en charge les symboles.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Envoyé par le DE quand un module est chargé ou déchargé.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Représente les informations du serveur source qui sont contenues dans un fichier PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Représente une énumération sur un ensemble de modules qui sont connues par un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a>Ports  
 Ces interfaces représentent les ports et les fournisseurs de port.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Représente le port par défaut sur l’ordinateur local.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Permet à un moteur de débogage qui utilise le modèle DCOM pour demander le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur pour vous assurer que le pare-feu ne bloque pas le débogage distant.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|Représente un port.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Envoyé par un port pour communiquer les événements de port à n’importe quel écouteur.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Représente un port peut démarrer et arrêter les processus.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Permet d’enregistrer et annuler l’inscription des programmes avec un port. permet au port effectuer le suivi des programmes en cours de débogage.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Représente une interface utilisateur personnalisée pour sélectionner le port.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Représente une demande pour un port à partir de laquelle un nouveau port va être créé ou situé.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Représente un fournisseur de ports.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Représente un fournisseur de ports qui peut être rendue persistante (enregistrer sur le disque) des informations sur les ports qu’il est créé.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Permet la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur pour afficher le texte à l’intérieur de la **informations de Transport** section de la **attacher au processus** boîte de dialogue.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Permet de demande d’informations sur l’ordinateur cible.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Représente une énumération sur un ensemble de ports.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Représente une énumération sur un ensemble de fournisseurs de port.|  
  
##  <a name="Processes"></a>Processus  
 Ces interfaces représentent des processus, un fichier exécutable contenant un ou plusieurs programmes.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Représente un processus qui s’exécute sur un ordinateur.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Représente un processus qui activement prend en charge le débogage (utilisé pour remplacer l’étape, continuer et exécuter des méthodes sur le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Envoyé par le port ou DE création d’un processus.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Envoyé par le port ou DE quand un processus a été détruit.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Représente un processus qui doit suivre la session lui est attachée.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Représente une énumération d’un ensemble de processus sur un port.|  
  
##  <a name="Programs"></a>Programmes  
 Ces interfaces représentent des programmes, les unités logiques d’exécution qui ne correspondent pas nécessairement à un fichier exécutable physique ou un module.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui doit fonctionner conjointement avec d’autres programmes en cours de débogage en même temps.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Représente une unité logique de l’exécution.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Envoyé par le port ou DE création d’un programme.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Envoyé par le port ou DE quand un programme a été détruit.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Représente un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui peut être géré par plusieurs moteurs de débogage.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui doit pouvoir effectuer le suivi de session lui est attachée.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui peut retourner des informations sur le processus dans lequel il est en cours d’exécution.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Représente un programme qui peut être débogué.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Permet à un nœud de programme être averti d’une tentative d’attachement au programme associé.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Fournit un moyen pour le SDM interroger un DE sur les programmes contrôlés par ce DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Utilisé par DEs auprès des programmes le SDM pour montrer qu’ils sont en cours de débogage.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Représente un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui puisse marshaler interfaces au-delà des limites de thread ou processus.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Représente une énumération d’un ensemble de programmes.|  
  
##  <a name="Properties"></a> Propriétés  
 Ces interfaces représentent les propriétés, une valeur associée à un contexte particulier, généralement le résultat d’une évaluation d’expression.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Représente un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui peut afficher sa valeur d’une manière personnalisée.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Représente une valeur d’un frame de pile, document ou le résultat d’une évaluation d’expression.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Représente un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui prend en charge les chaînes de longues arbitraire.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Envoyé par le DE lorsqu’une nouvelle propriété (représenté par la [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface) a été créé.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Envoyé par le DE quand une propriété a été détruite.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Représente une référence à une propriété qui peut exister en dehors d’un frame de pile donné.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Représente une énumération sur un ensemble de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures qui décrivent les variables, les registres, les paramètres et les expressions.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Représente une énumération sur un ensemble de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structures.|  
  
##  <a name="StackFrames"></a>Frames de pile  
 Ces interfaces représentent un frame de pile, un contexte dans lequel un point d’arrêt ou une exception s’est produite.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Représente un contexte dans lequel un point d’arrêt ou une exception s’est produite.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Représente un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui peut gérer interception des exceptions.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Représente une énumération dans le jeu de [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) séquence utilisée pour arriver à un frame de pile particulier d’appel de structures qui spécifient la fonction.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Représente une énumération sur un ensemble de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures qui décrivent les frames de pile.|  
  
##  <a name="Threads"></a> Threads  
 Ces interfaces représentent les threads et les événements associés.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Représente un thread d’exécution.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Envoyé par le DE lorsqu’un thread a été créé.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Envoyé par le DE quand un thread a été détruit.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Envoyé par le DE quand un thread a changé son nom.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Représente une énumération sur un ensemble de threads.|  
  
##  <a name="TypeVisualizers"></a>Visualiseurs de type  
 Ces interfaces prennent en charge les visualiseurs de type. Ces interfaces sont généralement implémentées par un évaluateur d’expression.  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Représente un tableau d’octets à être présentés à un visualiseur de type.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fournit des méthodes pour accéder aux données à passer à un visualiseur de type.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Représente une propriété qui fournit l’accès aux [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implémentations.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Création d’un moteur de débogage personnalisé](../../../extensibility/debugger/creating-a-custom-debug-engine.md)