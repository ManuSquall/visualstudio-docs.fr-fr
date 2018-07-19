---
title: IDebugDocumentHelper::AddDeferredText | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728539"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifie l’application d’assistance que le texte spécifié est disponible, mais il ne fournit pas les caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|La méthode a échoué.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode permet à l’hôte de report qui fournit les caractères pour ajouter jusqu'à ce qu’ils sont nécessaires, tout en autorisant l’application d’assistance générer des notifications exactes et les informations de taille. Le `dwTextStartCookie` paramètre est un cookie, défini par l’hôte, qui représente la position de départ du texte. Les appels suivants à `IDebugDocumentText::GetText` doit fournir ce cookie. Par exemple, dans un hôte qui représente le texte en DBCS, le cookie peut être un décalage d’octet.  
  
 Il est supposé qu’un seul appel à `IDebugDocumentText::GetText` peut obtenir les caractères de plusieurs appels à `AddDeferredText`. Classes d’assistance peuvent également demander la même plage de caractères différées plusieurs fois.  
  
> [!NOTE]
>  Les appels à `AddDeferredText` ne doit pas être combiné avec des appels à `AddUnicodeText` ou `AddDBCSText`. Si cela se produit, `E_FAIL` est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper (Interface)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)