---
title: IEEDataStorage::GetData | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ddbc77950396df743b88ce3b6c1a94bbeaf8126
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120853"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Récupère le nombre spécifié d’octets à partir de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dataSize`  
 [in] Le nombre d’octets à récupérer (la `data` tableau doit contenir au moins ce nombre d’octets).  
  
 `sizeGotten`  
 [out] Retourne le nombre d’octets réellement récupérées.  
  
 `data`  
 [dans, out] Tableau à remplir avec les données demandées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Est de l’utilisation recommandée de cette méthode pour récupérer tous les octets de données dans un tableau local, car il n’existe aucun moyen d’ignorer les octets dans le processus de récupération. Dans ce cas, le paramètre `dataSize` doit être la valeur retournée par la [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)