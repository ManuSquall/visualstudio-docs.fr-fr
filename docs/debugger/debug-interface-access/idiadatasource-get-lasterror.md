---
title: IDiaDataSource::get_lastError | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9458f287d39dac2a1e8e571aeee3926bdf181823
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Récupère le nom de fichier pour la dernière erreur de chargement.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pRetVal  
 [out] Retourne une chaîne qui contient le nom du fichier .pdb associé à la dernière erreur de chargement.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le dernier code d’erreur provoqué par une opération de chargement. Retourne `E_INVALIDARG` si le `pRetVal` paramètre est `NULL`.  
  
## <a name="example"></a>Exemple  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)