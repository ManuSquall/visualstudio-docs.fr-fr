---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11a4b986799cf03221b4af077fc3e1e5809c4137
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866478"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Obtient le nom de l’attribut personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bstrName`  
 [out] Retourne une chaîne contenant le nom de l’attribut personnalisé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Nommé retourné par cette méthode correspond au nom de la classe utilisée pour déclarer l’attribut. Pas exactement cela peut correspondre au nom de la classe d’attributs personnalisés lui-même, car c# permet le suffixe « Attribute » à supprimer à partir d’un nom d’attribut personnalisé lorsqu’elle est utilisée dans une déclaration.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)