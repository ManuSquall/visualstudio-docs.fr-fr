---
title: IDebugFunctionObject::CreateObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b0b9a36dfac48d86963db68c3ab68500d8b8bfba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Crée un objet à l’aide d’un constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pConstructor`  
 [in] Un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objet représentant le constructeur de l’objet à créer.  
  
 `dwArgs`  
 [in] Le nombre de paramètres dans le `pArg` tableau. Représente le nombre de paramètres transmis au constructeur.  
  
 `pArg`  
 [in] Un tableau de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objets représentant les paramètres passés au constructeur.  
  
 `ppObject`  
 [out] Retourne un `IDebugObject` représentant l’objet qui vient d’être créé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe (ou un autre type complexe qui nécessite un constructeur) qui est un paramètre à la fonction qui est représentée par le [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
 Si le paramètre d’objet ne nécessite pas un constructeur, appelez le [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)