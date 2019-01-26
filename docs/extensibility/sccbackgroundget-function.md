---
title: Fonction SccBackgroundGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6afce798e327e21bf2613a84d717bab3a737d05a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975684"
---
# <a name="sccbackgroundget-function"></a>Fonction SccBackgroundGet
Cette fonction récupère à partir du contrôle de code source chaque des fichiers spécifiés sans aucune interaction utilisateur.  
  
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
  
### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte de plug-in de contrôle de code source.  
  
 nFiles  
 [in] Nombre de fichiers spécifiés dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [in, out] Tableau des noms de fichiers à récupérer.  
  
> [!NOTE]
>  Les noms doivent être qualifiés complets des noms de fichiers local.  
  
 dwFlags  
 [in] Indicateurs de commande (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Une valeur unique associée à cette opération.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Opération achevée avec succès.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Une récupération en arrière-plan est déjà en cours (le plug-in de contrôle de code source doit retourner ce uniquement si elle ne prend pas en charge les opérations de traitement simultané).|  
|SCC_I_OPERATIONCANCELED|Opération a été annulée avant d’en cours terminée.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est toujours appelée sur un thread différent de celui qui a chargé le plug-in de contrôle de code source. Cette fonction n’est pas censée retourner jusqu'à ce que l’opération est terminée ; Toutefois, elle peut être appelée plusieurs fois avec plusieurs listes de fichiers, tous en même temps.  
  
 L’utilisation de la `dwFlags` argument est le même que le [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)