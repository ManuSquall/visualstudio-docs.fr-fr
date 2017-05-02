---
title: "SCRIPTPROP_HOSTKEEPALIVE, propri&#233;t&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPTPROP_HOSTKEEPALIVE, propri&#233;t&#233;
Utilisé pour spécifier si le moteur de script doit être conservé entièrement fonctionnel \- si des références en cours.  
  
 Utilisez [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) pour définir cette propriété avec `true`.  Si cette propriété a `true`, le moteur de script est maintenu entièrement fonctionnel \- tant qu'il y a au moins une référence en cours ou au moteur de script lui\-même ou un pointeur d' `IDispatch` à un objet JavaScript créé à l'aide de le moteur de script.  Lorsque cette propriété a `true`, vous ne devez pas explicitement fermer ou de réinitialiser le moteur de script à l'aide de les méthodes d' [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) ou d' [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) .  La version finale de la dernière référence à un objet de script ferme le moteur de script.  
  
## Syntaxe  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## Configuration requise  
 Cette propriété apparaît uniquement dans la version d'activscp.idl qui est installé avec [!INCLUDE[win8](../../javascript/includes/win8-md.md)], avec le Ko 2707082 pour Internet Explorer 8 sur [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], ou avec le Ko 2722913 pour Internet Explorer 9 sur [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] ou [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].