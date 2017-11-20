---
title: Fonction de SccEnumChangedFiles | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccEnumChangedFiles
helpviewer_keywords: SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ad62f14ea658e4af6e22d4beef410e6d9cf02df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles (fonction)
Obtenez la liste des fichiers locaux, cette fonction détermine quels fichiers sont différents dans les versions correspondantes dans la base de données de contrôle de code source.  
  
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
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 cFiles  
 [in] Nombre de noms de fichier spécifiés dans le `lpFileNames` tableau. Spécifie également la taille de `plIsFileDifferent` tableau.  
  
 lpFileNames  
 [in] Tableau des noms de fichier local à vérifier.  
  
 plIsFileDifferent  
 [dans, out] Tableau de valeurs indiquant l’état de la différence de chaque fichier (tableau doit avoir au moins `cFiles` entrées). Différent de zéro signifie que le fichier est différent.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Opération achevée avec succès.|  
|SCC_UNSPECIFIEDERROR|Erreur générique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)