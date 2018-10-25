---
title: Déterminer l’état de la commande à l’aide des assemblys d’interopérabilité | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8871793d27366771978b2cb23284d1dbe5f4dc5a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948250"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Déterminer l’état de la commande à l’aide d’assemblys d’interopérabilité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage doit conserver une trace de l’état des commandes qu’il peut gérer. L’environnement ne peut pas déterminer quand une commande au sein de votre VSPackage devienne activée ou désactivée. Il incombe à votre VSPackage pour informer l’environnement sur les États de la commande, par exemple, l’état générale de commandes telles que **couper**, **copie**, et **coller**.  
  
## <a name="status-notification-sources"></a>Sources de Notification d’état  
 L’environnement reçoit des informations sur les commandes via les VSPackages' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode), qui fait partie de la l’implémentation VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. L’environnement appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode du VSPackage sous deux conditions :  
  
- Lorsqu’un utilisateur ouvre un menu principal ou un menu contextuel (en effectuant un clic droit), l’environnement exécute la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode sur toutes les commandes sur ce menu pour déterminer leur état.  
  
- Quand le VSPackage demande que l’environnement de mettre à jour l’interface utilisateur actuelle (IU). Cela se produit que les commandes qui sont actuellement visibles à l’utilisateur, telles que la **couper**, **copie**, et **coller** regroupement en fonction de la barre d’outils standard, sont activés et désactivés dans réponse aux actions des utilisateurs et de contexte.  
  
  Étant donné que l’interpréteur de commandes héberge plusieurs VSPackages, les performances de l’interpréteur de commandes seraient dégraderont inacceptable s’il était nécessaire pour interroger chaque VSPackage pour déterminer l’état de la commande. Au lieu de cela, votre VSPackage doit notifier activement l’environnement lors de son interface utilisateur change au moment de la modification. Pour plus d’informations sur la notification de mise à jour, consultez [mise à jour de l’Interface utilisateur](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Échec de Notification d’état  
 Échec de votre VSPackage pour notifier l’environnement un commande de changement d’état peut placer l’interface utilisateur dans un état incohérent. N’oubliez pas que vos commandes de menu de contexte ou menu peuvent être placé sur une barre d’outils de configuration par l’utilisateur. Par conséquent, la mise à jour de l’interface utilisateur uniquement quand un menu ou le menu contextuel s’ouvre n’est pas suffisant.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implémentation](../../extensibility/internals/command-implementation.md)

