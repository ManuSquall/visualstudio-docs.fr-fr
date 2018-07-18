---
title: Fonction de SccEndBatch | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec549b5bb0a6c48946edf59f0ab1423cea0ac704
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138221"
---
# <a name="sccendbatch-function"></a>SccEndBatch (fonction)
Cette fonction termine un lot d’opérations de contrôle de code source. Ces lots ne peuvent pas être imbriqués.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Lot d’opérations conclu avec succès.|  
|SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Lots de contrôle de code source sont utilisés pour exécuter les opérations de contrôle de source même entre plusieurs projets ou de plusieurs contextes. Lots peuvent être utilisés pour éliminer des boîtes de dialogue redondante à partir de l’expérience utilisateur lors d’une opération par lot. Le [SccBeginBatch](../extensibility/sccbeginbatch-function.md) et `SccEndBatch` (fonction) sont utilisés en tant que paire pour indiquer le début et la fin d’une opération. Ils ne peuvent pas être imbriquées.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)