---
title: Fonction SccEnumChangedFiles | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200125"
---
# <a name="sccenumchangedfiles-function"></a>Fonction SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtenez la liste des fichiers locaux, cette fonction détermine quels fichiers sont différents des versions correspondantes dans la base de données de contrôle de code source.  
  
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
 [in] Le pointeur de contexte de plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 cFiles  
 [in] Nombre de noms de fichiers spécifié dans le `lpFileNames` tableau. Spécifie également la taille de `plIsFileDifferent` tableau.  
  
 lpFileNames  
 [in] Tableau des noms de fichier local à vérifier.  
  
 plIsFileDifferent  
 [in, out] Tableau de valeurs indiquant l’état de la différence de chaque fichier (tableau doit avoir au moins `cFiles` entrées). Valeur différente de zéro signifie que le fichier est différent.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Opération exécutée avec succès.|  
|SCC_UNSPECIFIEDERROR|Erreur générique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
