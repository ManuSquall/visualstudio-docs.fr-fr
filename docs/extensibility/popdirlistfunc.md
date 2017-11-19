---
title: POPDIRLISTFUNC | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: POPLISTFUNC
helpviewer_keywords: POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d5279f16dbc8228f0f116c47e6faa3ab0093472
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Il s’agit d’une fonction de rappel à la [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) (fonction) pour mettre à jour un ensemble de répertoires et (éventuellement) des noms de fichiers qui sont sous contrôle de code source.  
  
 Le `POPDIRLISTFUNC` rappel doit être appelé uniquement pour les répertoires et les noms de fichiers (dans la liste donnée à le `SccPopulateDirList` fonction) qui sont en réalité sous contrôle de code source.  
  
## <a name="signature"></a>Signature  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 pvCallerData  
 [in] Valeur d’utilisateur donnée [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bOptions  
 [in] `TRUE` si le nom de `lpDirectoryOrFileName` est un répertoire ; sinon, le nom est un nom de fichier.  
  
 lpDirectoryOrFileName  
 [in] Chemin d’accès complet à un nom de répertoire ou fichier est sous contrôle de code source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’IDE retourne un code d’erreur approprié :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Continuer le traitement.|  
|SCC_I_OPERATIONCANCELED|Arrêter le traitement.|  
|SCC_E_xxx|Une erreur de contrôle de source approprié doit arrêter le traitement.|  
  
## <a name="remarks"></a>Remarques  
 Si le `fOptions` paramètre de la `SccPopulateDirList` fonction contient le `SCC_PDL_INCLUDEFILES` indicateur, la liste contient éventuellement les noms de fichiers, ainsi que des noms de répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Codes d’erreur](../extensibility/error-codes.md)