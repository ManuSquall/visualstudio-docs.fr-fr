---
title: Fonction SccPopulateDirList | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 031735127fe648be72b221461ae9dbab15929446
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286974"
---
# <a name="sccpopulatedirlist-function"></a>Fonction SccPopulateDirList
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction détermine les répertoires et (éventuellement) les fichiers sont stockés dans le contrôle de code source, une liste de répertoires à examiner.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte de plug-in de contrôle de code source.  
  
 nDirs  
 [in] Nombre de chemins d’accès de répertoire dans le `lpDirPaths` tableau.  
  
 lpDirPaths  
 [in] Tableau de chemins de répertoires à examiner.  
  
 pfnPopulate  
 [in] Fonction de rappel à appeler pour chaque chemin d’accès de répertoire et (éventuellement) nom de fichier dans `lpDirPaths` (consultez [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) pour plus d’informations).  
  
 pvCallerData  
 [in] Valeur qui doit être transmises sans modification à la fonction de rappel.  
  
 Options  
 [in] Une combinaison de valeurs qui contrôlent la façon dont les répertoires sont traités (consultez la section « Indicateurs PopulateDirList » de [indicateurs de bits utilisés par les commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour les valeurs possibles).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|L’opération terminée.|  
|SCC_E_UNKNOWNERROR|Une erreur s'est produite.|  
  
## <a name="remarks"></a>Notes  
 Uniquement les répertoires et (éventuellement) les noms de fichiers qui sont réellement dans le référentiel de contrôle source sont passés à la fonction de rappel.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Codes d’erreur](../extensibility/error-codes.md)

