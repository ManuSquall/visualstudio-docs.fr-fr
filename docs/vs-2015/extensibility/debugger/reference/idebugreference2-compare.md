---
title: IDebugReference2::Compare | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 41b183baa00f86c7a6e54d35b6188cd8c04946b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938284"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Compare une référence à un autre. Réservé à un usage ultérieur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
