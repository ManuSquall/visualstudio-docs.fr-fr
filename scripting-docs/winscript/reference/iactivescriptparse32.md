---
title: IActiveScriptParse32 | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724399"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Si le Script moteur permet les scriptlets de code de texte brut à ajouter au script ou le texte de l’expression à évaluer au moment de l’exécution de Windows, il implémente la `IActiveScriptParse32` interface. Pour les langages de script interprétés ayant aucun environnement de programmation indépendant, tel que VBScript, cela fournit un mécanisme de remplacement (autre que `IPersist*`) pour obtenir le code de script dans le moteur de script et d’attacher des fragments de script à objet différents événements.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Ajoute un scriptlet du code pour le script.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Initialise le moteur de script.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analyse le scriptlet code donné, ajouter des déclarations dans l’espace de noms et l’évaluation du code comme il convient.|