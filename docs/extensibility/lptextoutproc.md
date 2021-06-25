---
title: LPTEXTOUTPROC | Microsoft Docs
description: En savoir plus sur le pointeur de fonction LPTEXTOUTPROC. L’IDE de Visual Studio implémente la fonction d’affichage de l’erreur et de l’État.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c313375efe8afd17dd5d76f55de4cdaf016bab40
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903097"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Lorsque l’utilisateur exécute une opération de contrôle de code source à l’intérieur de l’environnement de développement intégré (IDE), le plug-in de contrôle de code source peut souhaiter transmettre des messages d’erreur ou d’État relatifs à l’opération. Le plug-in peut afficher ses propres boîtes de message à cet effet. Toutefois, pour une intégration plus transparente, le plug-in peut passer des chaînes à l’IDE, qui les affiche ensuite dans son mode d’affichage natif des informations d’État. Le mécanisme est le pointeur de `LPTEXTOUTPROC` fonction. L’IDE implémente cette fonction (décrite plus en détail ci-dessous) pour l’affichage de l’erreur et de l’État.

L’IDE passe au plug-in de contrôle de code source un pointeur de fonction vers cette fonction, comme `lpTextOutProc` paramètre, lors de l’appel de [SccOpenProject](../extensibility/sccopenproject-function.md). Au cours d’une opération SCC, par exemple, au milieu d’un appel à [SccGet](../extensibility/sccget-function.md) impliquant de nombreux fichiers, le plug-in peut appeler la `LPTEXTOUTPROC` fonction, en passant régulièrement des chaînes à afficher. L’IDE peut afficher ces chaînes sur une barre d’État, dans une fenêtre de sortie ou dans une boîte de message distincte, selon le cas. Si vous le souhaitez, l’IDE peut être en mesure d’afficher certains messages avec un bouton **Annuler** . Cela permet à l’utilisateur d’annuler l’opération et donne à l’IDE la possibilité de renvoyer ces informations au plug-in.

## <a name="signature"></a>Signature
 La fonction de sortie de l’IDE a la signature suivante :

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Paramètres

display_string

Chaîne de texte à afficher. Cette chaîne ne doit pas se terminer par un retour chariot ou un saut de ligne.

mesg_type

Type de message. Le tableau suivant répertorie les valeurs prises en charge pour ce paramètre.

|Valeur|Description|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Le message est considéré comme information, avertissement ou erreur.|
|`SCC_MSG_STATUS`|Le message affiche État et peut s’afficher dans la barre d’État.|
|`SCC_MSG_DOCANCEL`|Envoyé sans chaîne de message.|
|`SCC_MSG_STARTCANCEL`|Commence à afficher un bouton **Annuler** .|
|`SCC_MSG_STOPCANCEL`|Arrête l’affichage d’un bouton **Annuler** .|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Demande l’IDE si l’opération d’arrière-plan doit être annulée : l’IDE retourne `SCC_MSG_RTN_CANCEL` si l’opération a été annulée ; sinon, retourne `SCC_MSG_RTN_OK` . Le `display_string` paramètre est casté en une structure [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) , qui est fournie par le plug-in de contrôle de code source.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indique à l’IDE à propos d’un fichier avant qu’il ne soit récupéré à partir du contrôle de version. Le `display_string` paramètre est casté en une structure [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) , qui est fournie par le plug-in de contrôle de code source.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indique à l’IDE à propos d’un fichier après qu’il a été récupéré à partir du contrôle de version. Le `display_string` paramètre est casté en une structure [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) , qui est fournie par le plug-in de contrôle de code source.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indique à l’IDE l’état actuel d’une opération d’arrière-plan. Le `display_string` paramètre est casté en une structure [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) , qui est fournie par le plug-in de contrôle de code source.|

## <a name="return-value"></a>Valeur retournée

|Valeur|Description|
|-----------|-----------------|
|SCC_MSG_RTN_OK|La chaîne a été affichée ou l’opération a été effectuée avec succès.|
|SCC_MSG_RTN_CANCEL|L’utilisateur souhaite annuler l’opération.|

## <a name="example"></a>Exemple
 Supposons que l’IDE appelle [SccGet](../extensibility/sccget-function.md) avec vingt noms de fichiers. Le plug-in de contrôle de code source souhaite empêcher l’annulation de l’opération au milieu d’un fichier. Après avoir obtenu chaque fichier, il appelle `lpTextOutProc` , en lui transmettant les informations d’État sur chaque fichier et envoie un `SCC_MSG_DOCANCEL` message s’il n’a pas d’État à signaler. Si, à un moment donné, le plug-in reçoit une valeur de retour de `SCC_MSG_RTN_CANCEL` à partir de l’IDE, il annule immédiatement l’opération d’extraction, afin qu’aucun autre fichier ne soit récupéré.

## <a name="structures"></a>Structures

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Cette structure est envoyée avec le `SCC_MSG_BACKGROUND_IS_CANCELLED` message. Elle est utilisée pour communiquer l’ID de l’opération d’arrière-plan qui a été annulée.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Cette structure est envoyée avec le `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` message. Elle est utilisée pour communiquer le nom du fichier sur le lieu d’être récupéré et l’ID de l’opération d’arrière-plan qui procède à la récupération.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Cette structure est envoyée avec le `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` message. Elle est utilisée pour communiquer le résultat de la récupération du fichier spécifié, ainsi que l’ID de l’opération d’arrière-plan qui a effectué la récupération. Consultez les valeurs de retour de [SccGet](../extensibility/sccget-function.md) pour ce qui peut être donné comme résultat.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Cette structure est envoyée avec le `SCC_MSG_BACKGROUND_ON_MESSAGE` message. Elle est utilisée pour communiquer l’état actuel d’une opération en arrière-plan. L’État est exprimé sous la forme d’une chaîne à afficher par l’IDE et `bIsError` indique la gravité du message ( `TRUE` pour un message d’erreur, `FALSE` un avertissement ou un message d’information). L’ID de l’opération d’arrière-plan qui envoie l’État est également donné.

## <a name="code-example"></a>Exemple de code
 Voici un bref exemple d’appel `LPTEXTOUTPROC` à pour envoyer le `SCC_MSG_BACKGROUND_ON_MESSAGE` message, indiquant comment effectuer un cast de la structure pour l’appel.

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
- [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
