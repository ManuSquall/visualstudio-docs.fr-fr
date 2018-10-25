---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69afacf68c77dcb2bca7c951dbd2a1ee9a344cfb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917276"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Lit le nombre spécifié d’octets à partir du spécifié adresse virtuelle relative (RVA) à partir du fichier exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `relativeVirtualAddress`  
 [in] L’adresse RVA dans le fichier exécutable à commencer la lecture.  
  
 `cbData`  
 [in] Nombre d’octets à lire.  
  
 `pcbData`  
 [out] Retourne le nombre d’octets lus.  
  
 `data[]`  
 [in, out] Un tableau est rempli avec les octets lus à partir du fichier.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée par le code de prise en charge DIA pour charger des octets de données à partir d’un fichier exécutable à l’aide d’une adresse virtuelle relative. Cette méthode est appelée à l’appui de la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)