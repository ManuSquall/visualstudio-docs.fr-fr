---
title: IDebugProcessQueryProperties::QueryProperty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperty
ms.assetid: 9a91707d-a590-44ef-b122-69d9816a7a79
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 72f91d6cf8554567807e958ae9a32b93f9228c8f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951987"
---
# <a name="idebugprocessquerypropertiesqueryproperty"></a>IDebugProcessQueryProperties::QueryProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Requêtes de cette méthode pour une valeur de propriété spécifiée du processus de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT QueryProperty(  
   PROCESS_PROPERTY_TYPE  dwPropType,  
   VARIANT               *pvarPropValue);  
```  
  
```csharp  
int QueryProperty(  
   enum_PROCESS_PROPERTY_TYPE dwPropType,  
   out object                 pvarPropValue);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwPropType`  
 [in] Définition de la propriété interrogée. Les valeurs sont les suivantes :  
  
- PROCESS_PROPERTY_COMMAND_LINE = 1  
  
- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2  
  
- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3  
  
  `pvarPropValue`  
  [out] La valeur de la propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est rarement utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
