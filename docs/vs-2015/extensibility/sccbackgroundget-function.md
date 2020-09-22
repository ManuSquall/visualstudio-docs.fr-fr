---
title: SccBackgroundGet fonction) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 118d8458fd9581a87baea08452d0011d4d66c9a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839545"
---
# <a name="sccbackgroundget-function"></a>Fonction SccBackgroundGet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction récupère, à partir du contrôle de code source, chacun des fichiers spécifiés sans intervention de l’utilisateur.  
  
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
 dans Pointeur de contexte du plug-in de contrôle de code source.  
  
 Nfichiers  
 dans Nombre de fichiers spécifiés dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [in, out] Tableau de noms des fichiers à récupérer.  
  
> [!NOTE]
> Les noms doivent être des noms de fichiers locaux complets.  
  
 dwFlags  
 dans Indicateurs de commande ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).  
  
 dwBackgroundOperationID  
 dans Valeur unique associée à cette opération.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Opération exécutée avec succès.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Une récupération en arrière-plan est déjà en cours (le plug-in de contrôle de code source doit le retourner uniquement s’il ne prend pas en charge les opérations batch simultanées).|  
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant d’être terminée.|  
  
## <a name="remarks"></a>Remarques  
 Cette fonction est toujours appelée sur un thread différent de celui qui a chargé le plug-in de contrôle de code source. Cette fonction ne doit pas être retournée tant qu’elle n’est pas terminée ; Toutefois, elle peut être appelée plusieurs fois avec plusieurs listes de fichiers, en même temps.  
  
 L’utilisation de l' `dwFlags` argument est identique à celle de [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)
