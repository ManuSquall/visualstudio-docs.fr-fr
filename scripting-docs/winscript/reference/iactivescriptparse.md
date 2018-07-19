---
title: IActiveScriptParse | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5b0e3990ca43043909d99b309f58a344c1727450
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645829"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Si le Script moteur permet les scriptlets de code de texte brut à ajouter au script ou le texte de l’expression à évaluer au moment de l’exécution de Windows, il implémente la `IActiveScriptParse` interface. Pour les langages de script interprétés ayant aucun environnement de programmation indépendant, tel que VBScript, cela fournit un mécanisme de remplacement (autre que `IPersist*`) pour obtenir le code de script dans le moteur de script et d’attacher des fragments de script à objet différents événements.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Initialise le moteur de script.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Ajoute un scriptlet du code pour le script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analyse le scriptlet code donné, ajouter des déclarations dans l’espace de noms et l’évaluation du code comme il convient.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)