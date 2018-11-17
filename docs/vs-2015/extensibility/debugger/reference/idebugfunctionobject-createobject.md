---
title: IDebugFunctionObject::CreateObject | Microsoft Docs
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
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78313153ead8f998ed52a0c04ee0a5c919c1eacc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721216"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un objet à l’aide d’un constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objet représentant le constructeur de l’objet doit être créé.  
  
 `dwArgs`  
 [in] Le nombre de paramètres dans le `pArg` tableau. Représente le nombre de paramètres passés au constructeur.  
  
 `pArg`  
 [in] Un tableau de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objets représentant les paramètres transmis au constructeur.  
  
 `ppObject`  
 [out] Retourne un `IDebugObject` représentant l’objet nouvellement créé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe (ou autre type complexe qui nécessite un constructeur) qui est un paramètre à la fonction qui est représentée par le [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
 Si le paramètre d’objet ne nécessite pas un constructeur, appelez le [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)

