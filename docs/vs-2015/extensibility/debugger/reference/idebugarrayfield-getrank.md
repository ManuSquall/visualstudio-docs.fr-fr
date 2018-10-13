---
title: IDebugArrayField::GetRank | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1f06df292c5ed9ed2b7201589f5aa659b3f9716
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177279"
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
 Le rang d’un tableau correspond au nombre de dimensions. Dans C++ et c#, les tableaux multidimensionnels sont vraiment les tableaux de tableaux et peut donc être considéré comme simplement un tableau unidimensionnel (et le `GetRank` méthode retourne toujours 1). Dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], quant à eux, des tableaux multidimensionnels sont gérés différemment et le classement d’un tel tableau reflète le nombre de dimensions (et le `GetRank` méthode retourne toujours le nombre de dimensions).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)

