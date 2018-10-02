---
title: Fonction SccWillCreateSccFile | Microsoft Docs
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
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79fd34f742309fe94a329e75d78a57cf551b3a85
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503074"
---
# <a name="sccwillcreatesccfile-function"></a>Fonction SccWillCreateSccFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fonction SccWillCreateSccFile](https://docs.microsoft.com/visualstudio/extensibility/sccwillcreatesccfile-function).  
  
Cette fonction détermine si le plug-in de contrôle de code source prend en charge la création de la MSSCCPRJ. Fichier de contrôle de code source pour chacun des fichiers donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte de plug-in de contrôle de code source.  
  
 nFiles  
 [in] Le nombre de noms de fichiers inclus dans le `lpFileNames` tableau ainsi que la longueur de la `pbSccFiles` tableau.  
  
 lpFileNames  
 [in] Un tableau de noms de fichier qualifié complet à vérifier (tableau doit être alloué par l’appelant).  
  
 pbSccFiles  
 [in, out] Tableau dans lequel stocker les résultats.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Opération réussie.|  
|SCC_E_INVALIDFILEPATH|Parmi les chemins d’accès dans le tableau n’est pas valide.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée avec une liste de fichiers pour déterminer si le plug-in de contrôle de code source fournit la prise en charge dans le MSSCCPRJ. Fichier de contrôle de code source pour chacun des fichiers données (pour plus d’informations sur la MSSCCPRJ. Fichier de contrôle de code source, consultez [MSSCCPRJ. Fichier de SCC](../extensibility/mssccprj-scc-file.md)). Plug-ins de contrôle de code source peut déclarer s’ils ont la capacité de création MSSCCPRJ. Fichiers SCC en déclarant `SCC_CAP_SCCFILE` pendant l’initialisation. Le plug-in retourne `TRUE` ou `FALSE` par fichier dans le `pbSccFiles` tableau pour indiquer quels fichiers donnés ayant MSSCCPRJ. Prise en charge du contrôle de code source. Si le plug-in retourne un code de réussite de la fonction, les valeurs dans le tableau de résultats sont respectées. En cas d’échec, le tableau est ignoré.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)

