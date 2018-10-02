---
title: IDebugGenericFieldDefinition::TypeParamCount | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2863a0c5d252cc2ace87b28f4f384796e98289ee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505912"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugGenericFieldDefinition::TypeParamCount](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount).  
  
Récupère le nombre de paramètres de type qui sont associés au champ générique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT TypeParamCount(  
   ULONG32* pcParams  
);  
```  
  
```csharp  
int TypeParamCount(  
   ref uint pcParams  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcParams`  
 [in, out] Nombre de paramètres de type.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si liste\<T >, cette méthode retourne 1 et, s’il liste\<T1, T2 >, cette méthode retourne la valeur 2. Cette méthode retourne 0 si aucun paramètre de type.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)

