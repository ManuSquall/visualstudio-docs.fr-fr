---
title: Implémentation d’un fournisseur de port | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152673"
---
# <a name="implementing-a-port-supplier"></a>Implémentation d’un fournisseur de ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fournisseur de port fournit des ports à la demande au gestionnaire de débogage de session (SDM). Un fournisseur de port doit être implémenté lors du débogage sur un ordinateur non-DCOM ou lorsqu’un nouveau périphérique doit être pris en charge. Par exemple, pour permettre le débogage sur un téléphone portable, vous pouvez implémenter un fournisseur de port qui fournit des ports qui se connectent au téléphone portable (par exemple, au moyen d’une connexion IR ou de cellule) et énumère les processus et les programmes en cours d’exécution sur le téléphone.  
  
 Pour déboguer des programmes sur des ordinateurs Windows (y compris le débogage distant), Visual Studio fournit des fournisseurs de port pour les processus natifs et CLR (Common Language Runtime). il n’est donc pas nécessaire d’implémenter votre propre fournisseur de port dans ces cas.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation et inscription d’un fournisseur de port](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Explique comment le SDM interagit avec le fournisseur de ports et ses ports.  
  
 [Interfaces de fournisseur de port requises](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Documente les interfaces qui doivent être implémentées pour obtenir un fournisseur de ports.  
  
## <a name="related-sections"></a>Sections connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architecturaux du débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
