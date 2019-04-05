---
title: Fonction SccQueryChanges | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: baa6059a1668be5507994921cb96ac3ed1cfd5fe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953518"
---
# <a name="sccquerychanges-function"></a>Fonction SccQueryChanges
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction énumère une liste de fichiers, en fournissant des informations sur les changements de nom pour chaque fichier via une fonction de rappel donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte de plug-in de contrôle de code source.  
  
 nFiles  
 [in] Nombre de fichiers dans `lpFileNames` tableau.  
  
 lpFileNames  
 [in] Tableau de noms de fichiers pour obtenir des informations.  
  
 pfnCallback  
 [in] Fonction de rappel à appeler pour chaque nom de fichier dans la liste (voir [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) pour plus d’informations).  
  
 pvCallerData  
 [in] Valeur qui est transmis sans modification à la fonction de rappel.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Le processus de requête s’est terminé correctement.|  
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert dans le contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|  
  
## <a name="remarks"></a>Notes  
 Les modifications en cours d’interrogation sont à l’espace de noms : en particulier, changement de nom, l’ajout et suppression d’un fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Codes d’erreur](../extensibility/error-codes.md)
