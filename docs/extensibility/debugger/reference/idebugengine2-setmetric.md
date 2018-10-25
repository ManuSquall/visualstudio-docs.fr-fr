---
title: IDebugEngine2::SetMetric | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 02f7d533cfc64ad7a1e3bfd342a2be56a5c6cd7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935950"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Cette méthode définit une valeur de Registre appelée une métrique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszMetric`  
 [in] Le nom de la mesure.  
  
 `varValue`  
 [in] Spécifie la valeur de métrique.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Une mesure est une valeur de Registre utilisée pour modifier le comportement d’un moteur débogage ou pour publier des fonctionnalités prises en charge. Cette méthode peut transférer l’appel à la forme appropriée de la [aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) (fonction), `SetMetric`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)