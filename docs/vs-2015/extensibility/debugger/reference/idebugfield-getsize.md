---
title: IDebugField::GetSize | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fded9abc006ff6a28e122f0a4b8d7fae5da997b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952162"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode obtient la taille d’un champ, en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
