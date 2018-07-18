---
title: IActiveScriptParseProcedure32 | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8cd253db8cb63adad093b84c4bf47df07bd66d69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645869"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Si le moteur de Script Windows autorise le texte du code source pour les procédures à ajouter au script, il implémente la `IActiveScriptParseProcedure32` interface. Pour les langages de script interprétés ayant aucun environnement de programmation indépendant, tel que VBScript, cela fournit un mécanisme de remplacement (autre que `IActiveScriptParse32` ou `IPersist`*) pour ajouter des procédures de script à l’espace de noms.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|||  
|-|-|  
|Méthode|Description|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analyse de la procédure de code donnée et ajoute la procédure à l’espace de noms.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)