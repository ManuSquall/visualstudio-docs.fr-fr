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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a53148b0130dd05f3ffc3360a518f9b2b66002e7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
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
  
  