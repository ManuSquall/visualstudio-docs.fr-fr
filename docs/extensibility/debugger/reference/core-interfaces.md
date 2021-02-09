---
title: Interfaces principales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee2f44e5d75d44cfc1c903d462e7a1df360eeefa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899170"
---
# <a name="core-interfaces"></a>Interfaces de base
Les interfaces suivantes sont les interfaces principales permettant d’étendre le débogueur à l’aide de [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Discussions
 Ces interfaces sont principalement utilisées pour créer le moteur DE débogage (DE). Ils sont organisés ici par catégories :

- [Points d'arrêt](#Breakpoints)

- [Contextes](#Contexts)

- [Serveur de base](#CoreServer)

- [Déboguer les moteurs](#DebugEngines)

- [Documents](#Documents)

- [Événements](#Events)

- [Expressions](#Expressions)

- [Mémoire](#Memory)

- [Modules](#Modules)

- [Ports](#Ports)

- [Processus](#Processes)

- [Programmes](#Programs)

- [Propriétés](#Properties)

- [Frames de pile](#StackFrames)

- [Threads](#Threads)

- [Visualiseurs de type](#TypeVisualizers)

  Les entités qui peuvent implémenter les interfaces sont les suivantes :

- Moteur DE débogage (DE)

- Fournisseur de port (PS)

- Évaluateur d’expression (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a> Points
 Ces interfaces sont liées à l’implémentation et au suivi des points d’arrêt.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Représente un point d’arrêt lié à un emplacement de mémoire.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Envoyé par le lorsqu’un point d’arrêt est lié à un emplacement de mémoire.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Représente la somme de contrôle d’un document pour une demande de point d’arrêt.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Envoyé par l’opération DE lorsqu’un point d’arrêt ne peut pas être lié à un emplacement de mémoire.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt est atteint.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Représente une demande pour un point d’arrêt ; utilisé lors de la création d’un point d’arrêt en attente.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Représente une demande pour un point d’arrêt ; utilisé lors de la création d’un point d’arrêt en attente.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Représente les informations utilisées pour lier un point d’arrêt.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Envoyé par le DE lorsqu’un point d’arrêt est indépendant d’un emplacement de mémoire.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Représente un point d’arrêt non valide (retourné par `IDebugBreakpointErrorEvent2` ).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Représente les informations de résolution relatives à un point d’arrêt non valide.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Représente une position dans une fonction où un point d’arrêt est défini.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Représente un point d’arrêt qui doit être lié ; utilisé pour créer un point d’arrêt lié.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Représente une énumération sur un jeu de points d’arrêt liés.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Représente une énumération sur un jeu de points d’arrêt qui n’a pas pu être lié à un emplacement de mémoire.|

## <a name="contexts"></a><a name="Contexts"></a> Contextes
 Ces interfaces représentent différents types de contextes au sein du programme en cours de débogage.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Représente la position de départ d’une instruction de code.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Étend l’interface [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) pour permettre la récupération d’interfaces de module et de processus.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Représente une position dans un document.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Représente le contexte dans lequel évaluer une expression.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Représente l’emplacement de départ en mémoire d’une collection d’octets.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Représente un contexte de frame de pile au niveau d’un point d’arrêt ou d’une exception.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Représente un contexte de frame de pile au niveau d’un point d’arrêt ou d’une exception.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Représente une énumération sur un jeu de contextes de code.|

## <a name="core-server"></a><a name="CoreServer"></a> Serveur de base
 Ces interfaces représentent l’ordinateur sur lequel un programme est en cours de débogage. Elles sont implémentées par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] mais peuvent être appelées par les moteurs de débogage.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Permet d’accéder aux ports et fournisseurs de port, ainsi qu’aux informations sur l’ordinateur.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Représente un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) qui prend en charge le débogage distant.|

## <a name="debug-engines"></a><a name="DebugEngines"></a> Déboguer les moteurs
 Ces interfaces représentent les moteurs de débogage et leurs événements associés.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Représente un moteur de débogage personnalisé.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Représente un moteur de débogage personnalisé qui prend en charge le chargement de symboles, JustMyCode et exceptions.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Envoyé par chaque nouvelle instance de l’élément de pour indiquer qu’il est prêt à gérer les tâches de débogage.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Représente un moteur de débogage personnalisé qui prend en charge le lancement de programmes.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Représente un nœud de programme qui gère plusieurs moteurs de débogage.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Offre un moyen pour le SDM d’obtenir une interface au moteur de débogage à partir d’un thread, d’un programme ou d’un frame de pile.|

## <a name="documents"></a><a name="Documents"></a> Évoqu
 Ces interfaces représentent des documents (fichiers sources) et leurs éléments associés.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Envoyé par le de pour demander l’ouverture d’un document.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Représente un flux d’instructions désassemblées à partir d’un document.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Représente un document fourni par le DE, en spécifiant un nom et un ID de classe (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Représente une somme de contrôle pour un document de débogage et permet de passer la somme de contrôle entre les composants.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Représente un contexte de document, une position dans un document qui correspond à une instruction particulière et un contexte de code.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Représente une position générale dans un document.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Représente une position dans un fichier source sous la forme d’un offset de caractère.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Représente un document texte fourni par le DE (dérivé de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), en fournissant le texte réel.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Envoyé par le de pour spécifier les modifications apportées à un fichier source qui est en mémoire.|

## <a name="events"></a><a name="Events"></a> Événements
 Ces interfaces représentent tous les événements qui sont envoyés entre le et le gestionnaire DE débogage DE session (SDM).

| Interface | Implémenté par | Description |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Envoyé par le de pour demander l’ouverture d’un document. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Le moteur DE débogage (DE) envoie cette interface au gestionnaire de débogage de session (SDM) pour définir le message de la barre d’État pendant les chargements de symboles. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Envoyé par le DE lorsqu’une interruption du programme est terminée. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Envoyé par l’un lorsqu’un point d’arrêt est lié. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Envoyé par le DE lorsqu’un point d’arrêt ne peut pas être lié. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Envoyé par le DE lorsqu’un point d’arrêt est atteint. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Envoyé par le DE lorsqu’un point d’arrêt est indépendant. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Envoyé par le de pour déterminer s’il doit s’arrêter à un emplacement particulier. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Envoyé par le de pour spécifier les modifications apportées à un fichier source qui est en mémoire. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Envoyé par chaque nouvelle instance de l’élément de pour indiquer qu’il est prêt à gérer les tâches de débogage. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Envoyé par le pour indiquer que le programme en cours de débogage est prêt à exécuter la première instruction. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Interface utilisée par d’autres interfaces d’événements, qui peuvent retourner une erreur, pour fournir des messages d’erreur explicites. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Interface de base à partir de laquelle toutes les autres interfaces d’événements sont dérivées. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Représente une interface implémentée par le SDM auquel les événements (exprimés sous forme d’objets implémentant une interface d’événement particulière) sont envoyés. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Envoyé par le si une exception s’est produite dans le programme en cours de débogage. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Envoyé par le lorsque l’évaluation d’une expression asynchrone est terminée. |
| IDebugFindSymbolEvent2 | | OBSOLÈTE. N’UTILISEZ PAS. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Envoyé par le DE lorsque le traitement d’une exception interceptée est terminé. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Envoyé par le DE lorsque le chargement d’un programme est terminé. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Envoyé par le de pour que l’IDE affiche un message d’information à l’utilisateur. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Envoyé par le DE lorsqu’un module est chargé ou déchargé. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Signale [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur du débogueur d’avertir l’utilisateur que les symboles n’ont pas pu être localisés pour l’exécutable lancé. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Envoyé par le de pour que l’IDE affiche une chaîne arbitraire. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Envoyé par un port pour communiquer des événements de port à n’importe quel écouteur. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Envoyé par le port DE ou lorsqu’un processus a été créé. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Envoyé par le port DE ou lorsqu’un processus a été détruit. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Envoyé par le port DE ou lorsqu’un programme a été créé. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Envoyé par le port DE ou lorsqu’un programme a été détruit. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Permet à un moteur de débogage de substituer le comportement par défaut de l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur quand vous terminez une session de débogage. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Envoyé du moteur de débogage (DE) au gestionnaire de débogage de session (SDM) lorsque le nom d’un programme change. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Envoyé par le DE quand une nouvelle propriété (représentée par l' `IDebugProperty2` interface) a été créée. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Envoyé par le DE quand une propriété a été détruite. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Envoyé par le en cas de pas à pas sortant ou sur une fonction afin que la valeur de retour puisse être affichée correctement. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Permet aux moteurs de débogage de lire des paramètres métriques à distance. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Envoyé par le DE lorsqu’une étape dans, au-dessus ou en dehors d’une instruction a été effectuée. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Envoyé par le pour indiquer la réussite ou l’échec du chargement des symboles pour un module. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Envoyé par le DE quand un thread a été créé. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Envoyé par le DE quand un thread a été détruit. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Envoyé par le DE quand un thread a modifié son nom. |

## <a name="expressions"></a>Expressions <a name="Expressions"></a>
 Ces interfaces représentent des expressions à évaluer dans un contexte particulier.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Représente une expression à évaluer. Obtenu à partir de l’interface [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Représente un contexte dans lequel une expression est évaluée. Obtenu à partir de l’interface [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) .|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Envoyé par le lorsque l’évaluation d’une expression asynchrone est terminée.|

## <a name="memory"></a><a name="Memory"></a> Capacité
 Ces interfaces représentent des séquences d’octets en mémoire.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Représente une séquence d’octets en mémoire à partir de laquelle il est possible de lire ou d’écrire.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Représente un emplacement en mémoire d’une séquence d’octets.|

## <a name="modules"></a><a name="Modules"></a> Actualis
 Ces interfaces représentent un module, qui correspond à un exécutable ou. Fichier DLL.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Représente un exécutable ou une DLL unique.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Représente un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui prend en charge les symboles.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Envoyé par le DE lorsqu’un module est chargé ou déchargé.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Représente les informations de serveur source contenues dans un fichier PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Représente une énumération sur un ensemble de modules connus par un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

## <a name="ports"></a><a name="Ports"></a> Utilis
 Ces interfaces représentent des ports et des fournisseurs de ports.

| Interface | Implémenté par | Description |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Représente le port par défaut sur l’ordinateur local. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Active un moteur de débogage qui utilise DCOM pour demander [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur de s’assurer que le pare-feu ne bloque pas le débogage distant. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Représente un port. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Envoyé par un port pour communiquer des événements de port à n’importe quel écouteur. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Représente un port qui peut lancer et terminer des processus. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Permet d’inscrire et d’annuler l’inscription de programmes sur un port ; permet au port de suivre les programmes en cours de débogage. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Représente une interface utilisateur personnalisée pour la sélection du port. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Représente une demande pour un port à partir duquel un nouveau port sera créé ou localisé. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Représente un fournisseur de ports. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Représente un fournisseur de ports qui peuvent persister (enregistrer sur disque) des informations sur les ports qu’il a créés. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Permet [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur d’afficher du texte dans la section **informations de transport** de la boîte de dialogue **attacher au processus** . |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Permet d’obtenir des informations sur l’ordinateur cible. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Représente une énumération sur un ensemble de ports. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Représente une énumération sur un ensemble de fournisseurs de ports. |

## <a name="processes"></a><a name="Processes"></a> Processus
 Ces interfaces représentent des processus, un exécutable unique qui contient un ou plusieurs programmes.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Représente un processus qui s’exécute sur un ordinateur.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Représente un processus qui prend activement en charge le débogage (utilisé pour remplacer les méthodes Step, continue et Execute sur l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Envoyé par le port DE ou lorsqu’un processus a été créé.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Envoyé par le port DE ou lorsqu’un processus a été détruit.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Représente un processus qui doit assurer le suivi de la session qui lui est associée.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Représente une énumération d’un ensemble de processus sur un port.|

## <a name="programs"></a><a name="Programs"></a> Installés
 Ces interfaces représentent des programmes, des unités logiques d’exécution qui ne correspondent pas nécessairement à un exécutable physique ou à un module.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui doit fonctionner de concert avec d’autres programmes en cours de débogage en même temps.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Représente une unité logique d’exécution.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Envoyé par le port DE ou lorsqu’un programme a été créé.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Envoyé par le port DE ou lorsqu’un programme a été détruit.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Représente un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui peut être géré par plusieurs moteurs de débogage.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui doit être en mesure d’effectuer le suivi de la session qui lui est associée.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui peut retourner des informations sur le processus dans lequel il s’exécute.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Représente un programme pouvant être débogué.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Permet à un nœud de programme d’être averti d’une tentative d’attachement au programme associé.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Fournit un moyen pour le SDM d’interroger un DE à propos des programmes contrôlés par ce.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Utilisé par les pour inscrire des programmes auprès du SDM pour montrer qu’ils sont en cours de débogage.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Représente un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui peut marshaler des interfaces à travers les limites de thread ou de processus.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Représente une énumération d’un ensemble de programmes.|

## <a name="properties"></a><a name="Properties"></a> Propriétés
 Ces interfaces représentent des propriétés, une valeur associée à un contexte particulier, généralement le résultat d’une évaluation d’expression.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Représente un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui peut afficher sa valeur de façon personnalisée.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Représente une valeur d’un frame de pile, d’un document ou le résultat d’une évaluation d’expression.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Représente un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui prend en charge les chaînes arbitrairement longues.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Envoyé par le DE lorsqu’une nouvelle propriété (représentée par l’interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ) a été créée.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Envoyé par le DE quand une propriété a été détruite.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Représente une référence à une propriété qui peut exister en dehors d’un frame de pile particulier.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Représente une énumération sur un ensemble de structures de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui décrivent des variables, des registres, des paramètres et des expressions.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Représente une énumération sur un ensemble de structures de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .|

## <a name="stack-frames"></a><a name="StackFrames"></a> Frames de pile
 Ces interfaces représentent un frame de pile, un contexte dans lequel un point d’arrêt ou une exception s’est produit.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Représente un contexte dans lequel un point d’arrêt ou une exception s’est produit.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Représente un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui peut gérer les exceptions interceptées.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Représente une énumération sur le jeu de structures de [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) qui spécifient la séquence d’appel de fonction utilisée pour arriver à un frame de pile particulier.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Représente une énumération sur un ensemble de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) qui décrivent des frames de pile.|

## <a name="threads"></a><a name="Threads"></a> Thèmes
 Ces interfaces représentent les threads et leurs événements associés.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Représente un thread d’exécution.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Envoyé par le DE quand un thread a été créé.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Envoyé par le DE quand un thread a été détruit.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Envoyé par le DE quand un thread a modifié son nom.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Représente une énumération sur un ensemble de threads.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a> Visualiseurs de type
 Ces interfaces assurent la prise en charge des visualiseurs de type. Ces interfaces sont généralement implémentées par un évaluateur d’expression.

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Représente un tableau d’octets à présenter à un visualiseur de type.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fournit des méthodes pour obtenir l’accès aux données à passer à un visualiseur de type.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Représente une propriété qui fournit l’accès aux implémentations de [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .|

## <a name="see-also"></a>Voir aussi
- [Référence sur l’API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Création d’un moteur de débogage personnalisé](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
