---
title: IDebugDocumentText2::GetText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetText
helpviewer_keywords:
- IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3eb4eae82dd11d58734ed114886c9ec121b60b69
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678356"
---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
Récupère le texte à partir de la position spécifiée dans le document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetText(
    TEXT_POSITION pos,
    ULONG         cMaxChars,
    WCHAR*        pText,
    ULONG*        pcNumChars
);
```

```csharp
int GetText(
    eumn_TEXT_POSITION pos,
    uint               cMaxChars,
    IntPtr             pText,
    out uint           pcNumChars
);
```

#### <a name="parameters"></a>Paramètres
`pos`

 [in] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure qui indique l’emplacement du texte à récupérer.

`cMaxChars`

 [in] Le nombre maximal de caractères du texte à récupérer.

`pText`

 [in, out] Pointeur vers une mémoire tampon qui doit être rempli avec le texte souhaité. Cette mémoire tampon doit être en mesure de contenir au moins `cMaxChars` nombre de caractères larges.

`pcNumChars`

 [out] Retourne le nombre de caractères réellement récupérées.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="example"></a>Exemple
Cet exemple montre comment cette méthode peut être appelée à partir de c#.

```csharp
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Debugger.Interop;

namespace Mynamespace
{
    class MyClass
    {
        string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)
        {
            string documentText = string.Empty;
            if (pText != null)
            {
                uint numLines = 0;
                uint numChars = 0;
                int hr;
                hr = pText.GetSize(ref numLines, ref numChars);
                if (ErrorHandler.Succeeded(hr))
                {
                    IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));
                    uint actualChars = 0;
                    hr = pText.GetText(pos, numChars, buffer, out actualChars);
                    if (ErrorHandler.Succeeded(hr))
                    {
                        documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);
                    }
                    Marshal.FreeCoTaskMem(buffer);
                }
            }
            return documentText;
        }
    }
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
