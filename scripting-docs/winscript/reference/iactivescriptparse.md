---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561640"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Si le moteur de script Windows autorise l’ajout de scriptlets de code texte brut au script ou autorise l’évaluation du texte d’expression au moment de l’exécution, il implémente l’interface `IActiveScriptParse`. Pour les langages de script interprétés qui n’ont pas d’environnement de création indépendant, tel que VBScript, il fournit un autre mécanisme (autre que `IPersist*`) pour obtenir le code de script dans le moteur de script, et pour joindre des fragments de script à divers événements d’objet. .  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Initialise le moteur de script.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Ajoute un scriptlet de code au script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analyse le scriptlet de code donné, en ajoutant des déclarations dans l’espace de noms et en évaluant le code comme il convient.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)