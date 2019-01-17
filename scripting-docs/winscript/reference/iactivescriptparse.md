---
title: IActiveScriptParse | Microsoft Docs
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
ms.openlocfilehash: 8325ffcb21f1871ca742611e6587df02ef3b89c8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349008"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Si le Script Windows moteur autorise les scriptlets de code de texte brut à ajouter au script ou être évaluées au moment de l’exécution de texte expression, elle implémente le `IActiveScriptParse` interface. Pour les langages de script interprétés ayant aucun environnement de création indépendant, tels que VBScript, cela fournit un mécanisme alternatif (autre que `IPersist*`) pour obtenir le code de script dans le moteur de script et d’attacher des fragments de script à objet divers événements.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Initialise le moteur de script.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Ajoute un scriptlet de code pour le script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analyse le scriptlet de code donné, ajoutant des déclarations dans l’espace de noms et l’évaluation de code comme il convient.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)