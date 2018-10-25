---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 96e1e98a8d095a2fd7fc9c63b42267fc70cab065
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933324"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Cette méthode utilise une recherche respectant la casse pour retourner la valeur associée au nom d’une constante d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
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
 Cette méthode respecte la casse. Si une recherche respectant la casse est nécessaire (par exemple, dans un langage tel que C++ où les noms respectent la casse), utilisez [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)