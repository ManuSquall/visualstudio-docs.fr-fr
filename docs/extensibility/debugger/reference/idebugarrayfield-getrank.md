---
title: IDebugArrayField::GetRank | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetRank
helpviewer_keywords: IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 786f765e684f720c8c29b91331259e772bd5a007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Obtient le rang ou le nombre de dimensions du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 Le rang d’un tableau correspond au nombre de dimensions. Dans C++ et c#, les tableaux multidimensionnels sont vraiment les tableaux de tableaux et peut donc être considéré comme simplement un tableau unidimensionnel (et le `GetRank` méthode retourne toujours 1). Dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], quant à eux, les tableaux multidimensionnels sont gérées différemment et le rang d’un tel tableau reflète le nombre de dimensions (et le `GetRank` méthode retourne toujours le nombre de dimensions).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)