---
title: IEEDataStorage::GetData | Microsoft Docs
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
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d23ecbc348d4aab4fdbbb83abaaba54fdad345
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751084"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère le nombre spécifié d’octets à partir de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in, out] Tableau à remplir avec les données demandées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’utilisation de cette méthode consiste à récupérer tous les octets de données dans un tableau local, dans la mesure où il n’existe aucun moyen d’ignorer les octets dans le processus d’extraction. Dans ce cas, le paramètre `dataSize` doit être la valeur retournée par la [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

