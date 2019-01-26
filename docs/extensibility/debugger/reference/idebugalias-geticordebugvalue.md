---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38debf5be309a97367f9a14c5f07ec3db6e7b666
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005941"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Récupère une interface en code managé qui représente la valeur associée à cet alias.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppUnk`  
 [out] `IUnknown` interface qui représente la valeur associée à cet alias. Cette interface peut être interrogée pour la `ICorDebugValue` interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode s’applique uniquement aux valeurs gérés (les `ICorDebugValue` une interface n’est disponible dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] et est défini dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK dans le fichier cordebug.idl).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)