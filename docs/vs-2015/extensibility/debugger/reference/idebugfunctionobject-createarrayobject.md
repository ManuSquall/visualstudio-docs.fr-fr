---
title: 'IDebugFunctionObject :: CreateArrayObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205819"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un objet tableau. Ce tableau peut contenir des valeurs de l’instance primitive ou Object.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ot`  
 dans Spécifie une valeur de l’énumération [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) indiquant le type du nouvel objet tableau.  
  
 `pClassField`  
 dans Objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente la classe d’un objet, en cas de création d’un tableau de valeurs d’instance d’objet. En cas de création d’un tableau d’objets primitifs, ce paramètre est une valeur null.  
  
 `dwRank`  
 dans Rang ou nombre de dimensions du tableau.  
  
 `dwDims`  
 dans Tailles de chaque dimension du tableau.  
  
 `dwLowBounds`  
 dans Origine de chaque dimension (généralement 0 ou 1).  
  
 `ppObject`  
 à Retourne un objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente le tableau nouvellement créé. Il s’agit en fait d’un objet [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer un objet qui représente un paramètre de tableau pour la fonction qui est représentée par l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
