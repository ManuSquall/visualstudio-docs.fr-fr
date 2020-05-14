---
title: Mise en œuvre d’un fournisseur de ports (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738555"
---
# <a name="implement-a-port-supplier"></a>Mettre en œuvre un fournisseur portuaire
Un fournisseur portuaire fournit des ports sur demande au gestionnaire de débogé de session (SDM). Un fournisseur de port doit être mis en œuvre lors du débogage vers une machine non-DCOM ou lorsqu’un nouvel appareil nécessite un soutien. Par exemple, pour fournir le débogage à un téléphone cellulaire, vous pouvez configurer un fournisseur de port qui fournit des ports, qui se connectent au téléphone cellulaire (peut-être par le moyen de l’IR ou une connexion cellulaire) et énumère les processus et les programmes en cours d’exécution sur le téléphone.

 Pour les programmes de débogage sur les machines Windows (y compris le débogage à distance), Visual Studio fournit des fournisseurs portuaires pour les processus natifs et common Language Runtime (CLR), de sorte qu’il n’est pas nécessaire de mettre en place votre propre fournisseur de port dans ces cas.

## <a name="in-this-section"></a>Contenu de cette section
 [Mettre en œuvre et enregistrer un fournisseur portuaire](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Discute de la façon dont le SDM interagit avec le fournisseur du port et ses ports.

 [Interfaces de fournisseur portuaire requises](../../extensibility/debugger/required-port-supplier-interfaces.md) Documente les interfaces que vous devez mettre en œuvre pour obtenir un fournisseur de port.

## <a name="related-sections"></a>Sections connexes
 [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md) Décrit les principaux concepts architecturaux débogage.

## <a name="see-also"></a>Voir aussi
 [Visual Studio débbugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
