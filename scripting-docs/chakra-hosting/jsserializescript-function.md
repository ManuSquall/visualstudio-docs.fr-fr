---
title: "JsSerializeScript, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSerializeScript"
helpviewer_keywords: 
  - "JsSerializeScript (fonction)"
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSerializeScript, fonction
Sérialise un script analysé dans une mémoire tampon qui peut être réutilisée.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### Paramètres  
 `script`  
 Script à sérialiser.  
  
 `buffer`  
 Mémoire tampon dans laquelle placer le script sérialisé.  Peuvent avoir la valeur null.  
  
 `bufferSize`  
 À l'entrée, la taille de la mémoire tampon, en octets. À la sortie, la taille de la mémoire tampon, en octets, nécessaire pour contenir le script sérialisé.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 `JsSerializeScript` analyse un script, puis stocke le formulaire analysé du script dans un format indépendant du runtime.  Le script sérialisé peut ensuite être désérialisé dans n'importe quel runtime sans que le script ne doive être réanalysé.  
  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)