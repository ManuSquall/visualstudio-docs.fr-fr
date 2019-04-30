---
title: Déterminer l’état de la commande à l’aide des assemblys d’interopérabilité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eab1768a44a85b2675a8bc2abf10f318a8902f94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861225"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Déterminer l’état de la commande à l’aide des assemblys d’interopérabilité
Un VSPackage doit conserver une trace de l’état des commandes qu’il peut gérer. L’environnement ne peut pas déterminer quand une commande au sein de votre VSPackage devienne activée ou désactivée. Il incombe à votre VSPackage pour informer l’environnement sur les États de la commande, par exemple, l’état générale de commandes telles que **couper**, **copie**, et **coller**.

## <a name="status-notification-sources"></a>Sources de notification d’état
 L’environnement reçoit des informations sur les commandes via les VSPackages' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode), qui fait partie de la l’implémentation VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. L’environnement appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode du VSPackage sous deux conditions :

- Lorsqu’un utilisateur ouvre un menu principal ou un menu contextuel (en effectuant un clic droit), l’environnement exécute la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode sur toutes les commandes sur ce menu pour déterminer leur état.

- Quand le VSPackage demande que l’environnement de mettre à jour l’interface utilisateur actuelle (IU). Cette mise à jour se produit que les commandes qui sont actuellement visibles à l’utilisateur, telles que la **couper**, **copie**, et **coller** regroupement en fonction de la barre d’outils standard, qui sont activés et désactivés en réponse aux actions des utilisateurs et de contexte.

  Étant donné que l’interpréteur de commandes héberge plusieurs VSPackages, les performances de l’interpréteur de commandes seraient dégraderont inacceptable s’il était nécessaire pour interroger chaque VSPackage pour déterminer l’état de la commande. Au lieu de cela, votre VSPackage doit notifier activement l’environnement lors de son interface utilisateur change au moment de la modification. Pour plus d’informations sur la notification de mise à jour, consultez [mettre à jour de l’interface utilisateur](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Échec de notification d’état
 Échec de votre VSPackage pour notifier l’environnement un commande de changement d’état peut placer l’interface utilisateur dans un état incohérent. N’oubliez pas que vos commandes de menu de contexte ou menu peuvent être placé sur une barre d’outils de configuration par l’utilisateur. Par conséquent, la mise à jour de l’interface utilisateur uniquement quand un menu ou le menu contextuel s’ouvre n’est pas suffisant.

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implémentation](../../extensibility/internals/command-implementation.md)