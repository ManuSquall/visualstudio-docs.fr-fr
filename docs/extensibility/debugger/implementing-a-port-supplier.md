---
title: Implémentation d’un fournisseur de Port | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d6875baf72d94494a1abaea9260e344b236f83c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685922"
---
# <a name="implement-a-port-supplier"></a>Implémenter un fournisseur de port
Un fournisseur de port fournit des ports à la demande sur le Gestionnaire de session de débogage (SDM). Un fournisseur de port doit être implémenté lors du débogage pour un ordinateur non-DCOM ou si un nouvel appareil nécessite une prise en charge. Par exemple, pour fournir le débogage à un téléphone portable, vous pouvez configurer un fournisseur de port qui fournit des ports, vous connecter pour le téléphone cellulaire (par exemple par le biais de runtime d’intégration ou d’une connexion de cellule) et énumère les processus et les programmes s’exécutant sur le téléphone.

 Pour le débogage des programmes sur des ordinateurs Windows (y compris le débogage à distance), Visual Studio fournit des fournisseurs de port pour natif et les processus de Common Language Runtime (CLR), il est donc pas nécessaire pour configurer votre propre fournisseur de port dans ces cas.

## <a name="in-this-section"></a>Dans cette section
 [Implémenter et inscrire un fournisseur de port](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) explique comment le SDM interagit avec le fournisseur de port et de ses ports.

 [Interfaces de fournisseur de port requises](../../extensibility/debugger/required-port-supplier-interfaces.md) documente les interfaces à implémenter pour obtenir un fournisseur de port.

## <a name="related-sections"></a>Rubriques connexes
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md) décrit les principaux concepts architectures débogage.

## <a name="see-also"></a>Voir aussi
 [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)