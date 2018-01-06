---
title: IDebugClassField::EnumNestedEnums | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumNestedEnums
helpviewer_keywords: IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8bdf03df64b88673404de9b6129569822c4aa31f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Crée un énumérateur pour les énumérateurs imbriqués de cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des énumérations imbriquées. Retourne une valeur null s’il n’y aucun énumérations imbriquées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou retourne S_FALSE, s’il n’y a aucune énumérateurs imbriqués. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque élément de l’énumération est un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objet décrivant une énumération imbriquée.  
  
 Une énumération déclarée à l’intérieur d’une classe est considérée comme une énumération imbriquée. Par exemple, soit :  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 Le `EnumNestedEnums` méthode retournerait une [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet qui contient un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objet qui représente le `NestedEnum` énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)