---
title: IDebugCodeContext2::GetLanguageInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords: IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2b2f6f49b7ee8ebdf356a25bc2531aa2b8b9cf8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Obtient les informations de langue pour ce contexte de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrLanguage`  
 [dans, out] Retourne une chaîne qui contient le nom de la langue, tel que « C++ ».  
  
 `pguidLanguage`  
 [dans, out] Retourne le GUID pour la langue du contexte du code, par exemple, `guidCPPLang`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Au moins un des paramètres doit retourner une valeur non null.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)