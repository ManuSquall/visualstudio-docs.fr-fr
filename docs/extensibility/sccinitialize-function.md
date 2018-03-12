---
title: Fonction de SccInitialize | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6bf217218dcc1830cc2acf2833aa7e31e85745d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sccinitialize-function"></a>SccInitialize (fonction)
Cette fonction initialise le plug-in de contrôle de code source et offre des fonctionnalités et les limites de l’environnement de développement intégré (IDE).  
  
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
 [in] Le plug-in de contrôle de code source peut placer un pointeur vers la structure de son contexte ici.  
  
 `hWnd`  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 `lpCallerName`  
 [in] Le nom du programme appelant le contrôle de source de plug-in.  
  
 `lpSccName`  
 [dans, out] La mémoire tampon où le plug-in de contrôle de code source met son propre nom (pour ne pas dépasser `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Retourne des indicateurs du plug-in du contrôle de code source.  
  
 `lpAuxPathLabel`  
 [dans, out] La mémoire tampon où le plug-in de contrôle de code source place une chaîne qui décrit le `lpAuxProjPath` paramètre renvoyé par le [SccOpenProject](../extensibility/sccopenproject-function.md) et [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (pour ne pas dépasser `SCC_AUXLABEL_LEN`).  
  
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
|SCC_E_NONSPECFICERROR|Erreur non spécifique ; système de contrôle de code source n’a pas été initialisé.|  
  
## <a name="remarks"></a>Notes  
 L’IDE appelle cette fonction lors du premier chargement du plug-in de contrôle de code source. Il permet à l’IDE passer de certaines informations, telles que le nom de l’appelant, le plug-in. L’IDE permet d’obtenir des informations telles que la longueur maximale autorisée pour les commentaires et les fonctionnalités du plug-in.  
  
 Le `ppvContext` pointe vers un `NULL` pointeur. Le plug-in de contrôle de code source peut allouer une structure pour son propre usage et stocker un pointeur vers cette structure dans `ppvContext`. L’IDE passe ce pointeur à chaque autre fonction VSSCI API, ce qui permet le plug-in pour que les informations de contexte disponibles sans avoir recours au stockage global et pour prendre en charge plusieurs instances de plug-in. Cette structure doit être libérée lorsque la [SccUninitialize](../extensibility/sccuninitialize-function.md) est appelée.  
  
 Le `lpCallerName` et `lpSccName` paramètres permettent l’IDE et le plug-in de contrôle de code source échanger des noms. Ces noms peuvent être utilisés simplement faire la distinction entre plusieurs instances, ou elles peuvent en fait apparaître dans les menus ou les boîtes de dialogue.  
  
 Le `lpAuxPathLabel` paramètre est une chaîne utilisée comme un commentaire pour identifier le chemin d’accès de projet auxiliaire qui est stocké dans le fichier solution et passé le contrôle de source de plug-in dans un appel à la [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]utilise la chaîne « projet SourceSafe : » ; autres plug-ins de contrôle de code source ne doit pas à l’aide de cette chaîne particulière.  
  
 Le `lpSccCaps` paramètre donne le contrôle de source de plug-in pour stocker des indicateurs de bits indiquant les fonctionnalités du plug-in. (Pour obtenir une liste complète des indicateurs de bits de capacité, consultez [indicateurs](../extensibility/capability-flags.md)). Par exemple, si les plans de plug-in pour écrire les résultats dans une fonction de rappel fournie par l’appelant, le plug-in est définie à la fonctionnalité de bit SCC_CAP_TEXTOUT. Cela serait indiquent l’IDE pour créer une fenêtre de résultats de contrôle de version.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Indicateurs de capacité](../extensibility/capability-flags.md)