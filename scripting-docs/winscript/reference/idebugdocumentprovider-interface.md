---
title: IDebugDocumentProvider (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider, interface
Fournit les moyens d’instanciation d’un document à la demande.  
  
## <a name="remarks"></a>Notes  
 Cela signifie indirecte d’instanciation d’un document :  
  
-   Permet le document à charger lorsque cela est nécessaire.  
  
-   Permet à l’objet de document doit être contenu dans le débogueur IDE.  
  
-   Permet de plusieurs façons d’accéder au même objet de document.  
  
 Cela sépare le document à partir de son fournisseur et permet au fournisseur transporter les informations de contexte supplémentaires moment de l’exécution.  
  
 Outre les méthodes héritées de `IDebugDocumentInfo`, le `IDebugDocumentProvider` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Provoque le document à instancier si elle n’existe pas déjà.|