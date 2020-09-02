---
title: SccQueryChanges fonction) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200016"
---
# <a name="sccquerychanges-function"></a>Fonction SccQueryChanges
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction énumère une liste donnée de fichiers, en fournissant des informations sur les modifications de nom pour chaque fichier via une fonction de rappel.  
  
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
 dans Pointeur de contexte du plug-in de contrôle de code source.  
  
 Nfichiers  
 dans Nombre de fichiers dans le `lpFileNames` tableau.  
  
 lpFileNames  
 dans Tableau de noms de fichiers à propos desquels obtenir des informations.  
  
 pfnCallback  
 dans Fonction de rappel à appeler pour chaque nom de fichier dans la liste (pour plus d’informations, consultez [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) ).  
  
 pvCallerData  
 dans Valeur qui sera passée sans modification à la fonction de rappel.  
  
## <a name="return-value"></a>Valeur renvoyée  
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Le processus de requête s’est terminé correctement.|  
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert dans le contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention.|  
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|  
  
## <a name="remarks"></a>Notes  
 Les modifications interrogées concernent l’espace de noms : en particulier, en renommant, en ajoutant et en supprimant un fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Codes d’erreur](../extensibility/error-codes.md)
