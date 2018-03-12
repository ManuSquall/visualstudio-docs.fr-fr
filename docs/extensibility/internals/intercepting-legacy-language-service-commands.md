---
title: "Interception des commandes du Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ad7870fcec07db3d4d529b856bc0e2f18006e819
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="intercepting-legacy-language-service-commands"></a>Interception des commandes du Service de langage hérité
Avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez avoir les commandes d’intercept de service de langage qui serait autrement en charge l’affichage de texte. Cela est utile pour le comportement spécifique au langage qui ne gère pas de l’affichage de texte. Vous pouvez intercepter ces commandes en ajoutant un ou plusieurs filtres de commande pour l’affichage de texte à partir de votre service de langage.  
  
## <a name="getting-and-routing-the-command"></a>Mise en route et le routage de la commande  
 Un filtre de commande est un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet qui surveille certaines séquences de caractères ou les commandes de touches. Vous pouvez associer plusieurs filtres de commande à une vue de texte unique. Chaque vue de texte conserve une chaîne de commande de filtres. Après avoir créé un nouveau filtre de commande, vous ajoutez le filtre à la chaîne pour l’affichage de texte appropriée.  
  
 Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour ajouter le filtre de commande à la chaîne. Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] retourne un autre filtre de commande à laquelle vous pouvez passer les commandes qui ne gère pas de filtre de votre commande.  
  
 Vous disposez des options suivantes pour la gestion des commandes :  
  
-   Gérer la commande, puis passer la commande une session sur le filtre de la commande suivante dans la chaîne.  
  
-   Gérer la commande et ne passez pas de la commande une session sur le filtre de commande suivant.  
  
-   Ne gèrent pas la commande, mais passer la commande une session sur le filtre de commande suivant.  
  
-   Ignorer la commande. Ne les gèrent pas dans le filtre actuel et ne le passez pas une session sur le filtre suivant.  
  
 Pour plus d’informations sur les commandes qui doit gérer votre service de langage, consultez [commandes Important pour les filtres de Service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).