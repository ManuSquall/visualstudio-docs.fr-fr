---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7044f237e5475cd355a744ad9af6fc0f6ce1c446
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725476"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode obtient le nom de la constante d’énumération étant donné sa valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value`  
 [in] La valeur pour laquelle obtenir le nom de l’énumération constante.  
  
 `pbstrValue`  
 [out] Retourne le nom de la constante d’énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` si la valeur n’a aucun nom associé, ou retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 S’il existe plusieurs noms associé à la même valeur, le premier nom défini dans l’énumération s’affichera.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)

