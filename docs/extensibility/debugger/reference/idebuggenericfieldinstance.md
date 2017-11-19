---
title: IDebugGenericFieldInstance | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d7a0a16a6e7eb9f5901cecb5765d1ea2de2fb98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
Représente une instance d’un champ d’un type générique de code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugGenericFieldInstance : IUnknown  
```  
  
## <a name="methods"></a>Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|Récupère les arguments de paramètre de type pour cette instance.|  
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|Retourne le nombre de types des arguments de paramètre pour cette instance.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll