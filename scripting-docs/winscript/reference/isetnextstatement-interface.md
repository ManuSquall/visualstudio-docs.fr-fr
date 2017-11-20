---
title: Isetnextstatement, Interface | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement, interface
Cette interface est implémentée par un interpréteur pour autoriser le Gestionnaire de déboguer des processus mettre à jour de l’instruction en cours. Il est implémenté à partir d’un objet de frame de pile et PDM obtient cette interface via QueryInterface.  
  
 interface fournit des méthodes qui sont utiles pour la définition du point d’exécution, qui détermine l’instruction suivante à exécuter.  
  
 Outre les méthodes héritées de `IUnknown`, le `ISetNextStatement` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Détermine si le point d’exécution peut être défini à l’emplacement spécifié.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Définit le point d’exécution à l’emplacement spécifié.|