---
title: Interface IDebugDocumentProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345212"
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider, interface
Permet d’instancier un document à la demande.  
  
## <a name="remarks"></a>Notes  
 Cela signifie indirect de l’instanciation d’un document :  
  
- Permet le document à charger lorsque cela est nécessaire.  
  
- Permet à l’objet de document doit être contenu dans l’IDE de débogueur.  
  
- Permet de plusieurs façons d’accéder au même objet de document.  
  
  Cela sépare le document à partir de son fournisseur et permet au fournisseur transporter les informations de contexte supplémentaires moment de l’exécution.  
  
  Outre les méthodes héritées de `IDebugDocumentInfo`, le `IDebugDocumentProvider` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Provoque le document soit instanciée si elle n’existe pas déjà.|