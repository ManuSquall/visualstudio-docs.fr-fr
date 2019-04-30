---
title: IActiveScriptParse32 | Microsoft Docs
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
ms.openlocfilehash: 9f44239b4e423588b8455b93b87e4084a9c7d1c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009315"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Si le Script Windows moteur autorise les scriptlets de code de texte brut à ajouter au script ou être évaluées au moment de l’exécution de texte expression, elle implémente le `IActiveScriptParse32` interface. Pour les langages de script interprétés ayant aucun environnement de création indépendant, tels que VBScript, cela fournit un mécanisme alternatif (autre que `IPersist*`) pour obtenir le code de script dans le moteur de script et d’attacher des fragments de script à objet divers événements.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Ajoute un scriptlet de code pour le script.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Initialise le moteur de script.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analyse le scriptlet de code donné, ajoutant des déclarations dans l’espace de noms et l’évaluation de code comme il convient.|