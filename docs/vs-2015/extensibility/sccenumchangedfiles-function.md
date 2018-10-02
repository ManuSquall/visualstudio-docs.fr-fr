---
title: Fonction SccEnumChangedFiles | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d1935724a965d7b7d62e6bc059c0d483bb3a1b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504749"
---
# <a name="sccenumchangedfiles-function"></a>Fonction SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fonction SccEnumChangedFiles](https://docs.microsoft.com/visualstudio/extensibility/sccenumchangedfiles-function).  
  
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
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Opération achevée avec succès.|  
|SCC_UNSPECIFIEDERROR|Erreur générique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)

