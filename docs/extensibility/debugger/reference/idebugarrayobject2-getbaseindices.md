---
title: IDebugArrayObject2::GetBaseIndices | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b53b8f2cd7819650abbb4fc88a7ec3f4b6dfe21
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903190"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Récupère l’index de base (limites inférieures) pour chaque index étant donné le nombre de dimensions dans le tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBaseIndices (  
   DWORD  dwRank,  
   DWORD* dwIndices  
);  
```  
  
```csharp  
int GetBaseIndices (  
   uint       dwRank,  
   out uint[] dwIndices  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwRank`  
 [in] Le nombre de dimensions (rang) du tableau.  
  
 `dwIndices`  
 [out] Index de base (limites inférieures) pour le tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Par exemple, cette fonction retourne « 5 » pour le tableau créé par ce qui suit C# code :  
  
```  
int[] lengths = { 12 };  
int[] lowerbounds = { 5 };  
Array.CreateInstance(typeof(int), lengths, lowerbounds);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)