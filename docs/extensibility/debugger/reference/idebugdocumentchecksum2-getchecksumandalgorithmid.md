---
title: IDebugDocumentChecksum2::GetChecksumAndAlgorithmId Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2::GetChecksumAndAlgorithmI
- GetChecksumAndAlgorithmI
ms.assetid: 25efef99-0ef3-4332-a752-607605fc6e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c26d5b9c2c45fd1ce932fc1108e4f77f2508cb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731943"
---
# <a name="idebugdocumentchecksum2getchecksumandalgorithmid"></a>IDebugDocumentChecksum2::GetChecksumAndAlgorithmId
Récupère l’identifiant de vérification des documents et de l’algorithme étant donné le nombre maximum d’octets à utiliser.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetChecksumAndAlgorithmId(
    GUID  *pRetVal,
    ULONG cMaxBytes,
    BYTE  *pChecksum,
    ULONG *pcNumBytes
);
```

```csharp
public int GetChecksumAndAlgorithmId(
    out Guid pRetVal,
    uint     cMaxBytes,
    out byte pChecksum,
    out uint pcNumBytes
);
```

## <a name="parameters"></a>Paramètres
`pRetVal`\
[out] Identifiant unique pour l’algorithme checksum.

`cMaxBytes`\
[dans] Nombre maximum d’octets à utiliser pour le checksum.

`pChecksum`\
[out] Valeur du checksum.

`pcNumBytes`\
[out] Nombre réel d’octets utilisés pour le checksum.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple
L’exemple suivant utilise cette méthode pour obtenir le checksum et l’algorithme d’un document.

```cpp
HRESULT CDebugCodeContext::GetDocumentChecksumAndAlgorithmId(GUID *pguidAlgorithm, BYTE **ppChecksum, ULONG *pcNumBytes)
{
    HRESULT hRes = E_FAIL;

    *ppChecksum = NULL;
    *pcNumBytes = 0;

    CComPtr<IDebugDocumentContext2> pDocContext;

    hRes = this->GetDocumentContext(&pDocContext);

    if ( HREVAL(S_OK, hRes) )
    {
        CComQIPtr<IDebugDocumentChecksum2> pDocChecksum(pDocContext);

        if ( pDocChecksum != NULL )
        {
            // Figure out the size of the checksum buffer required
            ULONG cNumBytes = 0;

            hRes = pDocChecksum->GetChecksumAndAlgorithmId(pguidAlgorithm, 0, NULL, &cNumBytes);

            if ( S_OK == hRes )
            {
                // check to see if we got back valid values
                if ( cNumBytes && GUID_NULL != (*pguidAlgorithm) )
                {
                    // Alloc space for the checksum data
                    BYTE *pChecksum = (BYTE*) CoTaskMemAlloc(cNumBytes);

                    if ( pChecksum )
                    {
                        // Get the buffer containing the checksum info
                        hRes = pDocChecksum->GetChecksumAndAlgorithmId(pguidAlgorithm, cNumBytes, pChecksum, &cNumBytes);

                        if ( HREVAL(S_OK, hRes) )
                        {
                            *ppChecksum = pChecksum;
                            *pcNumBytes = cNumBytes;
                        }
                        else
                        {
                            CoTaskMemFree(pChecksum);
                        }
                    }
                    else
                        hRes = E_OUTOFMEMORY;
                }
                else
                    hRes = S_FALSE; // lang doesn't support checksums
            }
            else
                hRes = S_FALSE; // failed to work out checksum info
        }
        else
            hRes = S_FALSE; // SH doesn't support checksums
    }

    return ( hRes );
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)
