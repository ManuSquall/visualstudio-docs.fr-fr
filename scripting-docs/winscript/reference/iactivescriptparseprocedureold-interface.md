---
title: Iactivescriptparseprocedureold, Interface | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld, interface
Permet le texte du code source pour les procédures à ajouter au script. Pour des langages de script interprétés qui n’ont pas d’un environnement de création indépendant, tels que VBScript, cela fournit un mécanisme de remplacement (autre que `IActiveScriptParse` ou `IPersist*`) pour ajouter des procédures de script à l’espace de noms.  
  
> [!NOTE]
>  Cette interface est déconseillée en faveur de la `IActiveScriptParseProcedure` interface.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptParseProcedureOld` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analyse de la procédure de code donnée et ajoute la procédure à l’espace de noms.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)