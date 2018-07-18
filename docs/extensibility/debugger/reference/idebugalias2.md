---
title: IDebugAlias2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15fbf639c15e62b19e112ad140517f096d49f9d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103212"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente un alias numérique pour une variable et permet l’évaluateur d’expression (EE) pour obtenir le domaine d’application pour l’alias.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par le moteur de débogage managés (DE).  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes sur le [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interface, cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Récupère l’identificateur pour le domaine d’application.|  
  
## <a name="remarks"></a>Notes  
 Un alias est un nombre décimal sous forme de chaîne suivi par le caractère #, par exemple, 1001#.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll