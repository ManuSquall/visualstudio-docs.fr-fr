---
title: 'IDebugEnumField :: GetStringFromValue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdd60c363e30afbe4c61e8e18660a17a06a5ce8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188994"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode obtient le nom de la constante d’énumération en fonction de sa valeur.  
  
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
 dans Valeur pour laquelle obtenir le nom de la constante d’énumération.  
  
 `pbstrValue`  
 à Retourne le nom de la constante d’énumération.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` si la valeur n’a pas de nom associé ou retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si plusieurs noms sont associés à la même valeur, le premier nom défini dans l’énumération est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
