---
title: "IDebugProcessQueryProperties::QueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties::QueryProperties"
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugProcessQueryProperties::QueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode requêtes pour les valeurs de propriétés spécifiées du processus de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT QueryProperties(  
   ULONG                  celt,  
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,  
   VARIANT               *rgtPropValues);  
```  
  
```c#  
int QueryProperties(  
   uint                       celt,  
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,  
   out object[ ]              rgtPropValues);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Taille des tableaux contenant des définitions et les valeurs de propriété.  
  
 `dwPropType`  
 \[in\]  Un tableau qui contient les définitions des propriétés interrogées.  Les valeurs possibles sont :  
  
-   PROCESS\_PROPERTY\_COMMAND\_LINE \= 1  
  
-   PROCESS\_PROPERTY\_CURRENT\_DIRECTORY \= 2  
  
-   PROCESS\_PROPERTY\_ENVIRONMENT\_VARIABLES \= 3  
  
 `pvarPropValue`  
 \[out\]  Un tableau contenant les valeurs de propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 cette méthode est rarement utilisée.  
  
## Voir aussi  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)