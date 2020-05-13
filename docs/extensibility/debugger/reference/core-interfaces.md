---
title: Interfaces de base (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737578"
---
# <a name="core-interfaces"></a>Interfaces de base
Les interfaces suivantes sont les interfaces de base [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]pour étendre le débbugger en utilisant le .

## <a name="discussion"></a>Discussions
 Ces interfaces sont principalement utilisées pour créer le moteur de débogé (DE). Ils sont organisés ici par catégories :

- [Points d’arrêt](#Breakpoints)

- [Contextes](#Contexts)

- [Serveur de base](#CoreServer)

- [Moteurs Debug](#DebugEngines)

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

- [Fils](#Threads)

- [Visualisateurs de type](#TypeVisualizers)

  Les entités qui peuvent implémenter les interfaces sont :

- Moteur Debug (DE)

- Fournisseur de port (PS)

- Évaluateur d’expression (EE)

- Studio visuel (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>Points d’arrêt
 Ces interfaces sont liées à la mise en œuvre et au suivi des points d’arrêt.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Représente un point d’arrêt lié à un emplacement de mémoire.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Envoyé par le DE quand un point d’arrêt est lié à un emplacement de mémoire.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Représente un document checksum pour une demande de point d’arrêt.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Envoyé par le DE quand un point d’arrêt ne parvient pas à être lié à un emplacement de mémoire.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Envoyé par le DE quand un point d’arrêt est atteint.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Représente une demande de point d’arrêt; utilisé dans la création d’un point d’arrêt en attente.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Représente une demande de point d’arrêt; utilisé dans la création d’un point d’arrêt en attente.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Représente les informations utilisées pour lier un point d’arrêt.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Envoyé par le DE quand un point d’arrêt est non lié à partir d’un emplacement de mémoire.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Représente un point d’arrêt invalide (retourné par `IDebugBreakpointErrorEvent2`).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Représente les informations de résolution sur un point d’arrêt invalide.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Représente une position dans une fonction où un point d’arrêt est défini.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Représente un point d’arrêt qui doit être lié; utilisé dans la création d’un point d’arrêt lié.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Représente un recensement sur un ensemble de points d’arrêt liés.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Représente un recensement sur un ensemble de points d’arrêt qui ne pouvaient pas être liés à un emplacement de mémoire.|

## <a name="contexts"></a><a name="Contexts"></a>Contextes
 Ces interfaces représentent différents types de contextes dans le programme étant débogé.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Représente la position de départ d’une instruction de code.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Étend l’interface [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) pour permettre la récupération des interfaces de module et de processus.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Représente une position dans un document.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Représente le contexte dans lequel évaluer une expression.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Représente l’emplacement de départ en mémoire d’une collection d’octets.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Représente un contexte de cadre de pile à un point d’arrêt ou une exception.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Représente un contexte de cadre de pile à un point d’arrêt ou une exception.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Représente une énumération sur un ensemble de contextes de code.|

## <a name="core-server"></a><a name="CoreServer"></a>Serveur de base
 Ces interfaces représentent la machine sur laquelle un programme est en cours de déboisation. Ceux-ci [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sont mis en œuvre par mais peuvent être appelés par les moteurs de débogé.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Fournit l’accès aux ports et aux fournisseurs portuaires ainsi que des informations sur l’ordinateur.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Représente un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) qui prend en charge le débogage à distance.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>Moteurs Debug
 Ces interfaces représentent les moteurs de débogé et leurs événements associés.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Représente un moteur de débogé personnalisé.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Représente un moteur de débogé personnalisé qui prend en charge le chargement des symboles, JustMyCode, et des exceptions.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Envoyé par chaque nouvelle instance de la DE pour indiquer qu’il est prêt à gérer les tâches de débogage.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Représente un moteur de débogé personnalisé qui prend en charge les programmes de lancement.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Représente un nœud de programme qui gère plusieurs moteurs débogés.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Fournit un moyen pour le SDM d’obtenir une interface au moteur de débogé à partir d’un fil, un programme ou un cadre de pile.|

## <a name="documents"></a><a name="Documents"></a>Documents
 Ces interfaces représentent des documents (fichiers sources) et leurs éléments associés.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Envoyé par le DE pour demander l’ouverture d’un document.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Représente un flux d’instructions démontées à partir d’un document.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Représente un document fourni par le DE, précisant un nom et une pièce d’identité de classe (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Représente un checksum pour un document de débogé et permet de passer le checksum entre les composants.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Représente un contexte de document, une position dans un document correspondant à un énoncé particulier et le contexte du code.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Représente une position générale dans un document.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Représente une position dans un fichier source en tant que décalage de caractère.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Représente un document texte fourni par le DE (dérivé de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), fournissant le texte réel.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Envoyé par le DE pour spécifier les modifications apportées à un fichier source en mémoire.|

## <a name="events"></a><a name="Events"></a>Événements
 Ces interfaces représentent tous les événements qui sont envoyés entre le DE et le gestionnaire de débogé de session (SDM).

| Interface | Mis en œuvre par | Description |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Envoyé par le DE pour demander l’ouverture d’un document. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Le moteur de déboçon (DE) envoie cette interface au gestionnaire de déboçon de session (SDM) pour définir le message de barre d’état pendant les charges de symbole. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Envoyé par le DE lorsqu’une pause dans le programme est terminée. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Envoyé par le DE quand un point d’arrêt est lié. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Envoyé par le DE quand un point d’arrêt ne parvient pas à être lié. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Envoyé par le DE quand un point d’arrêt est atteint. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Envoyé par le DE quand un point d’arrêt est non lié. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Envoyé par le DE pour déterminer s’il doit s’arrêter à un endroit particulier. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Envoyé par le DE pour spécifier les modifications apportées à un fichier source en mémoire. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Envoyé par chaque nouvelle instance de la DE pour indiquer qu’il est prêt à gérer les tâches de débogage. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Envoyé par le DE pour indiquer que le programme en cours de déboiffé est prêt à exécuter la première instruction. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Une interface qui est utilisée par d’autres interfaces d’événements, qui peuvent retourner une erreur, pour fournir des messages d’erreur lisibles par l’homme. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Interface de base à partir de laquelle toutes les autres interfaces d’événement sont dérivées. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Représente une interface implémentée par le SDM à laquelle les événements (exprimés comme des objets implémentant une interface événement particulier) sont envoyés. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Envoyé par le DE lorsqu’une exception s’est produite dans le programme étant débogé. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Envoyé par le DE lorsqu’une évaluation d’expression asynchrone est terminée. |
| IDebugFindSymbolEvent2 | | OBSOLÈTE. NE PAS UTILISER. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Envoyé par le DE lors du traitement d’une exception interceptée a été complété. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Envoyé par le DE lorsqu’un programme a terminé le chargement. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Envoyé par le DE pour que l’IDE affiche un message d’information à l’utilisateur. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Envoyé par le DE lorsqu’un module est chargé ou déchargé. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Signale [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur débbugger pour avertir l’utilisateur que les symboles ne pouvaient pas être localisés pour le lancement exécutable. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Envoyé par le DE pour avoir l’affichage IDE une chaîne arbitraire. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Envoyé par un port pour communiquer les événements portuaires à n’importe quel auditeur. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Envoyé par le DE ou le port lorsqu’un processus a été créé. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Envoyé par le DE ou le port lorsqu’un processus a été détruit. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Envoyé par le DE ou le port lorsqu’un programme a été créé. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Envoyé par le DE ou le port lorsqu’un programme a été détruit. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Permet à un moteur débogé de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] remplacer le comportement par défaut de l’interface utilisateur lorsque vous terminez une session de débogé. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Envoyé du moteur de débogé (DE) au gestionnaire de débogé de session (SDM) lorsque le nom d’un programme change. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Envoyé par le DE quand une nouvelle `IDebugProperty2` propriété (représentée par l’interface) a été créée. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Envoyé par le DE quand une propriété a été détruite. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Envoyé par le DE lors de la sortie ou sur une fonction de sorte que la valeur de retour peut être correctement affiché. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Permet aux moteurs de débogé de lire les paramètres métriques à distance. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Envoyé par le DE lorsqu’une entrée dans, plus ou hors d’une instruction a été complétée. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Envoyé par le DE pour indiquer le succès ou l’échec du chargement des symboles pour un module. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Envoyé par le DE quand un thread a été créé. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Envoyé par le DE quand un fil a été détruit. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Envoyé par le DE quand un thread a changé son nom. |

## <a name="expressions"></a>Expressions <a name="Expressions"></a>
 Ces interfaces représentent des expressions à évaluer dans un contexte particulier.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Représente une expression à évaluer. Obtenu à partir de l’interface [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Représente un contexte dans lequel une expression est évaluée. Obtenu à partir de l’interface [IDebugStackFrame2.](../../../extensibility/debugger/reference/idebugstackframe2.md)|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Envoyé par le DE lorsqu’une évaluation d’expression asynchrone est terminée.|

## <a name="memory"></a><a name="Memory"></a>Mémoire
 Ces interfaces représentent des séquences d’octets en mémoire.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Représente une séquence d’octets dans la mémoire qui peut être lu ou écrit à.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Représente un emplacement en mémoire d’une séquence d’octets.|

## <a name="modules"></a><a name="Modules"></a>Modules
 Ces interfaces représentent un module, qui correspond à un exécutable ou . Fichier DLL.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Représente un seul exécutant ou DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Représente un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui prend en charge les symboles.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Envoyé par le DE lorsqu’un module est chargé ou déchargé.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Représente les informations du serveur source contenues dans un fichier PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Représente un recensement sur un ensemble de modules qui sont connus par un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

## <a name="ports"></a><a name="Ports"></a>Ports
 Ces interfaces représentent les ports et les fournisseurs portuaires.

| Interface | Mis en œuvre par | Description |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Représente le port par défaut sur l’ordinateur local. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Permet à un moteur de débogage [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] qui utilise DCOM de demander à l’interface utilisateur pour s’assurer que le pare-feu ne bloquera pas le débogage à distance. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Représente un port. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Envoyé par un port pour communiquer les événements portuaires à n’importe quel auditeur. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Représente un port qui peut lancer et mettre fin aux processus. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Utilisé pour enregistrer et non enregistrer les programmes avec un port; permet au port de suivre les programmes actuellement déboqués. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Représente une interface utilisateur personnalisée pour la sélection du port. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Représente une demande pour un port à partir duquel un nouveau port sera créé ou situé. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Représente un fournisseur de ports. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Représente un fournisseur de ports qui peuvent persister (sauf pour le disque) des informations sur les ports qu’il a créés. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Permet [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur d’afficher du texte à l’intérieur de la section **Informations sur** les transports de la boîte de dialogue Attach **to Process.** |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Permet de demander des informations sur l’ordinateur cible. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Représente un recensement sur un ensemble de ports. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Représente un recensement sur un ensemble de fournisseurs portuaires. |

## <a name="processes"></a><a name="Processes"></a>Processus
 Ces interfaces représentent des processus, un seul exécutable qui contient un ou plusieurs programmes.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Représente un processus qui fonctionne sur un ordinateur.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Représente un processus qui prend activement en charge le débogage (utilisé pour remplacer les méthodes Step, Continue et Exécuter sur l’interface [IDebugProgram2).](../../../extensibility/debugger/reference/idebugprogram2.md)|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Envoyé par le DE ou le port lorsqu’un processus a été créé.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Envoyé par le DE ou le port lorsqu’un processus a été détruit.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Représente un processus qui doit suivre la session qui lui est rattachée.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Représente un recensement d’un ensemble de processus sur un port.|

## <a name="programs"></a><a name="Programs"></a>Programmes
 Ces interfaces représentent des programmes, des unités logiques d’exécution qui ne correspondent pas nécessairement à un module ou un module physique exécutable.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui doit travailler de concert avec d’autres programmes étant débogés en même temps.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Représente une unité logique d’exécution.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Envoyé par le DE ou le port lorsqu’un programme a été créé.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Envoyé par le DE ou le port lorsqu’un programme a été détruit.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Représente un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui peut être manipulé par plusieurs moteurs de débogé.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui doit être en mesure de suivre quelle session lui est attachée.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Représente un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui peut retourner des informations sur le processus dans lequel il est en cours d’exécution.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Représente un programme qui peut être déboqué.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Permet à un nœud de programme d’être avisé d’une tentative de s’attacher au programme associé.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Fournit un moyen pour le SDM d’interroger un DE sur les programmes contrôlés par ce DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Utilisé par les DE pour enregistrer les programmes auprès du SDM pour montrer qu’ils sont débogés.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Représente un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui peut marshal interfaces à travers le fil ou les limites de processus.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Représente un recensement d’un ensemble de programmes.|

## <a name="properties"></a>Propriétés de <a name="Properties"></a>
 Ces interfaces représentent des propriétés, une valeur associée à un contexte particulier, généralement le résultat d’une évaluation d’expression.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Représente un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui peut afficher sa valeur d’une manière personnalisée.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Représente la valeur d’un cadre de pile, d’un document ou du résultat d’une évaluation d’expression.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Représente un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui prend en charge les cordes arbitrairement longues.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Envoyé par le DE quand une nouvelle propriété (représentée par l’interface [IDebugProperty2)](../../../extensibility/debugger/reference/idebugproperty2.md) a été créée.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Envoyé par le DE quand une propriété a été détruite.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Représente une référence à une propriété qui peut exister en dehors de n’importe quel cadre de pile particulier.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Représente un recensement sur un ensemble de structures [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui décrivent les variables, les registres, les paramètres et les expressions.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Représente un recensement sur un ensemble de [structures DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)|

## <a name="stack-frames"></a><a name="StackFrames"></a>Cadres de pile
 Ces interfaces représentent un cadre de pile, un contexte dans lequel un point d’arrêt ou une exception s’est produit.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Représente un contexte dans lequel un point d’arrêt ou une exception s’est produit.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Représente un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui peut gérer les exceptions interceptées.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Représente un recensement sur l’ensemble des structures [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) qui spécifient la séquence d’appel de fonction utilisée pour arriver à un cadre de pile particulier.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Représente un recensement sur un ensemble de structures [FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) qui décrivent les cadres de pile.|

## <a name="threads"></a><a name="Threads"></a>Fils
 Ces interfaces représentent les fils et les événements qui y sont associés.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Représente un fil d’exécution.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Envoyé par le DE quand un thread a été créé.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Envoyé par le DE quand un fil a été détruit.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Envoyé par le DE quand un thread a changé son nom.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Représente une énumération sur un ensemble de fils.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>Visualisateurs de type
 Ces interfaces fournissent une prise en charge des visualisateurs de type. Ces interfaces sont généralement implémentées par un évaluateur d’expression.

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Représente un éventail d’octets à présenter à un visualisateur de type.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fournit des méthodes pour obtenir l’accès aux données à transmettre à un visualisateur de type.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Représente une propriété qui donne accès aux implémentations [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|

## <a name="see-also"></a>Voir aussi
- [Référence des API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Création d’un moteur de débogage personnalisé](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
