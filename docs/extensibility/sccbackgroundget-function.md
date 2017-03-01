---
title: Fonction de SccBackgroundGet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8bc845c2ef3cb4ece3e52dca272fdc75208e8dbd
ms.lasthandoff: 02/22/2017

---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet (fonction)
Cette fonction extrait à partir du contrôle de code source chaque des fichiers spécifiés sans aucune interaction utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 nFiles  
 [in] Nombre de fichiers spécifié dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [dans, out] Tableau de noms de fichiers à récupérer.  
  
> [!NOTE]
>  Les noms doivent être des noms qualifiés complets.  
  
 dwFlags  
 [in] Indicateurs de commande (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Une valeur unique associée à cette opération.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Opération réussie.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Une récupération en arrière-plan est déjà en cours (le plug-in de contrôle de code source doit retourner ce uniquement s’il ne prend pas en charge les opérations de traitement simultané).|  
|SCC_I_OPERATIONCANCELED|Opération annulée avant terminées.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est toujours appelée sur un thread différent de celui qui a chargé le plug-in de contrôle de code source. Cette fonction n’est pas censée retourner jusqu'à ce que l’opération est terminée ; Toutefois, il peut être appelé plusieurs fois avec plusieurs listes de fichiers, tous en même temps.  
  
 L’utilisation de la `dwFlags` argument est le même que le [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)
