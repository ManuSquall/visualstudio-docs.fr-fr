---
title: IDebugProperty3::GetStringChars ( Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721084"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Récupère la chaîne associée à cette propriété et la stocke dans un tampon fourni par l’utilisateur.

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
[dans] Nombre maximum de caractères que le tampon fourni par l’utilisateur peut contenir.

`rgString`\
[out] Retourne la ficelle.

 [C seulement], `rgString` est un pointeur à un tampon qui reçoit les caractères Unicode de la chaîne. Ce tampon doit `buflen` être au moins des caractères (pas des octets) de taille.

`pceltFetched`\
[out] Lorsque le nombre de caractères effectivement stockés dans le tampon est retourné. (Peut `NULL` être en C.)

## <a name="return-value"></a>Valeur de retour
En cas `S_OK`de succès, les retours; renvoie autrement un code d’erreur.

## <a name="remarks"></a>Notes
Dans le C, il faut s’assurer que le `buflen` tampon est au moins des caractères Unicode long. Notez qu’un personnage Unicode est de 2 octets de long.

> [!NOTE]
> Dans le C, la corde retournée n’inclut pas un caractère nul de fin. Si elle `pceltFetched` est donnée, spécifiera le nombre de caractères dans la chaîne.

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
