---
title: Détermination de l’état des commandes à l’aide d’assemblys d’interopérabilité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc67123e082258932ab5df6613941f869d6049a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196786"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Déterminer l’état de la commande à l’aide d’assemblys d’interopérabilité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage doit effectuer le suivi de l’état des commandes qu’il peut gérer. L’environnement ne peut pas déterminer quand une commande gérée dans votre VSPackage est activée ou désactivée. Il incombe à votre VSPackage d’informer l’environnement sur les États de commande, par exemple l’état des commandes générales telles que **couper**, **copier**et **coller**.  
  
## <a name="status-notification-sources"></a>Sources de notification d’État  
 L’environnement reçoit des informations sur les commandes via la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode VSPackages, qui fait partie de l’implémentation de l’interface du VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . L’environnement appelle la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode du VSPackage dans deux conditions :  
  
- Quand un utilisateur ouvre un menu principal ou un menu contextuel (en cliquant avec le bouton droit), l’environnement exécute la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode sur toutes les commandes de ce menu pour déterminer son état.  
  
- Lorsque le VSPackage demande que l’environnement met à jour l’interface utilisateur actuelle. Cela se produit lorsque des commandes qui sont actuellement visibles pour l’utilisateur, telles que **couper**, **copier**et **coller** dans la barre d’outils standard, sont activées et désactivées en réponse à des actions de contexte et utilisateur.  
  
  Étant donné que l’interpréteur de commandes héberge plusieurs VSPackages, les performances de l’interpréteur de commandes se dégradent de façon inacceptable s’il était nécessaire d’interroger chaque VSPackage pour déterminer l’état de la commande. Au lieu de cela, votre VSPackage doit informer activement l’environnement quand son interface utilisateur change au moment de la modification. Pour plus d’informations sur la notification de mise à jour, consultez [mise à jour de l’interface utilisateur](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Échec de la notification d’État  
 L’échec de votre VSPackage pour notifier l’environnement d’un changement d’état de la commande peut placer l’interface utilisateur dans un état incohérent. N’oubliez pas que les commandes de menu ou de menu contextuel peuvent être placées dans une barre d’outils par l’utilisateur. Par conséquent, la mise à jour de l’interface utilisateur uniquement lorsqu’un menu ou un menu contextuel s’ouvre ne suffit pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implémentation](../../extensibility/internals/command-implementation.md)
