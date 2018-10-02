---
title: IDebugObject::GetValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7db441f27ba8e095b3f45b404a670efa5f785713
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502831"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugObject::GetValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-getvalue).  
  
Obtient la valeur de l’objet sous la forme d’une série consécutive d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pValue`  
 [in, out] Tableau qui contient une série consécutive d’octets représentant la valeur de l’objet.  
  
 `nSize`  
 [in] Le nombre maximal d’octets à extraire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Obtenir le nombre total d’octets de valeur peuvent être extraites en appelant le [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

