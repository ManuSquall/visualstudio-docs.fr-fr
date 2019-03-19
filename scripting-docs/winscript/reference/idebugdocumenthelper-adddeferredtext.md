---
title: IDebugDocumentHelper::AddDeferredText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1219543c438c79ad1add068262d9556dd2d7ce8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159333"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifie l’application d’assistance que le texte donné est disponible, mais il ne fournit pas les caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cChars`  
 [in] Nombre de caractères (Unicode) à ajouter.  
  
 `dwTextStartCookie`  
 [in] Cookies définis par l’hôte qui représente la position de départ du texte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|La méthode a échoué.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet à l’hôte de différer la pour ajouter jusqu'à ce qu’ils sont nécessaires, tout en autorisant l’assistance générer des notifications précises et des informations sur la taille de caractères non valides. Le `dwTextStartCookie` paramètre est un cookie, défini par l’hôte, qui représente la position de départ du texte. Les appels suivants à `IDebugDocumentText::GetText` doit fournir ce cookie. Par exemple, dans un hôte qui représente le texte en DBCS, le cookie peut être un décalage d’octet.  
  
 Il est supposé qu’un seul appel à `IDebugDocumentText::GetText` peut obtenir des caractères à partir de plusieurs appels à `AddDeferredText`. Classes d’assistance peuvent également demander la même plage de caractères différées plusieurs fois.  
  
> [!NOTE]
>  Les appels à `AddDeferredText` ne doivent pas être mélangées avec les appels à `AddUnicodeText` ou `AddDBCSText`. Si cela se produit, `E_FAIL` est retournée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)