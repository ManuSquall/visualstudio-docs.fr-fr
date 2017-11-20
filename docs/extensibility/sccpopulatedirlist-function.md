---
title: Fonction de SccPopulateDirList | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccPopulateDirList
helpviewer_keywords: SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec22eaeaf24af1c65823c64c65dd2c39f1003ec8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList (fonction)
Cette fonction détermine les répertoires et (facultativement) les fichiers sont stockés dans le contrôle de code source, une liste de répertoires à examiner.  
  
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
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 nDirs  
 [in] Nombre de chemins d’accès de répertoire dans le `lpDirPaths` tableau.  
  
 lpDirPaths  
 [in] Tableau des chemins d’accès à examiner.  
  
 pfnPopulate  
 [in] Fonction de rappel à appeler pour chaque chemin d’accès de répertoire et (facultatif) nom de fichier dans `lpDirPaths` (consultez [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) pour plus d’informations).  
  
 pvCallerData  
 [in] Valeur qui doit être transmis sans modification à la fonction de rappel.  
  
 fOptions  
 [in] Une combinaison de valeurs qui contrôlent la façon dont les répertoires sont traités (consultez la section « Indicateurs PopulateDirList » de [indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour les valeurs possibles).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|L’opération terminée.|  
|SCC_E_UNKNOWNERROR|Une erreur s'est produite.|  
  
## <a name="remarks"></a>Remarques  
 Seuls les répertoires et (éventuellement) des noms de fichiers qui sont réellement dans le référentiel de contrôle de code source sont passés à la fonction de rappel.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Codes d’erreur](../extensibility/error-codes.md)