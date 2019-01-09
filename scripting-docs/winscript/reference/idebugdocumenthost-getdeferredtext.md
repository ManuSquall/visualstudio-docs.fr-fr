---
title: IDebugDocumentHost::GetDeferredText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f2a39122454ea170177aee9ce7b2bbeb7ea248e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092558"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Retourne une plage de caractères qui ont été ajoutés à l’aide de la `IDebugDocumentHelper::AddDeferredText` (méthode), dans le document d’hôte d’origine.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwTextStartCookie`  
 [in] Cookies définis par l’hôte qui représente la position de départ du texte.  
  
 `pcharText`  
 [in, out] Une mémoire tampon de texte caractères. Cette méthode ne retourne pas de caractères si ce paramètre est `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Une mémoire tampon de caractères attribut. Cette méthode ne retourne pas les attributs si ce paramètre est `NULL`.  
  
 `pcNumChars`  
 [in, out] Indique le nombre réel de caractères/attributs renvoyés. Ce paramètre doit être défini à zéro avant d’appeler cette méthode.  
  
 `cMaxChars`  
 [in] Le nombre maximal de caractères à retourner.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|La méthode n’est pas implémentée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut retourner `E_NOTIMPL`, si l’hôte n’appelle pas `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Cette méthode retourne le texte du document d’origine. L’hôte ne se préoccupe pas de modifications ou autres modifications au document.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)