---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77e4701d3d8ec54fd37d6483f55b10a28af65b15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194053"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il s’agit d’une fonction de rappel donnée à la fonction [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) pour mettre à jour une collection de répertoires et (éventuellement) des noms de fichiers pour déterminer ceux qui sont sous contrôle de code source.  
  
 Le `POPDIRLISTFUNC` rappel doit être appelé uniquement pour les répertoires et les noms de fichiers (dans la liste donnée à la `SccPopulateDirList` fonction) qui sont en fait sous contrôle de code source.  
  
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
 dans Valeur utilisateur donnée à [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bFolder  
 [in] `TRUE` Si le nom dans `lpDirectoryOrFileName` est un répertoire ; sinon, le nom est un nom de fichier.  
  
 lpDirectoryOrFileName  
 dans Chemin d’accès local complet à un répertoire ou à un nom de fichier qui est sous le contrôle de code source.  
  
## <a name="return-value"></a>Valeur renvoyée  
 L’IDE retourne un code d’erreur approprié :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Continuer le traitement.|  
|SCC_I_OPERATIONCANCELED|Arrêter le traitement.|  
|SCC_E_xxx|Toute erreur de contrôle de code source appropriée doit arrêter le traitement.|  
  
## <a name="remarks"></a>Notes  
 Si le `fOptions` paramètre de la `SccPopulateDirList` fonction contient l' `SCC_PDL_INCLUDEFILES` indicateur, la liste peut contenir des noms de fichiers, ainsi que des noms de répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Codes d’erreur](../extensibility/error-codes.md)
