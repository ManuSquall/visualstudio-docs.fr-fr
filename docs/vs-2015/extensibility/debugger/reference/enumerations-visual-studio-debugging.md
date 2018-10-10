---
title: Énumérations (débogage de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Studio SDK]
- debugging [Debugging SDK], enumerations
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e6c431624c176142007b383470d67dc4f73e50f
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881044"
---
# <a name="enumerations-visual-studio-debugging"></a>Énumérations (débogage Visual Studio)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [énumérations (débogage de Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/enumerations-visual-studio-debugging).  
  
Voici les énumérations pour le [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] SDK de débogage.  
  
 [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)  
 Spécifie comment interpréter un ID de processus dans le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure.  
  
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)  
 Spécifie les types d’une adresse.  
  
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)  
 Spécifie où se trouve un assembly.  
  
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)  
 Spécifie la raison pour le moteur de débogage (dé) à attacher à un nœud de programme.  
  
 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)  
 Spécifie le style de condition de point d’arrêt pour en attente et de points d’arrêt liés.  
  
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)  
 Spécifie le type d’erreur d’un point d’arrêt.  
  
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)  
 Fournit des indicateurs facultatifs qui peuvent être utilisées pour spécifier des informations supplémentaires lors de la définition d’un point d’arrêt.  
  
 [BP_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md)  
 Énumère les valeurs valides pour les indicateurs facultatifs qui peuvent être utilisées pour spécifier des informations supplémentaires lors de la définition d’un point d’arrêt. Cette énumération étend la [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) énumération.  
  
 [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)  
 Spécifie le type d’emplacement du point d’arrêt pour une demande de point d’arrêt.  
  
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)  
 Spécifie la condition associée au nombre de pass de point d’arrêt qui entraînera le point d’arrêt à déclencher.  
  
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)  
 Spécifie si le point d’arrêt données émulée ou implémentées en matériel.  
  
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)  
 Spécifie l’existence d’un point d’arrêt lié et s’il est activé.  
  
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)  
 Spécifie si le point d’arrêt se trouve à un emplacement de code, est un emplacement de données ou un autre type de point d’arrêt.  
  
 [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md)  
 Donne la raison pour laquelle qu'un point d’arrêt a été dissocié.  
  
 [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)  
 Spécifie les informations à récupérer sur la résolution d’un point d’arrêt ayant échouée.  
  
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)  
 Spécifie les informations à récupérer sur une demande de point d’arrêt.  
  
 [BPREQI_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md)  
 Énumère les valeurs valides qui spécifient les informations à récupérer une demande de point d’arrêt. Cette énumération étend la [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) énumération.  
  
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)  
 Spécifie les informations à récupérer sur la résolution d’un point d’arrêt.  
  
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)  
 Utilisé pour déterminer si un programme peut arrêter l’exécution après avoir atteint un point particulier dans l’exécution.  
  
 [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)  
 Une valeur qui indique le protocole utilisé pour communiquer entre un serveur de débogage et le package de débogage.  
  
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)  
 Sélectionne les différents types de constructeurs.  
  
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)  
 Spécifie les critères pour la comparaison de deux contextes de mémoire.  
  
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)  
 Spécifie les informations à récupérer sur un contexte de la mémoire.  
  
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)  
 Décrit les différents attributs pour un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ou un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interface.  
  
 [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)  
 Spécifie la raison pour laquelle le processus a été lancé pour le débogage.  
  
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)  
 Spécifie les informations à récupérer sur un objet de propriété de débogage.  
  
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)  
 Spécifie les informations à récupérer sur un objet de référence de débogage.  
  
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)  
 Spécifie les indicateurs pour le code machine.  
  
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)  
 Spécifie les informations à récupérer sur un champ de code machine.  
  
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)  
 Spécifie l’étendue du flux de code machine.  
  
 [DisplayKind](../../../extensibility/debugger/reference/displaykind.md)  
 Énumère les valeurs valides qui représentent les types d’informations à prendre dans un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) de l’objet et l’afficher à l’utilisateur.  
  
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)  
 Spécifie les critères pour la comparaison de deux contextes de document.  
  
 [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)  
 Spécifie la quantité d’état d’un programme pour faire un dump.  
  
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)  
 Spécifie comment interpréter le type d’un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.  
  
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)  
 Représente les raisons de modifier & Continuer n’est pas disponible.  
  
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)  
 Spécifie les indicateurs qui contrôlent l’évaluation de l’expression.  
  
 [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md)  
 Énumère les valeurs valides pour les indicateurs qui contrôlent l’évaluation de l’expression. Cette énumération étend la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération.  
  
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)  
 Spécifie les attributs d’événement.  
  
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)  
 Spécifie l’état d’exception.  
  
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)  
 Spécifie les informations à récupérer sur un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.  
  
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)  
 Spécifie le type de champ contenue dans un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.  
  
 [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md)  
 Énumère les types de champs supplémentaires un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet peut contenir. Cette énumération étend la [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) énumération.  
  
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)  
 Spécifie les modificateurs pour un type de champ.  
  
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)  
 Spécifie les informations permettant de récupérer sur un objet de frame de pile.  
  
 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)  
 Spécifie le type du nom d’hôte.  
  
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)  
 Spécifie le type de nom des fichiers à récupérer.  
  
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)  
 Spécifie les actions à entreprendre lors de l’interception des exceptions.  
  
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)  
 Spécifie la manière dont un programme doit être lancé.  
  
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)  
 Spécifie le genre d’informations à récupérer pour un ordinateur particulier.  
  
 [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md)  
 Utilisé pour décrire un ordinateur.  
  
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)  
 Spécifie le type de message et le motif.  
  
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)  
 Utilisé pour décrire un module.  
  
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)  
 Spécifie les indicateurs pour les informations de module de débogage.  
  
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)  
 Spécifie l’état de symboles pour un module.  
  
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)  
 Sélectionne l’option de casse pour les noms correspondants.  
  
 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md)  
 Spécifie le type d’un objet à partir de l’évaluateur d’expression.  
  
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)  
 Spécifie comment analyser une expression.  
  
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)  
 Spécifie l’état d’un point d’arrêt en attente (un point d’arrêt qui n’a pas encore été lié).  
  
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)  
 Spécifie les indicateurs d’état de point d’arrêt en attente.  
  
 [PORT_SUPPLIER_DESCRIPTION_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md)  
 Définit les métadonnées qui peuvent être récupérées sur un fournisseur de port.  
  
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)  
 Spécifié le type d’informations à récupérer pour un processus.  
  
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)  
 Décrivent ou spécifient les propriétés d’un processus.  
  
 [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)  
 Énumère les valeurs du programme détruire des indicateurs.  
  
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)  
 Spécifie les propriétés associées à un fournisseur de programme.  
  
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)  
 Spécifie les propriétés souhaitées doivent être obtenues à partir d’un fournisseur de programme.  
  
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)  
 Spécifie le type de comparaison des références.  
  
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)  
 Spécifie le type de référence.  
  
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)  
 Spécifie la position à partir duquel commencer la recherche dans le code machine.  
  
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)  
 Spécifie le type d’étape pour l’exécution pas à pas.  
  
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)  
 Spécifie l’unité de progression pour l’exécution pas à pas.  
  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)  
 Spécifie le genre d’informations de symbole à récupérer.  
  
 [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)  
 Décrit les attributs d’un document.  
  
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)  
 Spécifie les informations sur un thread qui doit être récupéré.  
  
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)  
 Spécifie l’état du thread.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h, sh.h ou ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

