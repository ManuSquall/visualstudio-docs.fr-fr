---
title: "SccOpenProject (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccOpenProject"
helpviewer_keywords: 
  - "SccOpenProject (fonction)"
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccOpenProject (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction ouvre un projet de contrôle de code source existant ou crée un nouveau.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpUser  
 \[dans, out\] Le nom de l'utilisateur \(à ne pas dépasser SCC\_USER\_SIZE, y compris le terminateur NULL\).  
  
 lpProjName  
 \[in\] Chaîne identifiant le nom du projet.  
  
 lpLocalProjPath  
 \[in\] Le chemin d'accès au dossier de travail pour le projet.  
  
 lpAuxProjPath  
 \[dans, out\] Chaîne facultative auxiliaire identifiant le projet \(ne dépassant pas SCC\_AUXPATH\_SIZE, y compris le terminateur NULL\).  
  
 lpComment  
 \[in\] Commentaire à un nouveau projet est créé.  
  
 lpTextOutProc  
 \[in\] Une fonction de rappel facultative pour afficher le texte de sortie à partir du plug\-in de contrôle de code source.  
  
 dwFlags  
 \[in\] Indique si un projet doit être créé si le projet est inconnu de la source de contrôle plug\-in. Valeur peut être une combinaison de `SCC_OP_CREATEIFNEW` et `SCC_OP_SILENTOPEN.`  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Réussite de l'ouverture du projet.|  
|SCC\_E\_INITIALIZEFAILED|Projet n'a pas pu être initialisé.|  
|SCC\_E\_INVALIDUSER|L'utilisateur n'a pas pu se connecter le système de contrôle source.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Le projet n'existait pas avant l'appel.  le `SCC_OPT_CREATEIFNEW` indicateur a été défini, mais le projet n'a pas pu être créé.|  
|SCC\_E\_PROJSYNTAXERR|Syntaxe de projet non valide.|  
|SCC\_E\_UNKNOWNPROJECT|Le projet est inconnu pour le plug\-in de contrôle de code source et le `SCC_OPT_CREATEIFNEW` indicateur n'a pas été défini.|  
|SCC\_E\_INVALIDFILEPATH|Chemin d'accès de fichier non valide ou inutilisable.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_NONSPECFICERROR|Une erreur non spécifique ; le système de contrôle de code source n'a pas été initialisé.|  
  
## Notes  
 L'IDE peut transmettre un nom d'utilisateur \(`lpUser`\), ou il peut simplement passer un pointeur vers une chaîne vide. S'il existe un nom d'utilisateur, le plug\-in de contrôle de code source doit l'utiliser comme valeur par défaut. Toutefois, si aucun nom n'a été passé, ou si la connexion a échoué avec le nom donné, le plug\-in doit inviter l'utilisateur à se connecter et retourne le nom valid dans `lpUser` lorsqu'elle reçoit une connexion valide`.` car le plug\-in peut changer la chaîne de nom d'utilisateur, l'IDE sera toujours allouer un tampon de taille \(`SCC_USER_LEN`\+ 1 ou SCC\_USER\_SIZE, qui inclut l'espace pour le terminateur null\).  
  
> [!NOTE]
>  La première action que l'IDE peut\-être être nécessaires pour exécuter peut être un appel à la `SccOpenProject` fonction ou [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Pour cette raison, les deux ont une même `lpUser` paramètre.  
  
 `lpAuxProjPath` et`lpProjName` sont lues à partir du fichier solution, ou ils sont retournés à partir d'un appel à la `SccGetProjPath` \(fonction\). Ces paramètres contiennent les chaînes qui associe les le plug\-in de contrôle de code source avec le projet et pertinents pour le plug\-in. Si aucune de ces chaînes ne sont dans le fichier solution et l'utilisateur n'a pas été invité à naviguer \(qui retourne une chaîne via la `SccGetProjPath` fonction\), l'IDE passe des chaînes vides pour les deux `lpAuxProjPath` et `lpProjName`, et attend que ces valeurs à mettre à jour par le plug\-in lorsque cette fonction retourne.  
  
 `lpTextOutProc` est un pointeur vers une fonction de rappel fournie par l'IDE pour le plug\-in en vue d'afficher la sortie de résultat de commande de contrôle de code source. Cette fonction de rappel est décrite en détail dans [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Si le plug\-in de contrôle de code source prévoit d'en tirer parti, il doit avoir le `SCC_CAP_TEXTOUT` indicateur dans le [SccInitialize](../extensibility/sccinitialize-function.md). Si cet indicateur n'a pas été défini, ou si l'IDE ne prend pas en charge cette fonctionnalité, `lpTextOutProc` sera `NULL`.  
  
 Le `dwFlags` paramètre contrôle le résultat dans le cas où le projet en cours d'ouverture n'existe pas actuellement. Il se compose de deux indicateurs de bits, `SCC_OP_CREATEIFNEW` et `SCC_OP_SILENTOPEN`. Si le projet est déjà ouvert existe, la fonction ouvre le projet et le renvoie `SCC_OK`. Si le projet n'existe pas et si le `SCC_OP_CREATEIFNEW` indicateur est activé, le plug\-in de contrôle de code source peut créer le projet dans le système de contrôle de code source, ouvrez\-le et retourner `SCC_OK`. Si le projet n'existe pas et si le `SCC_OP_CREATEIFNEW` indicateur est désactivée, le plug\-in doit ensuite vérifier le `SCC_OP_SILENTOPEN` indicateur. Si cet indicateur est désactivée, le plug\-in peut inviter l'utilisateur à un nom de projet. Si cet indicateur est activé, le plug\-in doit simplement renvoyer `SCC_E_UNKNOWNPROJECT`.  
  
## Ordre d'appel  
 Dans le cadre normal des événements, le [SccInitialize](../extensibility/sccinitialize-function.md) est appelée en premier pour ouvrir une session de contrôle de code source. Une session peut se composer d'un appel à `SccOpenProject`, suivi d'autres appels de fonction API de plug\-in de contrôle de code Source et se termine par un appel à la [SccCloseProject](../extensibility/scccloseproject-function.md). Ces sessions peuvent être répétées plusieurs fois avant la [SccUninitialize](../extensibility/sccuninitialize-function.md) est appelée.  
  
 Si la source de contrôle plug\-in définit la `SCC_CAP_REENTRANT` bit dans `SccInitialize`, puis la séquence de session ci\-dessus peut être répétée autant de fois en parallèle. Autre `pvContext` structures suivre les sessions différentes, dans lequel chaque `pvContext` est associé à un projet ouvert à la fois. Selon la`pvContext` paramètre, le plug\-in peut déterminer de quel projet est référencé dans un appel particulier. Si le bit de la fonction `SCC_CAP_REENTRANT` n'est pas définie, nonreentrant plug\-ins de contrôle de code source sont limités dans leur capacité à travailler avec plusieurs projets.  
  
> [!NOTE]
>  Le `SCC_CAP_REENTRANT` bits a été introduite dans la version 1.1 de l'API de plug\-in de contrôle de Source. Il n'est pas définie ou est ignoré dans la version 1.0, et toutes les version 1.0 contrôle plug\-ins de source sont supposés pour être nonreentrant.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Restrictions relatives aux longueurs de chaîne](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)