---
title: IDebugField::GetSize | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5f025b96c3a37cd55d8bc148d04196a862f7e7bc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Cette méthode obtient la taille d’un champ, en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwSize`  
 [out] Retourne la taille.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Tous les champs ont un type et tous les types ont une taille. Par exemple, un champ avec un type d’octet a une taille de 1 octet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
