---
title: Fonction de SccWillCreateSccFile | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6a0344177d50d7121b1116e80983db80233dac90
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile (fonction)
Cette fonction détermine si le plug-in de contrôle de code source prend en charge la création de la MSSCCPRJ. Fichier de contrôle de code source pour chacun des fichiers donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 nFiles  
 [in] Le nombre de noms de fichiers inclus dans le `lpFileNames` de tableau, ainsi que la longueur de la `pbSccFiles` tableau.  
  
 lpFileNames  
 [in] Tableau des noms de fichier qualifié complet à vérifier (tableau doit être alloué par l’appelant).  
  
 pbSccFiles  
 [dans, out] Tableau dans lequel stocker les résultats.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Opération réussie.|  
|SCC_E_INVALIDFILEPATH|Parmi les chemins d’accès dans le tableau n’est pas valide.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée avec une liste de fichiers pour déterminer si le plug-in de contrôle de code source fournit la prise en charge dans le MSSCCPRJ. Fichier de contrôle de code source pour chacun des fichiers de donnée (pour plus d’informations sur la MSSCCPRJ. Fichier de contrôle de code source, consultez [MSSCCPRJ. Fichier de contrôle de code source](../extensibility/mssccprj-scc-file.md)). Plug-ins de contrôle de code source peut déclarer si elles disposent de la fonctionnalité de création de MSSCCPRJ. Fichiers SCC en déclarant `SCC_CAP_SCCFILE` lors de l’initialisation. Le plug-in retourne `TRUE` ou `FALSE` par fichier dans le `pbSccFiles` tableau pour indiquer des fichiers donnés qui ont une MSSCCPRJ. Prise en charge du contrôle de code source. Si le plug-in retourne un code de réussite de la fonction, les valeurs dans le tableau de retour sont respectées. En cas d’échec, le tableau est ignoré.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)