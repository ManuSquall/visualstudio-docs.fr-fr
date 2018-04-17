---
title: Getautoinsertextensions, méthode | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67f6bfcb0ee38acf9abb604f28fa95eeaa605fde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
  