---
title: LPTEXTOUTPROC | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9fb212d7908d32bc9d9d14d7e8f4786089bc5f89
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Lorsque l’utilisateur exécute une opération de contrôle de code source à partir d’à l’intérieur de l’environnement de développement intégré (IDE), le plug-in de contrôle de code source pouvez souhaiter transmettre les messages d’erreur ou d’état relatives à l’opération. Le plug-in peut afficher ses propres boîtes de message à cet effet. Toutefois, pour une intégration plus transparente, le plug-in peut passer des chaînes à l’IDE, ce qui les affiche ensuite dans sa méthode native d’affichage des informations d’état. Le mécanisme est le `LPTEXTOUTPROC` pointeur de fonction. L’IDE implémente cette fonction (décrite plus en détail ci-dessous) pour afficher l’erreur et état.  
  
 L’IDE passe le contrôle de code source plug-in à cette fonction, un pointeur de fonction en tant que le `lpTextOutProc` paramètre, quand vous appelez le [SccOpenProject](../extensibility/sccopenproject-function.md). Pendant une opération de contrôle de code source, par exemple, au milieu d’un appel à la [SccGet](../extensibility/sccget-function.md) le plug-in impliquant un grand nombre de fichiers, peut appeler le `LPTEXTOUTPROC` fonction régulièrement des chaînes à afficher. L’IDE peut afficher ces chaînes sur une barre d’état dans une fenêtre de sortie, ou dans un message distinct, comme il convient. Si vous le souhaitez, l’IDE peut être en mesure d’afficher certains messages avec un **Annuler** bouton. Cela permet à l’utilisateur d’annuler l’opération, et il permet de l’IDE de transmettre ces informations au plug-in.  
  
## <a name="signature"></a>Signature  
 L’IDE de sortie de la fonction a la signature suivante :  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 display_string  
 Une chaîne de texte à afficher. Cette chaîne n’a pas doit se terminer par un transport de retour ou un saut de ligne.  
  
 mesg_type  
 Type de message. Le tableau suivant répertorie les valeurs prises en charge pour ce paramètre.  
  
|Value|Description|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Le message est considéré comme plus d’informations, avertissement ou erreur.|  
|`SCC_MSG_STATUS`|Le message affiche l’état et peut être affiché dans la barre d’état.|  
|`SCC_MSG_DOCANCEL`|Envoyé avec aucune chaîne de message.|  
|`SCC_MSG_STARTCANCEL`|Commence à afficher un **Annuler** bouton.|  
|`SCC_MSG_STOPCANCEL`|N’est plus affiché un **Annuler** bouton.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Demande IDE si l’opération d’arrière-plan doit être annulée : IDE retourne `SCC_MSG_RTN_CANCEL` si l’opération a été annulée ; sinon, retourne `SCC_MSG_RTN_OK`. Le `display_string` paramètre est casté en un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) structure, qui est fournie par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indique à l’IDE sur un fichier avant d’être récupérée à partir du contrôle de version. Le `display_string` paramètre est casté en un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) structure, qui est fournie par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indique à l’IDE sur un fichier une fois qu’il a été récupéré à partir du contrôle de version. Le `display_string` paramètre est casté en un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) structure, qui est fournie par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|L’IDE de l’état actuel d’une opération d’arrière-plan. Le `display_string` paramètre est casté en un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) structure, qui est fournie par le plug-in de contrôle de code source.|  
  
## <a name="return-value"></a>Valeur de retour  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|La chaîne a été affichée, ou l’opération a réussi.|  
|SCC_MSG_RTN_CANCEL|L’utilisateur souhaite annuler l’opération.|  
  
## <a name="example"></a>Exemple  
 Supposons que les appels de l’IDE le [SccGet](../extensibility/sccget-function.md) avec des noms de fichiers vingt. Le plug-in de contrôle de code source souhaite empêcher l’annulation de l’opération au milieu d’un fichier de get. Après l’obtention de chaque fichier, elle appelle `lpTextOutProc`, en lui passant les informations d’état sur chaque fichier et envoie un `SCC_MSG_DOCANCEL` message si elle n’a aucun état à un rapport. Si à tout moment le plug-in reçoit une valeur de retour de `SCC_MSG_RTN_CANCEL` à partir de l’IDE, il annule l’opération get immédiatement, afin qu’aucun autre fichier n’est récupérées.  
  
## <a name="structures"></a>Structures  
  
###  <a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Cette structure est envoyée avec le `SCC_MSG_BACKGROUND_IS_CANCELLED` message. Il est utilisé pour communiquer l’ID de l’opération d’arrière-plan qui a été annulée.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Cette structure est envoyée avec le `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` message. Il est utilisé pour communiquer le nom du fichier sur le point d’être récupérées et l’ID de l’opération d’arrière-plan qui effectue la récupération.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Cette structure est envoyée avec le `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` message. Il est utilisé pour communiquer le résultat de la récupération du fichier spécifié, ainsi que l’ID de l’opération d’arrière-plan qu’avez effectué la récupération. Consultez les valeurs de retour pour la [SccGet](../extensibility/sccget-function.md) pour ce qui peut être donné en conséquence.  
  
###  <a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Cette structure est envoyée avec le `SCC_MSG_BACKGROUND_ON_MESSAGE` message. Il est utilisé pour communiquer l’état actuel d’une opération d’arrière-plan. L’état est exprimé sous forme de chaîne devant être affiché par l’IDE, et `bIsError` indique la gravité du message (`TRUE` pour un message d’erreur ; `FALSE` pour un avertissement ou un message d’information). L’ID de l’envoi de l’état de l’opération d’arrière-plan est également fourni.  
  
## <a name="code-example"></a>Exemple de code  
 Voici un bref exemple de l’appel de `LPTEXTOUTPROC` pour envoyer le `SCC_MSG_BACKGROUND_ON_MESSAGE` message, en montrant comment effectuer un cast de la structure de l’appel.  
  
```cpp  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)