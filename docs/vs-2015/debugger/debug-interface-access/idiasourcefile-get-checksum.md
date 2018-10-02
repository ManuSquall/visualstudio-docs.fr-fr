---
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4c8ce89bd4cfe42be0fc67897a4545ecbe6a8a2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506997"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaSourceFile::get_checksum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasourcefile-get-checksum).  
  
Récupère les octets de la somme de contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbData`  
 [in] Taille de la mémoire tampon de données, en octets.  
  
 `pcbData`  
 [out] Retourne le nombre d’octets de la somme de contrôle. Ce paramètre ne peut pas être `NULL`.  
  
 `data`  
 [in, out] Une mémoire tampon est remplie avec les octets de la somme de contrôle. Si ce paramètre est `NULL`, puis `pcbData` retourne le nombre d’octets requis.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Pour déterminer le type d’algorithme de somme de contrôle qui a été utilisé pour générer les octets de la somme de contrôle, appelez le [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) (méthode).  
  
 La somme de contrôle est généralement généré à partir de l’image du fichier source afin de modifications dans le fichier source sont répercutées dans les modifications dans les octets de la somme de contrôle. Si les octets de la somme de contrôle ne correspondent pas à une somme de contrôle généré à partir de l’image chargée du fichier, puis le fichier doit être considéré comme endommagé ou falsifié.  
  
 Sommes de contrôle standard ne sont jamais plus de 32 octets taille mais ne supposent pas qui est la taille maximale d’une somme de contrôle. Définir le `data` paramètre `NULL` pour obtenir le nombre d’octets requis pour récupérer la somme de contrôle. Allouer une mémoire tampon de la taille appropriée, puis appelez cette méthode une fois de plus, avec la nouvelle mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)



