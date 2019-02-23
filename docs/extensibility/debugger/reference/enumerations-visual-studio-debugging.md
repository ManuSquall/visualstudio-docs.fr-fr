---
title: Énumérations (débogage de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerations [Visual Studio SDK]
- debugging [Debugging SDK], enumerations
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86a41c0b548cc457853ecd1190c84f1ced846e58
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694528"
---
# <a name="enumerations-visual-studio-debugging"></a>Énumérations (débogage Visual Studio)
Voici les énumérations pour le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de débogage.

- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md) spécifie comment interpréter un ID de processus dans le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure.

- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) spécifie les types d’une adresse.

- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) spécifie où se trouve un assembly.

- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) spécifie la raison pour le moteur de débogage (dé) à attacher à un nœud de programme.

- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) spécifie la condition de point d’arrêt en attente de style pour et points d’arrêt liés.

- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) Spécifie le type d’erreur d’un point d’arrêt.

- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) fournit des indicateurs facultatifs qui peuvent être utilisées pour spécifier des informations supplémentaires lors de la définition d’un point d’arrêt.

- [BP_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md) énumère les valeurs valides pour les indicateurs facultatifs qui peuvent être utilisées pour spécifier des informations supplémentaires lors de la définition d’un point d’arrêt. Cette énumération étend la [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) énumération.

- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) Spécifie le type d’emplacement du point d’arrêt pour une demande de point d’arrêt.

- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) spécifie la condition associée au nombre de pass de point d’arrêt qui entraînera le point d’arrêt à déclencher.

- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) Spécifie si le point d’arrêt données émulée ou implémentées en matériel.

- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Spécifie l’existence d’un point d’arrêt lié et s’il est activé.

- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) Spécifie si le point d’arrêt se trouve à un emplacement de code, est un emplacement de données ou un autre type de point d’arrêt.

- [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) donne la raison pour laquelle un point d’arrêt a été dissocié.

- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) spécifie les informations à récupérer sur la résolution d’un point d’arrêt ayant échouée.

- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) spécifie les informations à récupérer sur une demande de point d’arrêt.

- [BPREQI_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md) énumère les valeurs valides qui spécifient les informations à récupérer une demande de point d’arrêt. Cette énumération étend la [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) énumération.

- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) spécifie les informations qui doit être récupérée sur la résolution d’un point d’arrêt.

- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) utilisée pour déterminer si un programme peut arrêter l’exécution après avoir atteint un point particulier dans l’exécution.

- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) une valeur qui indique le protocole utilisé pour communiquer entre un serveur de débogage et le package de débogage.

- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) sélectionne les différents types de constructeurs.

- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) spécifie les critères pour la comparaison de deux contextes de mémoire.

- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) spécifie les informations à récupérer sur un contexte de la mémoire.

- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) décrit plusieurs attributs d’un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ou un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interface.

- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) spécifie pourquoi le processus a été lancé pour le débogage.

- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) spécifie les informations à récupérer sur un objet de propriété de débogage.

- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) spécifie les informations à récupérer sur un objet de référence de débogage.

- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) spécifie les indicateurs pour le code machine.

- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) spécifie les informations à récupérer sur un champ de code machine.

- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) spécifie la portée du flux de code machine.

- [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) énumère les valeurs valides qui représentent les types d’informations à prendre dans un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) de l’objet et l’afficher à l’utilisateur.

- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) spécifie les critères pour la comparaison de deux contextes de document.

- [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) spécifie la quantité d’état d’un programme pour faire un dump.

- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) spécifie comment interpréter le type d’un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.

- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) représente les raisons de modifier et continueront n’est pas disponible.

- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) spécifie les indicateurs qui contrôlent l’évaluation de l’expression.

- [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md) énumère les valeurs valides pour les indicateurs qui contrôlent l’évaluation de l’expression. Cette énumération étend la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération.

- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) spécifie les attributs d’événement.

- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Spécifie l’état d’exception.

- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) spécifie les informations à récupérer sur un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.

- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Spécifie le type de champ contenue dans un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.

- [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) énumère les types de champs supplémentaires un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet peut contenir. Cette énumération étend la [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) énumération.

- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) spécifie les modificateurs pour un type de champ.

- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) spécifie les informations à récupérer sur un objet de frame de pile.

- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) Spécifie le type de nom d’hôte.

- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) Spécifie le type de nom des fichiers à récupérer.

- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) spécifie les actions à entreprendre lors de l’interception des exceptions.

- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) spécifie la manière dont un programme doit être lancé.

- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) spécifie quel type d’informations à récupérer pour un ordinateur particulier.

- [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) utilisé pour décrire un ordinateur.

- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) Spécifie le type de message et le motif.

- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) utilisé pour décrire un module.

- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) spécifie les indicateurs pour les informations de module de débogage.

- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Spécifie l’état de symboles pour un module.

- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) sélectionne l’option de casse pour les noms correspondants.

- [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Spécifie le type d’un objet à partir de l’évaluateur d’expression.

- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) spécifie comment analyser une expression.

- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) Spécifie l’état d’un point d’arrêt en attente (un point d’arrêt qui n’a pas encore été lié).

- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) spécifie les indicateurs d’état de point d’arrêt en attente.

- [PORT_SUPPLIER_DESCRIPTION_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md) définit les métadonnées qui peuvent être récupérées sur un fournisseur de port.

- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) spécifié quel type d’informations à récupérer pour un processus.

- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) décrit ou spécifie les propriétés d’un processus.

- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md) énumère les valeurs du programme détruire des indicateurs.

- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) spécifie les propriétés associées à un fournisseur de programme.

- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) spécifie des propriétés souhaitées pour être obtenu à partir d’un fournisseur de programme.

- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) Spécifie le type de comparaison de références.

- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) Spécifie le type de référence.

- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) spécifie la position à partir duquel commencer la recherche dans le code machine.

- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) Spécifie le type d’étape pour l’exécution pas à pas.

- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) Spécifie l’unité de progression pour l’exécution pas à pas.

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) spécifie quel type d’informations de symbole à récupérer.

- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) décrit les attributs d’un document.

- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) spécifie les informations sur un thread qui doit être récupéré.

- [Des États du thread](../../../extensibility/debugger/reference/threadstate.md) Spécifie l’état du thread.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h, sh.h ou ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)