---
title: IDebugTypeFieldBuilder2::CreateArrayOfType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3171fedfe263aa4e2624e4425d3bc6929dd3c2fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950444"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
Crée un tableau du type spécifié et de taille.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateArrayOfType (  
   IDebugField*  pTypeField,  
   DWORD         rank,  
   IDebugField** pArrayOfTypeField  
);  
```  
  
```csharp  
int CreateArrayOfType (  
   IDebugField     pTypeField,  
   uint            rank,  
   out IDebugField pArrayOfTypeField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pTypeField`  
 [in] Type des éléments de que tableau contiendra.  
  
 `rank`  
 [in] Nombre d’éléments dans le tableau.  
  
 `pArrayOfTypeField`  
 [out] Retourne le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objets qui représentent le nouveau tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)