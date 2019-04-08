---
title: IDebugArrayField::GetRank | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d0396718482c9ce90527155a3612160612f66d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952378"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le rang ou le nombre de dimensions du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwRank`  
 [out] Retourne le rang.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le rang d’un tableau correspond au nombre de dimensions. Dans C++ et C#, les tableaux multidimensionnels sont vraiment les tableaux de tableaux et peut donc être considéré comme simplement un tableau unidimensionnel (et le `GetRank` méthode retourne toujours 1). Dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], quant à eux, des tableaux multidimensionnels sont gérés différemment et le classement d’un tel tableau reflète le nombre de dimensions (et le `GetRank` méthode retourne toujours le nombre de dimensions).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
