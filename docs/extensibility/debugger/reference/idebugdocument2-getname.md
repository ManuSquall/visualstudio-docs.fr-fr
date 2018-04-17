---
title: IDebugDocument2::GetName | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e20d70b86050ae4b2ef4d983bb0efa8305947dff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Obtient le nom du document dans un des différents formulaires.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `gnType`  
 [in] Une valeur à partir de la [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) énumération qui détermine le type de nom à retourner.  
  
 `pbstrFileName`  
 [out] Retourne une chaîne contenant le nom du document.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut, par exemple, retourner le nom du document comme un titre ou un nom de fichier ou de la même partie d’un nom de fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)