---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cb9ff60968d806cfdee0201746a02483895b0af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée par le code de prise en charge DIA pour charger des octets de données à partir d’un fichier exécutable à l’aide d’un offset de fichier absolu. Cette méthode est appelée à l’appui de la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)