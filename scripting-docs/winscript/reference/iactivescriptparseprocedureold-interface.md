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
ms.openlocfilehash: 520d3f1414447abfc7c018d36853b72aefbbf15f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386167"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld, interface
Permet le texte du code source pour les procédures à ajouter au script. Pour les langages de script interprétés qui n’ont pas d’un environnement de création indépendant, tels que VBScript, cela fournit un mécanisme de remplacement (autre que `IActiveScriptParse` ou `IPersist*`) pour ajouter des procédures de script à l’espace de noms.  
  
> [!NOTE]
> Cette interface est déconseillée en faveur de la `IActiveScriptParseProcedure` interface.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptParseProcedureOld` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analyse de la procédure de code donné et ajoute la procédure à l’espace de noms.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)