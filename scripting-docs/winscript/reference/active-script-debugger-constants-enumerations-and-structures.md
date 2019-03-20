---
title: Constantes de débogueur de Script actif, énumérations et Structures | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b287001371b80612a2b09a9672e59aff51309cc9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153095"
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>Débogueur de script actif, constantes, énumérations et structures
Les constantes, les énumérations et les structures suivantes sont utilisées par les interfaces actives de débogage.  
  
## <a name="constants-enumerations-and-structures"></a>Constantes, énumérations et structures  
  
|Constantes|Description|  
|---------------|-----------------|  
|[APPBREAKFLAGS (constantes)](../../winscript/reference/appbreakflags-enumeration.md)|Indique l'état actuel du débogage des applications et des threads.|  
|[Constantes DEBUG_TEXT](../../winscript/reference/debug-text-constants.md)|Indicateurs d’option utilisés pendant [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).|  
|[Constantes TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)|Décrit les attributs du document.|  
  
|Énumérations|Description|  
|------------------|-----------------|  
|[APPBREAKFLAGS (constantes)](../../winscript/reference/appbreakflags-enumeration.md)|Indique l'état actuel du débogage des applications et des threads.|  
|[Énumération APPLICATION_NODE_EVENT_FILTER](../../winscript/reference/application-node-event-filter-enumeration.md)|Indique les nœuds à exclure par un filtre.|  
|[Énumération BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)|Indique l'état d'un point d'arrêt.|  
|[Énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md)|Indique ce qui a provoqué l'arrêt.|  
|[Énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)|Explique comment poursuivre à partir d'un point d'arrêt.|  
|[Énumération DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)|Décrit le type à obtenir pour un document.|  
|[Énumération ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)|Explique comment poursuivre à partir d'une erreur d'exécution.|  
|[Énumération JS_PROPERTY_ATTRIBUTES](../../winscript/reference/js-property-attributes-enumeration.md)|Indique les attributs d'une propriété.|  
|[Énumération JS_PROPERTY_MEMBERS](../../winscript/reference/js-property-members-enumeration.md)|Indicateurs pour spécifier le type d'informations à retourner dans une requête pour les membres d'un objet.|  
|[Énumération JsDebugReadMemoryFlags](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|Indicateurs pour spécifier le comportement pendant la lecture de la mémoire.|  
|[Énumération SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md)|Indique un jeu d'options ou des fonctions qui s'appliquent au débogueur joint.|  
|[Énumération SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|Indique le type d'exception levé.|  
|[SOURCE_TEXT_ATTR (constantes)](../../winscript/reference/source-text-attr-enumeration.md)|Décrit les attributs d'un caractère unique de texte source.|  
  
|Structures|Description|  
|----------------|-----------------|  
|[Structure DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)|Énumère les frames de pile et fusionne les résultats de plusieurs énumérateurs sur le même thread.|  
|[Structure JS_NATIVE_FRAME](../../winscript/reference/js-native-frame-structure.md)|Représente un frame de pile.|  
|[Structure JsDebugPropertyInfo](../../winscript/reference/jsdebugpropertyinfo-structure.md)|Indique des informations sur une propriété.|  
|[Structure TEXT_DOCUMENT_ARRAY](../../winscript/reference/text-document-array-structure.md)|Fournit un ensemble de documents.|