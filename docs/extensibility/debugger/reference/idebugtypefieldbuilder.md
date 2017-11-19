---
title: IDebugTypeFieldBuilder | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e90ed00775c8c2ba53a68c67b4bcc11ed84e20b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Représente la capacité de créer un champ qui représente un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est obtenue à partir du fournisseur de symboles.  
  
## <a name="methods"></a>Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Crée un objet qui représente un type primitif.|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crée un pointeur vers le type spécifié.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll