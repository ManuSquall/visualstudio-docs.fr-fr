---
title: IDebugDocumentText2::GetText | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentText2::GetText
helpviewer_keywords: IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f018ce4d2a72c740909cb5dbc890a4d55294e03b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
Récupère le texte de la position spécifiée dans le document.  
  
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
 [in] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure qui indique l’emplacement du texte doit être récupéré.  
  
 `cMaxChars`  
 [in] Le nombre maximal de caractères du texte doit être récupéré.  
  
 `pText`  
 [dans, out] Pointeur vers une mémoire tampon qui doit être remplie avec le texte souhaité. Cette mémoire tampon doit être en mesure de contenir au moins `cMaxChars` nombre de caractères larges.  
  
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
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)