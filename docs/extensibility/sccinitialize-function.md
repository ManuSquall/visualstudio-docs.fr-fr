---
title: "SccInitialize (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccInitialize"
helpviewer_keywords: 
  - "SccInitialize (fonction)"
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccInitialize (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction initialise le plug\-in de contrôle de code source et fournit des fonctionnalités et les limites de l'environnement de développement intégré \(IDE\).  
  
## Syntaxe  
  
```cpp#  
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
  
#### Paramètres  
 `ppvContext`  
 \[in\] Le plug\-in de contrôle de code source peut placer un pointeur vers la structure de contexte ici.  
  
 `hWnd`  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 `lpCallerName`  
 \[in\] Nom du programme qui appelle le contrôle de code source du plug\-in.  
  
 `lpSccName`  
 \[dans, out\] La mémoire tampon où le plug\-in de contrôle de code source met son propre nom \(pour ne pas dépasser `SCC_NAME_LEN`\).  
  
 `lpSccCaps`  
 \[out\] Retourne des indicateurs du plug\-in du contrôle de code source.  
  
 `lpAuxPathLabel`  
 \[dans, out\] La mémoire tampon où le plug\-in de contrôle de code source met une chaîne qui décrit le `lpAuxProjPath` paramètre retourné par la [SccOpenProject](../extensibility/sccopenproject-function.md) et [SccGetProjPath](../extensibility/sccgetprojpath-function.md) \(pour ne pas dépasser `SCC_AUXLABEL_LEN`\).  
  
 `pnCheckoutCommentLen`  
 \[out\] Retourne la longueur maximale autorisée pour un commentaire d'extraction.  
  
 `pnCommentLen`  
 \[out\] Retourne la longueur maximale autorisée pour les autres commentaires.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Initialisation du contrôle de code source a réussi.|  
|SCC\_E\_INITIALIZEFAILED|Système n'a pas pu être initialisé.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer l'opération spécifiée.|  
|SCC\_E\_NONSPECFICERROR|Erreur non spécifique ; système de contrôle de code source n'a pas été initialisé.|  
  
## Notes  
 L'IDE appelle cette fonction lors du premier chargement du plug\-in de contrôle de code source. Il permet à l'IDE transmettre certaines informations, telles que le nom de l'appelant, le plug\-in. L'IDE permet d'obtenir des informations telles que la longueur maximale autorisée pour les commentaires et le plug\-in.  
  
 Le `ppvContext` pointe vers un `NULL` pointeur. Le plug\-in de contrôle de code source peut allouer une structure pour son propre usage et stocker un pointeur vers cette structure dans `ppvContext`. L'IDE passe ce pointeur pour chaque autre fonction VSSCI API, autorisant le plug\-in pour que les informations de contexte disponibles sans avoir recours à un stockage global et prendre en charge plusieurs instances du plug\-in. Cette structure doit être libérée lorsque la [SccUninitialize](../extensibility/sccuninitialize-function.md) est appelée.  
  
 Le `lpCallerName` et `lpSccName` paramètres permettent à l'IDE et le plug\-in de contrôle de code source échanger des noms. Ces noms peuvent être utilisés tout simplement pour faire la distinction entre plusieurs instances, ou ils peuvent réellement apparaissent dans les menus ou les boîtes de dialogue.  
  
 Le `lpAuxPathLabel` paramètre est une chaîne utilisée comme un commentaire pour identifier le chemin d'accès de projet auxiliaire qui est stocké dans le fichier solution et passé au contrôle de source de plug\-in dans un appel à la [SccOpenProject](../extensibility/sccopenproject-function.md).[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] utilise la chaîne « projet SourceSafe: » ; autres plug\-ins de contrôle de code source doit éviter d'utiliser cette chaîne particulière.  
  
 Le `lpSccCaps` paramètre donne le contrôle de code source du plug\-in pour stocker des indicateurs de bits indiquant les capacités du plug\-in. \(Pour obtenir une liste complète des indicateurs de bits de capacité, consultez [Indicateurs de capacité](../extensibility/capability-flags.md)\). Par exemple, si les plans de plug\-in pour écrire les résultats dans une fonction de rappel fournie par l'appelant, le plug\-in définit la fonctionnalité de bit SCC\_CAP\_TEXTOUT. Cela serait signaler l'IDE pour créer une fenêtre de résultats du contrôle de version.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Indicateurs de capacité](../extensibility/capability-flags.md)