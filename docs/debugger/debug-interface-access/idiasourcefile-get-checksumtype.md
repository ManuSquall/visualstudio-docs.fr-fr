---
title: IDiaSourceFile::get_checksumType | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fafd9e813c22b899603a2e62c5a2c90ece1a709
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Récupère le type de somme de contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le type de somme de contrôle.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le type de somme de contrôle est une valeur qui peut être mappée à un algorithme de somme de contrôle. Par exemple, le format de fichier PDB standard généralement peut avoir une des valeurs suivantes :  
  
|Type de somme de contrôle|Étiquette de CryptoAPI|Description|  
|-------------------|---------------------|-----------------|  
|0|\<Aucun >|Aucune somme de contrôle présent.|  
|1|`CALG_MD5`|somme de contrôle généré avec l’algorithme de hachage MD5.|  
|2|`CALG_SHA1`|somme de contrôle généré avec l’algorithme de hachage SHA1.|  
  
 Le `CryptoAPI` sont des étiquettes à partir de la `ALG_ID` énumération. Pour plus d’informations sur les algorithmes de hachage, consultez la `CryptoAPI` section de Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Pour obtenir les octets de somme de contrôle réelle du fichier source, appelez le [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)