---
title: Interface ISetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de300a7af8492e6431f6b8513cde84a15895ad96
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148423"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement, interface
Cette interface est implémentée par un interpréteur pour autoriser le Gestionnaire de débogage de processus pour mettre à jour de l’instruction en cours. Il est implémenté à partir d’un objet de frame de pile, et la PDM obtient cette interface via QueryInterface.  
  
 interface fournit des méthodes qui sont utiles pour configurer le point d’exécution, qui détermine l’instruction suivante à exécuter.  
  
 Outre les méthodes héritées de `IUnknown`, le `ISetNextStatement` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Détermine si le point d’exécution peut être défini à l’emplacement spécifié.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Définit le point d’exécution à l’emplacement spécifié.|