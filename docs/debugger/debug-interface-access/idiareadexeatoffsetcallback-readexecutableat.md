---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44285e1d0ec0210193f196b5436407d8a0c2ff66
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466417"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Lit le nombre spécifié d’octets commençant au décalage spécifié à partir d’un fichier exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 fileOffset  
 [in] Offset dans le fichier exécutable pour commencer la lecture.  
  
 cbData  
 [in] Nombre d’octets à lire.  
  
 pcbData  
 [out] Retourne le nombre d’octets lus.  
  
 données]  
 [dans, out] Tableau qui est rempli avec les octets lus à partir du fichier.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée par le code de prise en charge DIA pour charger des octets de données à partir d’un fichier exécutable à l’aide d’un offset de fichier absolu. Cette méthode est appelée à l’appui de la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)