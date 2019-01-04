---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9710d3bb30d838ed1fc90543e25c0892ea1d7bca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878963"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Cette méthode retourne la valeur associée au nom d’une constante d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszValue`  
 [in] Chaîne spécifiant le nom pour lequel obtenir la valeur. Notez que pour C++, il s’agit d’une chaîne de caractères larges.  
  
 `pValue`  
 [out] Retourne la valeur numérique associée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE`, si le nom ne fait pas partie de l’énumération ou un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode respecte la casse. Si une recherche respectant la casse est nécessaire (par exemple, dans un langage tel que Visual Basic, où les noms ne sont pas sensible à la casse), utilisez [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)