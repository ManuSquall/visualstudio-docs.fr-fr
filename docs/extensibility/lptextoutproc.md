---
title: LPTEXTOUTPROC | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7229d2681912663ad2cddcf95e140197495c0934
ms.lasthandoff: 02/22/2017

---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Lorsque l’utilisateur exécute une opération de contrôle de code source à partir d’à l’intérieur de l’environnement de développement intégré (IDE), le plug-in de contrôle de code source souhaiterez transmettant les messages d’erreur ou d’état concernant l’opération. Le plug-in peut afficher ses propres boîtes de message à cet effet. Toutefois, pour une intégration plus transparente, le plug-in peut passer des chaînes à l’IDE, qui les affiche ensuite dans sa méthode native de l’affichage des informations d’état. Le mécanisme est le `LPTEXTOUTPROC` (pointeur fonction). L’IDE implémente cette fonction (décrite plus en détail ci-dessous) pour afficher l’erreur et état.  
  
 L’IDE passe le contrôle de code source du plug-in un pointeur de fonction à cette fonction, comme le `lpTextOutProc` paramètre, quand vous appelez le [SccOpenProject](../extensibility/sccopenproject-function.md). Pendant une opération de contrôle de code source, par exemple, au milieu d’un appel à la [SccGet](../extensibility/sccget-function.md) le plug-in impliquant de nombreux fichiers, peut appeler le `LPTEXTOUTPROC` fonction en passant périodiquement des chaînes à afficher. L’IDE peut afficher ces chaînes dans une barre d’état, dans une fenêtre de sortie, ou dans un message distinct, comme il convient. Si vous le souhaitez, l’IDE peut être en mesure d’afficher certains des messages avec un **Annuler** bouton. Cela permet à l’utilisateur d’annuler l’opération, et il permet l’IDE pour transmettre ces informations pour le plug-in.  
  
## <a name="signature"></a>Signature  
 L’IDE de sortie de fonction a la signature suivante :  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 display_string  
 Une chaîne de texte à afficher. Cette chaîne ne doit pas se terminer par un chariot, retour ou un saut de ligne.  
  
 mesg_type  
 Type de message. Le tableau suivant répertorie les valeurs prises en charge pour ce paramètre.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Le message est considéré comme plus d’informations, avertissement ou erreur.|  
|`SCC_MSG_STATUS`|Le message affiche l’état et peut être affiché dans la barre d’état.|  
|`SCC_MSG_DOCANCEL`|Envoyé avec aucune chaîne de message.|  
|`SCC_MSG_STARTCANCEL`|Commence à afficher un **Annuler** bouton.|  
|`SCC_MSG_STOPCANCEL`|N’est plus affiché une **Annuler** bouton.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Demande IDE si l’opération d’arrière-plan doit être annulée : IDE retourne `SCC_MSG_RTN_CANCEL` si l’opération a été annulée ; sinon, retourne `SCC_MSG_RTN_OK`. Le `display_string` paramètre est casté en un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) structure, qui est fourni par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indique à l’environnement IDE relatives à un fichier avant d’être récupérée à partir du contrôle de version. Le `display_string` paramètre est casté en un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) structure, qui est fourni par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indique à l’environnement IDE relatives à un fichier après que qu’il a été récupéré à partir du contrôle de version. Le `display_string` paramètre est casté en un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) structure, qui est fourni par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|L’IDE de l’état actuel d’une opération en arrière-plan. Le `display_string` paramètre est casté en un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) structure, qui est fourni par le plug-in de contrôle de code source.|  
  
## <a name="return-value"></a>Valeur de retour  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|La chaîne a été affichée ou l’opération a réussi.|  
|SCC_MSG_RTN_CANCEL|L’utilisateur souhaite annuler l’opération.|  
  
## <a name="example"></a>Exemple  
 Supposons que les appels IDE la [SccGet](../extensibility/sccget-function.md) avec&20; noms de fichiers. Le plug-in de contrôle de code source souhaite empêcher l’annulation de l’opération en cours d’une opération get fichier. Après la mise en route de chaque fichier, il appelle `lpTextOutProc`, en lui transmettant les informations d’état sur chaque fichier et envoie une `SCC_MSG_DOCANCEL` message s’il n’a aucun état à signaler. Si à tout moment le plug-in reçoit une valeur de retour de `SCC_MSG_RTN_CANCEL` à partir de l’IDE, il annule l’opération d’obtention immédiatement, afin qu’aucun autre fichier n’est récupérées.  
  
## <a name="structures"></a>Structures  
  
###  <a name="a-namelinksccmsgdataiscancelleda-sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Cette structure est envoyée avec la `SCC_MSG_BACKGROUND_IS_CANCELLED` message. Il est utilisé pour communiquer l’ID de l’opération d’arrière-plan qui a été annulée.  
  
###  <a name="a-namelinksccmsgdataonbeforegetfilea-sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Cette structure est envoyée avec la `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` message. Il est utilisé pour communiquer le nom du fichier sur le point d’être récupérées et l’ID de l’opération d’arrière-plan qui effectue la récupération.  
  
###  <a name="a-namelinksccmsgdataonaftergetfilea-sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Cette structure est envoyée avec la `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` message. Il est utilisé pour communiquer le résultat de l’extraction du fichier spécifié, ainsi que l’ID de l’opération d’arrière-plan qui a effectué la récupération. Consultez les valeurs de retour pour la [SccGet](../extensibility/sccget-function.md) pour ce qui peuvent être fourni en conséquence.  
  
###  <a name="a-namelinksccmsgdataonmessagea-sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Cette structure est envoyée avec la `SCC_MSG_BACKGROUND_ON_MESSAGE` message. Il est utilisé pour communiquer l’état actuel d’une opération en arrière-plan. L’état est exprimé sous forme de chaîne s’affiche à l’IDE, et `bIsError` indique la gravité du message (`TRUE` pour un message d’erreur ; `FALSE` pour un avertissement ou un message d’information). L’ID de l’envoi de l’état de l’opération d’arrière-plan est également fourni.  
  
## <a name="code-example"></a>Exemple de code  
 Voici un exemple de l’appel de `LPTEXTOUTPROC` pour envoyer le `SCC_MSG_BACKGROUND_ON_MESSAGE` message, indiquant comment effectuer un cast de la structure de l’appel.  
  
```cpp#  
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
