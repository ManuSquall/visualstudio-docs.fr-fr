---
title: Setwefprocessid, méthode
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
ms.openlocfilehash: b426237816bfee53e7c3e50c19e29168b27e16e1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693430"
---
# <a name="setwefprocessid-method"></a>Setwefprocessid, méthode
  Fournit l’identificateur de processus qui s’exécutera le contenu Web Extensions Framework (WEF).  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
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
  
## <a name="remarks"></a>Notes  
 Cette méthode doit être appelée une fois le processus de contenu WEF est créé, mais avant l’exécution de n’importe quel contenu WEF.  
  
 Si vous souhaitez que l’environnement de développement pour attacher un débogueur au processus contenu WEF, l’environnement doit effectuer cette opération dans votre implémentation de cette méthode.  
  
  