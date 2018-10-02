---
title: LPTEXTOUTPROC | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e8fc709353e4a2e39059cade96aa49c30fedac4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505813"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [LPTEXTOUTPROC](https://docs.microsoft.com/visualstudio/extensibility/lptextoutproc).  
  
Lorsque l’utilisateur exécute une opération de contrôle de code source à partir d’à l’intérieur de l’environnement de développement intégré (IDE), le plug-in de contrôle de code source pouvez souhaiter transmettre les messages d’erreur ou d’état concernant l’opération. Le plug-in peut afficher ses propres boîtes de message à cet effet. Toutefois, pour une intégration plus transparente, le plug-in peut passer des chaînes à l’IDE, ce qui les affiche ensuite dans ses moyen natif d’affichage des informations d’état. Le mécanisme est le `LPTEXTOUTPROC` pointeur de fonction. L’IDE implémente cette fonction (décrite plus en détail ci-dessous) pour afficher l’erreur et état.  
  
 L’IDE transmet le contrôle de source de plug-in un pointeur de fonction à cette fonction, comme le `lpTextOutProc` paramètre, quand vous appelez le [SccOpenProject](../extensibility/sccopenproject-function.md). Pendant une opération de contrôle de code source, par exemple, au milieu d’un appel à la [SccGet](../extensibility/sccget-function.md) le plug-in impliquant de nombreux fichiers, peut appeler le `LPTEXTOUTPROC` fonction en passant périodiquement des chaînes à afficher. L’IDE peut afficher ces chaînes sur une barre d’état dans une fenêtre de sortie, ou dans un message distinct, comme il convient. Si vous le souhaitez, l’IDE peut être en mesure d’afficher certains messages avec un **Annuler** bouton. Cela permet à l’utilisateur d’annuler l’opération, et vous offre l’IDE la possibilité de transmettre ces informations au plug-in.  
  
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
 Une chaîne de texte à afficher. Cette chaîne ne doit pas se terminer avec un chariot, retour ou un saut de ligne.  
  
 mesg_type  
 Type de message. Le tableau suivant répertorie les valeurs prises en charge pour ce paramètre.  
  
|Value|Description|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Le message est considéré comme plus d’informations, avertissement ou erreur.|  
|`SCC_MSG_STATUS`|Le message affiche l’état et peut être affiché dans la barre d’état.|  
|`SCC_MSG_DOCANCEL`|Envoyé avec aucune chaîne de message.|  
|`SCC_MSG_STARTCANCEL`|Commence à afficher un **Annuler** bouton.|  
|`SCC_MSG_STOPCANCEL`|N’est plus affiché une **Annuler** bouton.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Demande IDE si l’opération d’arrière-plan doit être annulée : IDE retourne `SCC_MSG_RTN_CANCEL` si l’opération a été annulée ; sinon, retourne `SCC_MSG_RTN_OK`. Le `display_string` paramètre est casté en un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) structure, qui est fourni par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indique à l’IDE sur un fichier avant d’être récupérée à partir du contrôle de version. Le `display_string` paramètre est casté en un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) structure, qui est fourni par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indique à l’IDE sur un fichier une fois qu’elles ont été récupérées à partir du contrôle de version. Le `display_string` paramètre est casté en un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) structure, qui est fourni par le plug-in de contrôle de code source.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|L’IDE de l’état actuel d’une opération d’arrière-plan. Le `display_string` paramètre est casté en un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) structure, qui est fourni par le plug-in de contrôle de code source.|  
  
## <a name="return-value"></a>Valeur de retour  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|La chaîne a été affichée, ou l’opération a réussi.|  
|SCC_MSG_RTN_CANCEL|L’utilisateur souhaite annuler l’opération.|  
  
## <a name="example"></a>Exemple  
 Supposons que les appels de l’IDE le [SccGet](../extensibility/sccget-function.md) avec 20 noms de fichiers. Le plug-in de contrôle de code source souhaite empêcher l’annulation de l’opération au milieu d’une opération get fichier. Après avoir obtenu chaque fichier, il appelle `lpTextOutProc`, en lui passant les informations d’état sur chaque fichier et envoie un `SCC_MSG_DOCANCEL` message si elle n’a aucun état à signaler. Si à tout moment le plug-in reçoit une valeur de retour de `SCC_MSG_RTN_CANCEL` à partir de l’IDE, il annule l’opération get immédiatement, afin qu’aucun autre fichier n’est récupérées.  
  
## <a name="structures"></a>Structures  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Cette structure est envoyée avec la `SCC_MSG_BACKGROUND_IS_CANCELLED` message. Il est utilisé pour communiquer l’ID de l’opération d’arrière-plan qui a été annulée.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Cette structure est envoyée avec la `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` message. Il est utilisé pour communiquer le nom du fichier sur le point d’être récupérées et l’ID de l’opération d’arrière-plan qui effectue la récupération.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Cette structure est envoyée avec la `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` message. Il est utilisé pour communiquer le résultat de la récupération du fichier spécifié, ainsi que l’ID de l’opération d’arrière-plan qui a effectué la récupération. Consultez les valeurs de retour pour la [SccGet](../extensibility/sccget-function.md) pour ce qui peut être donné en conséquence.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Cette structure est envoyée avec la `SCC_MSG_BACKGROUND_ON_MESSAGE` message. Il est utilisé pour communiquer l’état actuel d’une opération d’arrière-plan. L’état est exprimé sous forme de chaîne à afficher par l’IDE, et `bIsError` indique la gravité du message (`TRUE` pour un message d’erreur ; `FALSE` pour un avertissement ou un message d’information). L’ID de l’opération d’arrière-plan que le statut d’envoi est également donnée.  
  
## <a name="code-example"></a>Exemple de code  
 Voici un exemple rapide de l’appel `LPTEXTOUTPROC` pour envoyer le `SCC_MSG_BACKGROUND_ON_MESSAGE` message, montrant comment effectuer un cast de la structure pour l’appel.  
  
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

