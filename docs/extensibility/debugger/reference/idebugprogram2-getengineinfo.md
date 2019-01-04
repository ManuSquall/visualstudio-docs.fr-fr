---
title: IDebugProgram2::GetEngineInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8a3b2fca94451eded823cac23524ea04d6e5d6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840948"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
Obtient le nom et le GUID du moteur de débogage (dé) ce programme en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetEngineInfo(   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(   
   out string pbstrEngine,  
   out GUID   pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrEngine`  
 [out] Retourne le nom de la DE ce programme en cours d’exécution.  
  
 `pguidEngine`  
 [out] Retourne le GUID de la DE ce programme en cours d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque dé définit son propre GUID pour l’identification.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)