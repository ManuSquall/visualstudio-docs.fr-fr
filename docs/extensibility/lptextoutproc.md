---
title: LPTEXTOUTPROC - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702788"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Lorsque l’utilisateur exécute une opération de contrôle source à partir de l’intérieur de l’environnement de développement intégré (IDE), le plug-in de contrôle source peut vouloir transmettre des messages d’erreur ou d’état relatifs à l’opération. Le plug-in peut afficher ses propres boîtes de messages à cette fin. Cependant, pour une intégration plus transparente, le plug-in peut passer les chaînes à l’IDE, qui les affiche ensuite dans sa façon indigène d’afficher des informations sur l’état. Le mécanisme pour `LPTEXTOUTPROC` cela est le pointeur de fonction. L’IDE implémente cette fonction (décrite plus en détail ci-dessous) pour afficher l’erreur et l’état.

L’IDE passe au plug-in de contrôle source un `lpTextOutProc` pointeur de fonction à cette fonction, comme le paramètre, lors de l’appel de la [SccOpenProject](../extensibility/sccopenproject-function.md). Au cours d’une opération SCC, par exemple, au milieu d’un appel au `LPTEXTOUTPROC` [SccGet](../extensibility/sccget-function.md) impliquant de nombreux fichiers, le plug-in peut appeler la fonction, périodiquement passer des chaînes à afficher. L’IDE peut afficher ces chaînes sur une barre d’état, dans une fenêtre de sortie ou dans une boîte de message séparée, le cas échéant. En option, l’IDE peut afficher certains messages avec un bouton **Annuler.** Cela permet à l’utilisateur d’annuler l’opération, et il donne à l’IDE la possibilité de transmettre ces informations au plug-in.

## <a name="signature"></a>Signature
 La fonction de sortie de l’IDE a la signature suivante :

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Paramètres

display_string

Une chaîne de texte à afficher. Cette corde ne doit pas être terminée avec un retour de chariot ou un flux de ligne.

mesg_type

Type de message. Le tableau suivant répertorie les valeurs prises en charge pour ce paramètre.

|Valeur|Description|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Le message est considéré comme l’information, l’avertissement ou l’erreur.|
|`SCC_MSG_STATUS`|Le message affiche l’état et peut être affiché dans la barre d’état.|
|`SCC_MSG_DOCANCEL`|Envoyé sans chaîne de message.|
|`SCC_MSG_STARTCANCEL`|Commence à afficher un bouton **Annuler.**|
|`SCC_MSG_STOPCANCEL`|Arrête d’afficher un bouton **Annuler.**|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Demande à IDE si l’opération de `SCC_MSG_RTN_CANCEL` fond doit être annulée : IDE revient si l’opération a été annulée; autrement, `SCC_MSG_RTN_OK`les retours . Le `display_string` paramètre est moulé comme une structure [SccMsgDataIsCancelled,](#LinkSccMsgDataIsCancelled) qui est fourni par le plug-in de contrôle source.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informe l’IDE d’un fichier avant qu’il ne soit récupéré à partir du contrôle de la version. Le `display_string` paramètre est présenté sous la forme d’une structure [SccMsgDataOnBeforeGetFile,](#LinkSccMsgDataOnBeforeGetFile) qui est fournie par le plug-in de contrôle source.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Informe l’IDE d’un fichier après avoir été récupéré à partir du contrôle de la version. Le `display_string` paramètre est coulé comme une structure [SccMsgDataOnAfterGetFile,](#LinkSccMsgDataOnAfterGetFile) qui est fourni par le plug-in de contrôle source.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indique à l’IDE l’état actuel d’une opération de fond. Le `display_string` paramètre est présenté comme une structure [SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) qui est fournie par le plug-in de contrôle source.|

## <a name="return-value"></a>Valeur retournée

|Valeur|Description|
|-----------|-----------------|
|SCC_MSG_RTN_OK|La chaîne a été affichée ou l’opération a été complétée avec succès.|
|SCC_MSG_RTN_CANCEL|L’utilisateur veut annuler l’opération.|

## <a name="example"></a>Exemple
 Supposons que l’IDE appelle le [SccGet](../extensibility/sccget-function.md) avec vingt noms de fichiers. Le plug-in de contrôle source veut empêcher l’annulation de l’opération au milieu d’un fichier obtenir. Après avoir reçu chaque `lpTextOutProc`fichier, il appelle, en lui `SCC_MSG_DOCANCEL` passant les informations d’état sur chaque fichier, et envoie un message s’il n’a pas d’état à signaler. Si à tout moment le plug-in `SCC_MSG_RTN_CANCEL` reçoit une valeur de retour de l’IDE, il annule l’opération get immédiatement, de sorte qu’aucun plus de fichiers ne sont récupérés.

## <a name="structures"></a>Structures

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Cette structure est `SCC_MSG_BACKGROUND_IS_CANCELLED` envoyée avec le message. Il est utilisé pour communiquer l’ID de l’opération de fond qui a été annulée.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Cette structure est `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` envoyée avec le message. Il est utilisé pour communiquer le nom du fichier sur le point d’être récupéré et l’identification de l’opération de fond qui effectue la récupération.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAprèsgetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Cette structure est `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` envoyée avec le message. Il est utilisé pour communiquer le résultat de la récupération du fichier spécifié ainsi que l’ID de l’opération de fond qui a effectué la récupération. Voir les valeurs de retour pour le [SccGet](../extensibility/sccget-function.md) pour ce qui peut être donné en conséquence.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Cette structure est `SCC_MSG_BACKGROUND_ON_MESSAGE` envoyée avec le message. Il est utilisé pour communiquer l’état actuel d’une opération de fond. Le statut est exprimé comme une chaîne à `bIsError` afficher par l’IDE, et indique la gravité du message (pour`TRUE` un message d’erreur; `FALSE` pour un avertissement ou pour un message d’information). L’ID de l’opération d’arrière-plan envoyant le statut est également donné.

## <a name="code-example"></a>Exemple de code
 Voici un bref exemple `LPTEXTOUTPROC` d’appel pour envoyer le `SCC_MSG_BACKGROUND_ON_MESSAGE` message, montrant comment jeter la structure de l’appel.

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
- [Fonctions de rappel mises en œuvre par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
