---
title: IDebugProperty3::GetStringChars | Microsoft Docs
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
ms.openlocfilehash: 7d6df39bcd02fe74e2c6ada24d341cd3d2fdfb75
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932928"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Récupère la chaîne associée à cette propriété et le stocke dans une mémoire tampon fournie par l’utilisateur.  
  
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
  
 (C++ uniquement), `rgString` est un pointeur vers une mémoire tampon qui reçoit les caractères Unicode de la chaîne. Cette mémoire tampon doit être au moins `buflen` caractères (non en octets) la taille.  
  
 `pceltFetched`  
 [out] Où le nombre de caractères réellement stocké dans la mémoire tampon est retourné. (Peut être `NULL` en C++.)  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En C++, doit veiller à s’assurer que la mémoire tampon est au moins `buflen` caractères Unicode. Notez qu’un caractère Unicode est de 2 octets de long.  
  
> [!NOTE]
>  En C++, la chaîne retournée n’inclut pas un caractère null de fin. Si spécifié, `pceltFetched` indique le nombre de caractères dans la chaîne.  
  
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