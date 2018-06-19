---
title: IDiaEnumSegments::Clone | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3198e21440d2fc20898fde83925aaf8ae0e3a3be
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457775"
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Clone (   
   IDiaEnumSegments** ppenum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 ppenum  
 [out] Retourne un [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) objet qui contient une copie de l’énumérateur. Les segments ne sont pas dupliquées, seulement l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)