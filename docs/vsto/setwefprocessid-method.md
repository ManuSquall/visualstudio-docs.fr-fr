---
title: Setwefprocessid, méthode
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7807d0495c5f0548178b1bc2ecae12d57cc3b072
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876120"
---
# <a name="setwefprocessid-method"></a>Setwefprocessid, méthode
  Fournit l’identificateur de processus qui exécutera le contenu de l’infrastructure d’Extensions Web (WEF).  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*dwProcessId*|L’identificateur de processus qui sera utilisé pour exécuter le contenu WEF.|  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur HRESULT qui indique si la méthode a réussi.  
  
## <a name="remarks"></a>Notes  
 Cette méthode doit être appelée une fois le processus de contenu WEF est créé, mais avant l’exécution de n’importe quel contenu WEF.  
  
 Si vous souhaitez que l’environnement de développement pour attacher un débogueur au processus contenu WEF, l’environnement doit effectuer cette opération dans votre implémentation de cette méthode.  
