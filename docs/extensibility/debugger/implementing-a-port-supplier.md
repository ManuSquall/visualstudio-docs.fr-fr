---
title: "Implémentation d’un fournisseur de Port | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3bc985bf9fb55b67b5a332f007abe98c6718fbf2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-port-supplier"></a>Implémentation d’un fournisseur de Port
Un fournisseur de port fournit des ports sur demande pour le Gestionnaire de session de débogage (SDM). Un fournisseur de port doit être implémentée lors du débogage à un ordinateur non-DCOM ou lorsqu’un nouveau périphérique doit être pris en charge. Par exemple, pour fournir le débogage sur un téléphone portable, vous pouvez implémenter un fournisseur de port qui fournit des ports qui se connecter sur le téléphone portable (au moyen d’IR ou d’une connexion de la cellule) et énumère les processus et les programmes en cours d’exécution sur le téléphone.  
  
 Pour le débogage de programmes sur les ordinateurs basés sur Windows (y compris le débogage à distance), Visual Studio fournit des fournisseurs de port pour natif et les processus de Common Language Runtime (CLR), il est donc inutile d’implémenter votre propre fournisseur de port dans ces cas.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation et inscription d’un fournisseur de port](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Explique comment le SDM interagit avec le fournisseur de port et de ses ports.  
  
 [Interfaces de fournisseur de port requises](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Décrit les interfaces qui doivent être implémentées pour obtenir un fournisseur de port.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts d’architecture débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)