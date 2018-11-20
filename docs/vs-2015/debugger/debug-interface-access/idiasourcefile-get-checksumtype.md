---
title: IDiaSourceFile::get_checksumType | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 374528b1e48077ba7cd4c1bc25a5cb6d1e87c661
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724819"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le type de somme de contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le type de somme de contrôle.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le type de somme de contrôle est une valeur qui peut être mappée à un algorithme de somme de contrôle. Par exemple, le format de fichier PDB standard généralement peut avoir une des valeurs suivantes :  
  
|Type de somme de contrôle|Étiquette de CryptoAPI|Description|  
|-------------------|---------------------|-----------------|  
|0|\<Aucun >|Aucune somme de contrôle présent.|  
|1|`CALG_MD5`|somme de contrôle généré avec l’algorithme de hachage MD5.|  
|2|`CALG_SHA1`|somme de contrôle généré avec l’algorithme de hachage SHA1.|  
  
 Le `CryptoAPI` sont des étiquettes à partir de la `ALG_ID` énumération. Pour plus d’informations sur les algorithmes de hachage, consultez la `CryptoAPI` section de Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)].  
  
 Pour obtenir les octets de la somme de contrôle réelle du fichier source, appelez le [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)



