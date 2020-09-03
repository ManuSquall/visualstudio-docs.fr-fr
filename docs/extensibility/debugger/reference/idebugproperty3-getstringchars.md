---
title: 'IDebugProperty3 :: GetStringChars | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721084"
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

## <a name="parameters"></a>Paramètres
`buflen`\
dans Nombre maximal de caractères que la mémoire tampon fournie par l’utilisateur peut contenir.

`rgString`\
à Retourne la chaîne.

 [C++ uniquement], `rgString` est un pointeur vers une mémoire tampon qui reçoit les caractères Unicode de la chaîne. La taille de cette mémoire tampon doit être d’au moins `buflen` caractères (et non pas d’octets).

`pceltFetched`\
à Où le nombre de caractères réellement stockés dans la mémoire tampon est retourné. (Peut être `NULL` en C++.)

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
En C++, vous devez veiller à ce que la mémoire tampon soit au moins un `buflen` caractère Unicode long. Notez qu’un caractère Unicode a une longueur de 2 octets.

> [!NOTE]
> En C++, la chaîne retournée n’inclut pas de caractère null de fin. S’il est spécifié, `pceltFetched` spécifie le nombre de caractères dans la chaîne.

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
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
