---
title: IDiaEnumFrameData::Clone | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8bd5ac8a9af2ff06e8095dda1c4724f5f76d9b51
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466654"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 ppenum  
 [out] Retourne un [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) objet qui contient une copie de l’énumérateur. Le frame de données ne sont pas dupliquée, seulement l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)