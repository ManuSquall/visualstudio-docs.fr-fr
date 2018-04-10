---
title: Fonction de SccBeginBatch | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d6415953a350321cb13f2705fa2bb182c278faa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch (fonction)
Cette fonction démarre une séquence d’opérations de contrôle de code source. Le [SccEndBatch](../extensibility/sccendbatch-function.md) sera appelée pour terminer le lot. Ces lots ne peuvent pas être imbriqués.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Lot d’opérations a démarré avec succès.|  
|SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Lots de contrôle de code source sont utilisées pour exécuter les mêmes opérations sur plusieurs projets ou de plusieurs contextes. Lots peuvent être utilisés pour éliminer les boîtes de dialogue projet redondante à partir de l’expérience utilisateur lors d’une opération par lot. Le `SccBeginBatch` (fonction) et le [SccEndBatch](../extensibility/sccendbatch-function.md) sont utilisés comme une paire de fonctions pour indiquer le début et la fin d’une opération. Ils ne peuvent pas être imbriquées. `SccBeginBatch`définit un indicateur qui indique qu’une opération de traitement par lots est en cours d’exécution.  
  
 Pendant une opération de traitement est en vigueur, le plug-in de contrôle de code source doit présenter au maximum d’une boîte de dialogue pour toute question à l’utilisateur et s’appliquent de la réponse à partir de cette boîte de dialogue sur toutes les opérations suivantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)