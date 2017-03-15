---
title: "SccGetUserOption (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetUserOption"
helpviewer_keywords: 
  - "SccGetUserOption (fonction)"
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccGetUserOption (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction extrait une variété d'options spécifiques à l'utilisateur.  
  
## Syntaxe  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] Le pointeur de contexte plug\-in de contrôle de code source.  
  
 nOption  
 \[in\] Option à récupérer \(voir la section Notes pour les options possibles\).  
  
 lpVal  
 \[out\] Valeur associée d'option.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Option a été récupérée avec succès.|  
|SCC\_E\_OPNOTSUPPORTED|Option n'est pas prise en charge.|  
|SCC\_E\_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|  
  
## Notes  
 Les options suivantes sont prises en charge par cette commande :  
  
|Option de l'utilisateur|Description|  
|-----------------------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Détermine si l'utilisateur souhaite extraire une version locale des fichiers.`lpVal` est affecté `SCC_USEROPT_COLV_YES` \(utilisateur souhaite extraire des fichiers locaux\) ou `SCC_USEROPT_COLV_NO`.|  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Codes d'erreur](../extensibility/error-codes.md)