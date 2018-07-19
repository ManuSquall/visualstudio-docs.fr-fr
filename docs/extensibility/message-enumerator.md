---
title: Énumérateur de message | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bc945908ac61a0eaa4df49c76725b2291686eac3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140260"
---
# <a name="message-enumerator"></a>Énumérateur de message
Les indicateurs suivants sont utilisés pour le `TEXTOUTPROC` fonction, qui est une fonction de rappel que l’IDE fournit lorsqu’il appelle le [SccOpenProject](../extensibility/sccopenproject-function.md) (consultez [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) pour plus d’informations sur le rappel fonction).  
  
 Si l’IDE est invité à annuler le processus, il peut obtenir un des messages d’annulation. Dans ce cas, la contrôle de code source du plug-in utilise `SCC_MSG_STARTCANCEL` demander à l’IDE pour afficher le **Annuler** bouton. Après cela, n’importe quel jeu de messages normaux peut-être être envoyé. Si une des ces retourne `SCC_MSG_RTN_CANCEL`, puis se ferme l’opération du plug-in et le retourne. Le plug-in également interroge `SCC_MSG_DOCANCEL` périodiquement afin de déterminer si l’utilisateur a annulé l’opération. Lorsque toutes les opérations sont effectuées, ou si l’utilisateur a annulé, envoie le plug-in `SCC_MSG_STOPCANCEL`. Le `SCC_MSG_INFO`, SCC_MSG_WARNING, et les types SCC_MSG_ERROR sont utilisés pour les messages qui s’affichent dans la liste déroulante des messages. `SCC_MSG_STATUS` est un type spécial qui indique que le texte doit s’afficher dans une barre d’état ou de la zone d’affichage temporaire. Il ne reste pas définitivement dans la liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Membres  
 SCC_MSG_RTN_CANCEL  
 Retour de rappel pour indiquer l’annuler.  
  
 SCC_MSG_RTN_OK  
 Retour de rappel pour continuer.  
  
 SCC_MSG_INFO  
 Est un message d’information.  
  
 SCC_MSG_WARNING  
 Message est un avertissement.  
  
 SCC_MSG_ERROR  
 Il s’agit d’une erreur de message.  
  
 SCC_MSG_STATUS  
 Message est destiné à la barre d’état.  
  
 SCC_MSG_DOCANCEL  
 Aucun texte ; IDE retourne `SCC_MSG_RTN_OK` ou `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Démarre une boucle de l’annuler.  
  
 SCC_MSG_STOPCANCEL  
 Interrompt la boucle de l’annuler.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)