---
title: "IDebugDocumentProvider, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentProvider (interface)"
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider, interface
Fournit le moyen d'instancier un document à la demande.  
  
## Remarques  
 Cela signifie indirects d'instancier un document :  
  
-   Permet au document pour charger aisément.  
  
-   Permet l'objet document à inclure dans le débogueur de l'IDE.  
  
-   Permet de plusieurs manières d'accéder au même objet.  
  
 Il sépare efficacement le document de son fournisseur et permet au fournisseur pour distribuer le moment de l'exécution en outre, les informations de contexte.  
  
 Outre les méthodes héritées de `IDebugDocumentInfo`, l'interface `IDebugDocumentProvider` expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Entraîne le document d'être instancié s'il n'existe pas.|