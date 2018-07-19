---
title: IDebugProperty3::GetStringChars | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f7d5430326f57acf686b90f911445cc36dbf02
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118243"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Récupère la chaîne associée à cette propriété et la stocke dans une mémoire tampon fournie par l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `buflen`  
 [in] Nombre maximal de caractères de que la mémoire tampon fournie par l’utilisateur peut contenir.  
  
 `rgString`  
 [out] Retourne la chaîne.  
  
 (C++ uniquement), `rgString` est un pointeur vers une mémoire tampon qui reçoit les caractères Unicode de la chaîne. Cette mémoire tampon doit être au moins `buflen` caractères (pas des octets) de taille.  
  
 `pceltFetched`  
 [out] Où le nombre de caractères réellement stocké dans la mémoire tampon est retourné. (Peut être `NULL` en C++.)  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En C++, veillez à vous assurer que la mémoire tampon est au moins `buflen` caractères Unicode. Notez qu’un caractère Unicode est de 2 octets de long.  
  
> [!NOTE]
>  En C++, la chaîne retournée n’inclut pas un caractère null de fin. Si, `pceltFetched` indique le nombre de caractères dans la chaîne.  
  
## <a name="example"></a>Exemple  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>Voir aussi  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)