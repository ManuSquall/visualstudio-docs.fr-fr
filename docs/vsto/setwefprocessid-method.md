---
title: "Setwefprocessid, méthode | Documents Microsoft"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0821c799a4d6385997704724c00a2aff4669eb17
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="setwefprocessid-method"></a>SetWefProcessId, méthode
  Fournit l’identificateur de processus qui s’exécutera le contenu Web Extensions Framework (WEF).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*dwProcessId*|L’identificateur de processus qui servira à exécuter le contenu WEF.|  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur HRESULT qui indique si la méthode a réussi.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode doit être appelée une fois le processus de contenu WEF est créé, mais avant l’exécution de n’importe quel contenu WEF.  
  
 Si vous souhaitez que l’environnement de développement pour attacher un débogueur au processus contenu WEF, l’environnement doit effectuer cette opération dans votre implémentation de cette méthode.  
  
  