---
title: IDebugField::GetSize | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e7343f6d496587c3fbf69adf3ec56a9f516a9be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110352"
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
  
## <a name="remarks"></a>Notes  
 Tous les champs ont un type et tous les types ont une taille. Par exemple, un champ avec un type d’octet a une taille de 1 octet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)