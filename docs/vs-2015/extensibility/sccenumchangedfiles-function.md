---
title: SccEnumChangedFiles fonction) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200125"
---
# <a name="sccenumchangedfiles-function"></a>Fonction SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

À partir de la liste des fichiers locaux, cette fonction détermine les fichiers qui sont différents des versions correspondantes dans la base de données de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 dans Pointeur de contexte du plug-in de contrôle de code source.  
  
 hWnd  
 dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 cFiles  
 dans Nombre de noms de fichiers spécifiés dans le `lpFileNames` tableau. Spécifie également la taille du `plIsFileDifferent` tableau.  
  
 lpFileNames  
 dans Tableau de noms de fichiers locaux à vérifier.  
  
 plIsFileDifferent  
 [in, out] Tableau de valeurs indiquant l’état de différence de chaque fichier (le tableau doit avoir au moins `cFiles` entrées). Une valeur différente de zéro signifie que le fichier est différent.  
  
## <a name="return-value"></a>Valeur renvoyée  
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Opération exécutée avec succès.|  
|SCC_UNSPECIFIEDERROR|Erreur générique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
