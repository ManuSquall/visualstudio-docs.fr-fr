---
title: IDebugReference2::Compare | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b00eb4e64e9dcccf4519f5e799f238ad01773b8a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860485"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Compare une référence à un autre. Réservé à un usage ultérieur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```csharp  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCompare`  
 [in] Une valeur comprise entre le [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) énumération qui spécifie l’opération de comparaison, par exemple, égale à, inférieur à ou supérieure à.  
  
 `pReference`  
 [in] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet représentant la référence à comparer.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)