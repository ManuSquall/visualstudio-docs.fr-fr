---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e983251a54d493115ba050503abe4f4c18933a99
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495988"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugEnumField::GetValueFromString](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugenumfield-getvaluefromstring).  
  
Cette méthode retourne la valeur associée au nom d’une constante d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszValue`  
 [in] Chaîne spécifiant le nom pour lequel obtenir la valeur. Notez que pour C++, il s’agit d’une chaîne de caractères larges.  
  
 `pValue`  
 [out] Retourne la valeur numérique associée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE`, si le nom ne fait pas partie de l’énumération ou un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode respecte la casse. Si une recherche respectant la casse est nécessaire (par exemple, dans un langage tel que Visual Basic, où les noms ne sont pas sensible à la casse), utilisez [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)

