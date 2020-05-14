---
title: Enumérateur de messages ( fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702504"
---
# <a name="message-enumerator"></a>Enumérateur de message
Les drapeaux suivants sont `TEXTOUTPROC` utilisés pour la fonction, qui est une fonction de rappel que l’IDE fournit lorsqu’il appelle le [SccOpenProject](../extensibility/sccopenproject-function.md) (voir [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) pour plus de détails sur la fonction de rappel).

 Si l’IDE est invité à annuler le processus, il peut obtenir l’un des messages d’annulation. Dans ce cas, le plug-in de contrôle source utilise `SCC_MSG_STARTCANCEL` pour demander à l’IDE d’afficher le bouton **Annuler.** Après cela, tout ensemble de messages normaux peut être envoyé. Si l’un `SCC_MSG_RTN_CANCEL`de ces retours, alors le plug-in quitte l’opération et revient. Le plug-in `SCC_MSG_DOCANCEL` permet également de déterminer périodiquement si l’utilisateur a annulé l’opération. Lorsque toutes les opérations sont terminées, ou si l’utilisateur a annulé, le plug-in envoie `SCC_MSG_STOPCANCEL`. Les `SCC_MSG_INFO`types , SCC_MSG_WARNING et SCC_MSG_ERROR sont utilisés pour les messages qui s’affichent dans la liste de défilement des messages. `SCC_MSG_STATUS`est un type spécial qui indique que le texte doit apparaître dans une barre d’état ou une zone d’affichage temporaire. Il ne reste pas en permanence dans la liste.

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
 SCC_MSG_RTN_CANCEL Retour du rappel pour indiquer l’annulation.

 SCC_MSG_RTN_OK Retour de rappel pour continuer.

 SCC_MSG_INFO Message est informationnel.

 SCC_MSG_WARNING Message est un avertissement.

 SCC_MSG_ERROR Message est une erreur.

 SCC_MSG_STATUS Message est destiné à la barre de statut.

 SCC_MSG_DOCANCEL Pas de texte; IDE `SCC_MSG_RTN_OK` revient ou `SCC_MSG_RTN_CANCEL`.

 SCC_MSG_STARTCANCEL démarre une boucle d’annulation.

 SCC_MSG_STOPCANCEL Arrête la boucle d’annulation.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
