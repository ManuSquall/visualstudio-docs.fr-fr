---
title: Fonction de SccRunScc | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRunScc
helpviewer_keywords: SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9ac82ac0363428ade1b6010a9060e15284db224
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccrunscc-function"></a>SccRunScc (fonction)
Cette fonction appelle l’outil d’administration de contrôle source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 nFiles  
 [in] Nombre de fichiers spécifiés dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [in] Tableau des noms de fichier sélectionné.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|L’outil administration de contrôle de code source a été appelé avec succès.|  
|SCC_I_OPERATIONCANCELED|L’opération a été annulée.|  
|SCC_E_INITIALIZEFAILED|Impossible d’initialiser le système de contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC_E_CONNECTIONFAILURE|Impossible de se connecter au système de contrôle de code source.|  
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Remarques  
 Cette fonction permet à l’appelant pour accéder à la gamme complète des fonctionnalités du système de contrôle de code source via un outil d’administration externe. Si le système de contrôle de code source n’a aucune interface utilisateur, le plug-in de contrôle de code source peut implémenter une interface pour effectuer des fonctions d’administration nécessaires.  
  
 Cette fonction est appelée avec un nombre et un tableau de noms de fichiers pour les fichiers actuellement sélectionnés. Si l’outil d’administration prend en charge, la liste des fichiers peut servir à présélectionner des fichiers dans l’interface d’administration ; dans le cas contraire, la liste peut être ignorée.  
  
 Cette fonction est généralement appelée lorsque l’utilisateur sélectionne le **lancer \<Source Control Server >** à partir de la **fichier** -> **contrôle de code Source** menu. Cela **lancer** option de menu permettre être toujours désactivée ou masquée en définissant une entrée de Registre. Consultez [Comment : installer un plug-in de contrôle de code Source](../extensibility/internals/how-to-install-a-source-control-plug-in.md) pour plus d’informations. Cette fonction est appelée uniquement si [SccInitialize](../extensibility/sccinitialize-function.md) retourne le `SCC_CAP_RUNSCC` bits de capacité (consultez [indicateurs](../extensibility/capability-flags.md) pour plus d’informations sur les autres bits de fonctionnalité).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Comment : installer un plug-in de contrôle de code Source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Indicateurs de capacité](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)