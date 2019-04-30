---
title: IDebugProcess2::GetProcessId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b927d5a8da316faa76b5d102ad0cfb14e0cb61e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870935"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le GUID de ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```csharp  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pguidProcessId`  
 [out] Retourne le GUID pour ce processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’identificateur global Unique (GUID) identifie ce processus à partir de tous les autres processus en cours d’exécution dans le système.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
