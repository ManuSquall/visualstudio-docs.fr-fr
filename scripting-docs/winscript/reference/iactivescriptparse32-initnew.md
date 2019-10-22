---
title: 'IActiveScriptParse32 :: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561661"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32 :: InitNew
Initialise le moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_FAIL` si une erreur s’est produite lors de l’initialisation.  
  
## <a name="remarks"></a>Notes  
 Avant de pouvoir utiliser le moteur de script, vous devez appeler l’une des méthodes suivantes : `IPersist*::Load`, `IPersist*::InitNew` ou `IActiveScriptParse32::InitNew`. La sémantique de cette méthode est identique à `IPersistStreamInit::InitNew`, car cette méthode indique au moteur de script de s’initialiser. Notez qu’il n’est pas possible d’appeler à la fois `IPersist*::InitNew` ou `IActiveScriptParse32::InitNew` et `IPersist*::Load`, ni d’appeler `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` ou `IPersist*::Load` plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)