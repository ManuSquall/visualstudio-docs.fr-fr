---
title: Implémentation d’un fournisseur de Port | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cdde98a85175692ed4717c8a9af0b26799c35214
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233033"
---
# <a name="implement-a-port-supplier"></a>Implémenter un fournisseur de port
Un fournisseur de port fournit des ports à la demande sur le Gestionnaire de session de débogage (SDM). Un fournisseur de port doit être implémenté lors du débogage pour un ordinateur non-DCOM ou si un nouvel appareil nécessite une prise en charge. Par exemple, pour fournir le débogage à un téléphone portable, vous pouvez configurer un fournisseur de port qui fournit des ports, vous connecter pour le téléphone cellulaire (par exemple par le biais de runtime d’intégration ou d’une connexion de cellule) et énumère les processus et les programmes s’exécutant sur le téléphone.  
  
 Pour le débogage des programmes sur des ordinateurs Windows (y compris le débogage à distance), Visual Studio fournit des fournisseurs de port pour natif et les processus de Common Language Runtime (CLR), il est donc pas nécessaire pour configurer votre propre fournisseur de port dans ces cas.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémenter et inscrire un fournisseur de port](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Explique comment le SDM interagit avec le fournisseur de port et de ses ports.  
  
 [Interfaces de fournisseur de port requis](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Décrit les interfaces que vous devez implémenter pour obtenir un fournisseur de port.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architectures débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)