---
title: Getautoinsertextensions, méthode
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
ms.openlocfilehash: 7e3e0fda420682e4f33c0d22a3e9c8caa920895b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672892"
---
# <a name="getautoinsertextensions-method"></a>Getautoinsertextensions, méthode
  Obtient des informations sur les applications pour Office qui doivent être insérés automatiquement pendant le débogage.  
  
 Cette méthode est réservée à une utilisation ultérieure.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*psaExtensionNames*|Les noms d’extension des applications pour Office.|  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur HRESULT qui indique si la méthode a réussi.  
  
## <a name="remarks"></a>Notes  
 Chaque application pour Office doit être inséré est retournée comme un nom d’extension application Office, ce qui correspond à une valeur sous **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. L’hôte doit rechercher ces valeurs dans le Registre et puis insère automatiquement les extensions.  
  
  