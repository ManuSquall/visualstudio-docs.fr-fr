---
title: "Getautoinsertextensions, méthode | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cef8de366b812baee96ba889cc26157594d55954
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions, méthode
  Obtient des informations sur les applications pour Office qui doivent être insérés automatiquement pendant le débogage.  
  
 Cette méthode est réservée à une utilisation ultérieure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*psaExtensionNames*|Les noms d’extension des applications pour Office.|  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur HRESULT qui indique si la méthode a réussi.  
  
## <a name="remarks"></a>Notes  
 Chaque application pour Office à insérer est retournée comme un nom d’extension application Office, ce qui correspond à une valeur sous HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer. L’ordinateur hôte doit rechercher ces valeurs dans le Registre et insérez ensuite automatiquement les extensions.  
  
  