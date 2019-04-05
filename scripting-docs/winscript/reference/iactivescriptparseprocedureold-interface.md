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
ms.openlocfilehash: 99fa06086bfad56b266b043716e82181aa4c97d5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160626"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld, interface
Permet le texte du code source pour les procédures à ajouter au script. Pour les langages de script interprétés qui n’ont pas d’un environnement de création indépendant, tels que VBScript, cela fournit un mécanisme de remplacement (autre que `IActiveScriptParse` ou `IPersist*`) pour ajouter des procédures de script à l’espace de noms.  
  
> [!NOTE]
>  Cette interface est déconseillée en faveur de la `IActiveScriptParseProcedure` interface.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptParseProcedureOld` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analyse de la procédure de code donné et ajoute la procédure à l’espace de noms.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)