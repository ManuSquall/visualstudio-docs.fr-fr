---
title: Déterminer le statut de commande en utilisant des assemblages Interop Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708711"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Déterminer l’état de commande en utilisant des assemblages interop
Un VSPackage doit garder une trace de l’état des commandes qu’il peut manipuler. L’environnement ne peut pas déterminer quand une commande manipulée dans votre VSPackage devient activée ou désactivée. Il est de la responsabilité de votre VSPackage d’informer l’environnement sur les états de commandement, par exemple, l’état des commandes générales telles que **Cut**, **Copy**, et **Pâte**.

## <a name="status-notification-sources"></a>Sources de notification d’état
 L’environnement reçoit des informations sur les <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> commandes par le biais de la méthode VSPackages, qui fait partie de la mise en œuvre de l’interface par le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> VSPackage. L’environnement <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> appelle la méthode du VSPackage dans deux conditions :

- Lorsqu’un utilisateur ouvre un menu principal ou un menu contextuelle <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (en cliquant à droite), l’environnement exécute la méthode sur toutes les commandes de ce menu pour déterminer son état.

- Lorsque le VSPackage demande que l’environnement met à jour l’interface utilisateur actuelle (interface utilisateur). Cette mise à jour se produit lorsque les commandes qui sont actuellement visibles pour l’utilisateur, telles que le **groupement Cut,** **Copy**et **Paste** sur la barre d’outils standard, deviennent activés et désactivés en réponse aux actions contextuelles et utilisateur.

  Étant donné que la coquille accueille plusieurs VSPackages, la performance de la coquille se dégraderait de façon inacceptable si elle était nécessaire pour sonder chaque VSPackage pour déterminer l’état de commande. Au lieu de cela, votre VSPackage devrait informer activement l’environnement lorsque son interface utilisateur change au moment du changement. Pour plus d’informations sur la notification de mise à jour, voir [Mettre à jour l’interface utilisateur](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Échec de la notification d’état
 L’échec de votre VSPackage pour aviser l’environnement d’un changement d’état de commande peut placer l’interface utilisateur dans un état incohérent. N’oubliez pas que n’importe laquelle de vos commandes de menu ou de menu contextuelle peut être placée sur une barre d’outils par l’utilisateur. Par conséquent, la mise à jour de l’interface utilisateur seulement lorsqu’un menu ou un menu contextuelle s’ouvre ne suffit pas.

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implémentation](../../extensibility/internals/command-implementation.md)
