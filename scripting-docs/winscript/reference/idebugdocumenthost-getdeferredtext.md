---
title: IDebugDocumentHost::GetDeferredText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569425"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Retourne une plage de caractères qui ont été ajoutés à l’aide de la méthode `IDebugDocumentHelper::AddDeferredText`, dans le document hôte d’origine.  
  
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
 dans Cookie défini par l’hôte qui représente la position de départ du texte.  
  
 `pcharText`  
 [in, out] Mémoire tampon de texte de caractères. Cette méthode ne retourne pas de caractères si ce paramètre est `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Mémoire tampon d’attribut de caractère. Cette méthode ne retourne pas d’attributs si ce paramètre est `NULL`.  
  
 `pcNumChars`  
 [in, out] Indique le nombre réel de caractères/attributs retournés. Ce paramètre doit avoir la valeur zéro avant d’appeler cette méthode.  
  
 `cMaxChars`  
 dans Nombre maximal de caractères à retourner.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|Cette méthode n'est pas implémentée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut retourner `E_NOTIMPL`, si l’hôte n’appelle pas `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Cette méthode retourne le texte du document d’origine. L’hôte n’effectue pas le suivi des modifications ou d’autres modifications apportées au document.  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)