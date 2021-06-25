---
title: Énumérateur de message | Microsoft Docs
description: Les membres de cet énumérateur sont utilisés pour la fonction TEXTOUTPROC, qui est une fonction de rappel fournie par l’IDE lorsqu’il appelle la SccOpenProject.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77c49f79ccdcfc4aa0325b89dfb38f3f8d4da721
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902590"
---
# <a name="message-enumerator"></a>Énumérateur de message
Les indicateurs suivants sont utilisés pour la `TEXTOUTPROC` fonction, qui est une fonction de rappel fournie par l’IDE lorsqu’il appelle le [SccOpenProject](../extensibility/sccopenproject-function.md) (consultez [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) pour plus d’informations sur la fonction de rappel).

 Si l’IDE est invité à annuler le processus, il peut recevoir l’un des messages d’annulation. Dans ce cas, le plug-in de contrôle de code source utilise `SCC_MSG_STARTCANCEL` pour demander à l’IDE d’afficher le bouton **Annuler** . Après cela, tout ensemble de messages normaux peut être envoyé. Si l’un de ces deux retournes `SCC_MSG_RTN_CANCEL` , le plug-in quitte l’opération et retourne. Le plug-in effectue également des interrogations `SCC_MSG_DOCANCEL` périodiques pour déterminer si l’utilisateur a annulé l’opération. Lorsque toutes les opérations sont terminées, ou si l’utilisateur a annulé, le plug-in envoie `SCC_MSG_STOPCANCEL` . Les `SCC_MSG_INFO` types, SCC_MSG_WARNING et SCC_MSG_ERROR sont utilisés pour les messages qui s’affichent dans la liste déroulante de messages. `SCC_MSG_STATUS` est un type spécial qui indique que le texte doit s’afficher dans une barre d’État ou dans une zone d’affichage temporaire. Elle n’est pas conservée de manière permanente dans la liste.

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
 SCC_MSG_RTN_CANCEL retourner à partir du rappel pour indiquer l’annulation.

 SCC_MSG_RTN_OK retourner du rappel pour continuer.

 SCC_MSG_INFO message est informatif.

 SCC_MSG_WARNING message est un avertissement.

 SCC_MSG_ERROR message est une erreur.

 SCC_MSG_STATUS message est destiné à la barre d’État.

 SCC_MSG_DOCANCEL pas de texte ; L’IDE retourne `SCC_MSG_RTN_OK` ou `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL démarre une boucle d’annulation.

 SCC_MSG_STOPCANCEL arrête la boucle d’annulation.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
