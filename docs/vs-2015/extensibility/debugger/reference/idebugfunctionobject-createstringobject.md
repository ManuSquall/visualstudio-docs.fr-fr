---
title: 'IDebugFunctionObject :: CreateStringObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05f8e77bd019b1bed04ec3a08cda5bbcfefa30ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179435"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un objet String.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CreateStringObject(   
   LPCOLESTR      pcstrString,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateStringObject(  
   string      pcstrString,   
   out IDebugObject ppOjbect  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcstrString`  
 dans Valeur de chaîne de l’objet String.  
  
 `ppObject`  
 à Retourne un objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente l’objet String nouvellement créé.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer un objet qui représente une chaîne qui est un paramètre de la fonction qui est représentée par l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
