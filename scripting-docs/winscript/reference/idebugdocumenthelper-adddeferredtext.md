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
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577041"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifie le programme d’assistance que le texte spécifié est disponible, mais ne fournit pas les caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cChars`  
 dans Nombre de caractères (Unicode) à ajouter.  
  
 `dwTextStartCookie`  
 dans Cookie défini par l’hôte qui représente la position de départ du texte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Échec de la méthode.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet à l’hôte de différer la fourniture des caractères à ajouter jusqu’à ce qu’ils soient nécessaires, tout en permettant à l’application auxiliaire de générer des notifications et des informations de taille précises. Le paramètre `dwTextStartCookie` est un cookie, défini par l’hôte, qui représente la position de départ du texte. Les appels suivants à `IDebugDocumentText::GetText` doivent fournir ce cookie. Par exemple, dans un hôte qui représente du texte dans DBCS, le cookie peut être un décalage d’octet.  
  
 Il est supposé qu’un seul appel à `IDebugDocumentText::GetText` peut obtenir des caractères à partir de plusieurs appels à `AddDeferredText`. Les classes d’assistance peuvent également demander plusieurs fois la même plage de caractères différés.  
  
> [!NOTE]
> Les appels à `AddDeferredText` ne doivent pas être mélangés avec des appels à `AddUnicodeText` ou `AddDBCSText`. Si cela se produit, `E_FAIL` est retourné.  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)