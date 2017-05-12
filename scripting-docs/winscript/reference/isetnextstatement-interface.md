---
title: "ISetNextStatement, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ISetNextStatement, interface
Cette interface est implémentée par un interpréteur pour permettre au Process Debug Manager pour mettre à jour l'instruction en cours.  Son implémentation d'un objet de frame de pile, et le PDM reçoit cette interface via QueryInterface.  
  
 l'interface fournit les méthodes qui sont utiles pour définir le point d'exécution, qui détermine la prochaine instruction à exécuter.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `ISetNextStatement` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Détermine si le point d'exécution peut être défini à l'emplacement spécifié.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Définit le point d'exécution à l'emplacement spécifié.|