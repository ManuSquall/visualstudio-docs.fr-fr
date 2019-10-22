---
title: IActiveScriptParseProcedure32 | Microsoft Docs
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
ms.openlocfilehash: 1993cbef966a4d73a2a3ed55c3317db444702232
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574874"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Si le moteur de script Windows autorise l’ajout du texte de code source pour les procédures au script, il implémente l’interface `IActiveScriptParseProcedure32`. Pour les langages de script interprétés qui n’ont pas d’environnement de création indépendant, tel que VBScript, il fournit un autre mécanisme (autre que `IActiveScriptParse32` ou `IPersist` *) pour ajouter des procédures de script à l’espace de noms.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|||  
|-|-|  
|Méthode|Description|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analyse la procédure de code donnée et ajoute la procédure à l’espace de noms.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)