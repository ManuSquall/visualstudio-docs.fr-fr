---
title: POPDIRLISTFUNC | Microsoft Docs
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
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4afd84af0ab6d7f801c486dd506ca5d5a10f6909
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867960"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il s’agit d’une fonction de rappel donnée à la [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) (fonction) pour mettre à jour une collection de répertoires et (éventuellement) des noms de fichiers qui sont sous contrôle de code source.  
  
 Le `POPDIRLISTFUNC` rappel doit être appelé uniquement pour les répertoires et les noms de fichiers (dans la liste donnée à la `SccPopulateDirList` (fonction)) qui sont réellement sous contrôle de code source.  
  
## <a name="signature"></a>Signature  
  
```cpp#  
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
 [in] `TRUE` si le nom dans `lpDirectoryOrFileName` est un répertoire ; sinon, le nom est un nom de fichier.  
  
 lpDirectoryOrFileName  
 [in] Chemin d’accès local complet à un nom de répertoire ou fichier est sous contrôle de code source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’IDE retourne un code d’erreur approprié :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Continuer le traitement.|  
|SCC_I_OPERATIONCANCELED|Arrêter le traitement.|  
|SCC_E_xxx|Une erreur de contrôle de source approprié doit arrêter le traitement.|  
  
## <a name="remarks"></a>Notes  
 Si le `fOptions` paramètre de la `SccPopulateDirList` fonction contient le `SCC_PDL_INCLUDEFILES` indicateur, puis la liste contient éventuellement les noms de fichiers, ainsi que des noms de répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Codes d’erreur](../extensibility/error-codes.md)

