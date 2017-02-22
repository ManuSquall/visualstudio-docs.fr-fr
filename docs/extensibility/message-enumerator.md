---
title: "&#201;num&#233;rateur de message | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "énumérateur de message"
  - "contrôle plug-ins de source, énumération de messages"
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# &#201;num&#233;rateur de message
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les indicateurs suivants sont utilisés pour le `TEXTOUTPROC` fonction, qui est une fonction de rappel que l'IDE fournit lorsqu'il appelle le [SccOpenProject](../extensibility/sccopenproject-function.md) \(voir [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Pour plus d'informations sur la fonction de rappel\).  
  
 Si l'IDE est invité à annuler le processus, il peut obtenir un des messages d'annulation. Dans ce cas, la contrôle du code source du plug\-in utilise `SCC_MSG_STARTCANCEL` pour demander l'IDE pour afficher les **Annuler** bouton. Après cela, n'importe quel jeu de messages normaux peut\-être être envoyé. Si une de ces retourne `SCC_MSG_RTN_CANCEL`, le plug\-in se ferme l'opération et retourne. Le plug\-in interroge également `SCC_MSG_DOCANCEL` régulièrement pour déterminer si l'utilisateur a annulé l'opération. Lorsque toutes les opérations sont effectuées, ou si l'utilisateur a annulé, envoie le plug\-in `SCC_MSG_STOPCANCEL`. Le `SCC_MSG_INFO`, SCC\_MSG\_WARNING, et les types SCC\_MSG\_ERROR sont utilisés pour les messages qui s'affichent dans la liste déroulante des messages.`SCC_MSG_STATUS` est un type spécial qui indique que le texte, qui doit apparaître dans une barre d'état ou de la zone d'affichage temporaire. Il ne reste pas définitivement dans la liste.  
  
## Syntaxe  
  
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
  
## Membres  
 SCC\_MSG\_RTN\_CANCEL  
 Retour de rappel pour indiquer les annuler.  
  
 SCC\_MSG\_RTN\_OK  
 Retour de rappel pour continuer.  
  
 SCC\_MSG\_INFO  
 Est un message d'information.  
  
 SCC\_MSG\_WARNING  
 Message est un avertissement.  
  
 SCC\_MSG\_ERROR  
 Message est une erreur.  
  
 SCC\_MSG\_STATUS  
 Message est destiné à la barre d'état.  
  
 SCC\_MSG\_DOCANCEL  
 Aucun texte ; IDE retourne `SCC_MSG_RTN_OK` ou `SCC_MSG_RTN_CANCEL`.  
  
 SCC\_MSG\_STARTCANCEL  
 Démarre une boucle d'annulation.  
  
 SCC\_MSG\_STOPCANCEL  
 Arrête la boucle d'annulation.  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)