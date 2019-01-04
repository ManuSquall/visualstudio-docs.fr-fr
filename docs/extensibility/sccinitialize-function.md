---
title: Fonction SccInitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d43bdc2be0de233c30d36da445a2b7bee3afbaf2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950035"
---
# <a name="sccinitialize-function"></a>Fonction SccInitialize
Cette fonction initialise le plug-in de contrôle de code source et fournit des fonctionnalités et limites pour l’environnement de développement intégré (IDE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppvContext`  
 [in] Le plug-in de contrôle de code source peut placer un pointeur vers sa structure de contexte ici.  
  
 `hWnd`  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 `lpCallerName`  
 [in] Le nom du programme appelant le contrôle de source de plug-in.  
  
 `lpSccName`  
 [in, out] La mémoire tampon dans lequel le plug-in de contrôle de code source place son propre nom (ne pouvant excéder `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Retourne des indicateurs de capacité du plug-in du contrôle de code source.  
  
 `lpAuxPathLabel`  
 [in, out] La mémoire tampon où le plug-in de contrôle de code source place une chaîne qui décrit le `lpAuxProjPath` paramètre retourné par la [SccOpenProject](../extensibility/sccopenproject-function.md) et [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (ne pouvant excéder `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Retourne la longueur maximale autorisée pour un commentaire d’extraction.  
  
 `pnCommentLen`  
 [out] Retourne la longueur maximale autorisée pour les autres commentaires.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Initialisation du contrôle de code source a réussi.|  
|SCC_E_INITIALIZEFAILED|Système n’a pas pu être initialisé.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer l’opération spécifiée.|  
|SCC_E_NONSPECFICERROR|Échec non spécifique ; système de contrôle de code source n’a pas été initialisé.|  
  
## <a name="remarks"></a>Notes  
 L’IDE appelle cette fonction lors du premier chargement du plug-in de contrôle de code source. Il permet à l’IDE transmettre certaines informations, telles que le nom de l’appelant, le plug-in. L’IDE récupère également certaines informations telles que la longueur maximale autorisée pour les commentaires et les fonctionnalités du plug-in.  
  
 Le `ppvContext` pointe vers un `NULL` pointeur. Le plug-in de contrôle de code source peut allouer une structure pour son propre usage et stocker un pointeur vers cette structure dans `ppvContext`. L’IDE passera ce pointeur à chaque autre fonction VSSCI API, ce qui permet le plug-in pour disposer des informations de contexte sans avoir recours à un stockage global et pour prendre en charge plusieurs instances du plug-in. Cette structure doit être libérée lorsque la [SccUninitialize](../extensibility/sccuninitialize-function.md) est appelée.  
  
 Le `lpCallerName` et `lpSccName` paramètres permettent à l’IDE et le plug-in de contrôle de code source échanger des noms. Ces noms peuvent être utilisés tout simplement pour faire la distinction entre plusieurs instances, ou elles peuvent en fait apparaître dans les menus ou les boîtes de dialogue.  
  
 Le `lpAuxPathLabel` paramètre est une chaîne utilisée comme un commentaire pour identifier le chemin d’accès de projet auxiliaire qui est stocké dans le fichier solution et passé au contrôle de source de plug-in dans un appel à la [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] utilise la chaîne « projet SourceSafe : » ; autres plug-ins de contrôle de code source doit éviter d’utiliser cette chaîne particulière.  
  
 Le `lpSccCaps` paramètre donne le contrôle de source de plug-in pour stocker des indicateurs de bits indiquant les capacités du plug-in. (Pour obtenir une liste complète des bits indicateurs de fonctionnalité, consultez [indicateurs de capacité](../extensibility/capability-flags.md)). Par exemple, si les plans de plug-in pour écrire les résultats dans une fonction de rappel fournie par l’appelant, le plug-in définit la fonctionnalité de bit SCC_CAP_TEXTOUT. Cela serait signaler l’IDE pour créer une fenêtre pour les résultats de contrôle de version.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Indicateurs de capacité](../extensibility/capability-flags.md)