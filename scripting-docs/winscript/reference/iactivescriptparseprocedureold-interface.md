---
title: Interface IActiveScriptParseProcedureOld | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571427"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld, interface
Autorise l’ajout du texte de code source pour les procédures à ajouter au script. Pour les langages de script interprétés qui ne disposent pas d’un environnement de création indépendant, tel que VBScript, il fournit un autre mécanisme (autre que `IActiveScriptParse` ou `IPersist*`) pour ajouter des procédures de script à l’espace de noms.  
  
> [!NOTE]
> Cette interface est déconseillée en faveur de l’interface `IActiveScriptParseProcedure`.  
  
## <a name="methods"></a>Méthodes  
 En plus des méthodes héritées de `IUnknown`, l’interface `IActiveScriptParseProcedureOld` expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analyse la procédure de code donnée et ajoute la procédure à l’espace de noms.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)