---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4463fc4f9d321b26487e885255843a7acd945f76
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950703"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le nom de l’attribut personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
