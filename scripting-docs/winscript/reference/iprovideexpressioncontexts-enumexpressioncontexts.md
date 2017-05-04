---
title: "IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProvideExpressionContexts.EnumExpressionContexts
apilocation: jscript.dll
helpviewer_keywords: 
  - "IProvideExpressionContexts::EnumExpressionContexts"
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts::EnumExpressionContexts
Retourne un énumérateur des contextes d'expression connus par ce composant.  
  
## Syntaxe  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### Paramètres  
 `ppedec`  
 \[out\]  un énumérateur des contextes d'expression connus par ce composant.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Le processus de débogage utilise de gestionnaire cette méthode pour rechercher tous les contextes globaux d'expression associés à un thread donné.  
  
> [!NOTE]
>  Cette méthode est appelée du thread concerné.  Elle appartient à l'implémenteur pour identifier le thread actuel et pour retourner un énumérateur approprié.  
  
## Voir aussi  
 [IProvideExpressionContexts, interface](../../winscript/reference/iprovideexpressioncontexts-interface.md)