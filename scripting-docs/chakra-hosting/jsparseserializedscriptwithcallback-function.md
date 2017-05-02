---
title: "JsParseSerializedScriptWithCallback, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a93ecfb-4b82-4a85-b24c-6816db2332ea
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsParseSerializedScriptWithCallback, fonction
Analyse un script sérialisé et retourne une fonction représentant le script. Permet de charger en différé la source du script uniquement si\/quand cela est nécessaire.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_ JsValueRef * result  
);  
  
```  
  
#### Paramètres  
 `scriptLoadCallback`  
 Rappel appelé lorsque le code source du script doit être chargé.  
  
 `scriptUnloadCallback`  
 Rappel appelé lorsque le script sérialisé et le code source ne sont plus nécessaires.  
  
 `buffer`  
 Le script sérialisé.  
  
 `sourceContext`  
 Un cookie qui identifie le script utilisable par des contextes de scripts débogables. Ce contexte est passé dans scriptLoadCallback et scriptUnloadCallback.  
  
 `sourceUrl`  
 L'emplacement d'où provenait le script.  
  
 `result`  
 Une fonction représentant le code du script.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
  
> [!NOTE]
>  Cette API n’est pas encore disponible pour les applications de Store.  
  
 Nécessite un contexte de script actif.  
  
 Le runtime conserve la mémoire tampon jusqu’à ce que toutes les instances de fonctions créées à partir de la mémoire tampon soient nettoyées.  Il appelle ensuite scriptUnloadCallback pour informer l’appelant qu’elle peut être libérée sans risque.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)