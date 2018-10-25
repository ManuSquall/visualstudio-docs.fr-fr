---
title: IDiaDataSource::get_lastError | Microsoft Docs
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
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 853d7177b3d2bae01eb140ce0ddb3046c49470f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837839"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le nom de fichier pour la dernière erreur de chargement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pRetVal  
 [out] Retourne une chaîne qui contient le nom de fichier .pdb associé à la dernière erreur de chargement.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le dernier code d’erreur provoqué par une opération de chargement. Retourne `E_INVALIDARG` si le `pRetVal` paramètre est `NULL`.  
  
## <a name="example"></a>Exemple  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)



