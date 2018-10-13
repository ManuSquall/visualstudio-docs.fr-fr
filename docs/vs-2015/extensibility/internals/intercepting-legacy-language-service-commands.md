---
title: Interception des commandes de Service de langage hérité | Microsoft Docs
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
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96a641778811d88c0087a23822ab789e72b066f0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190006"
---
# <a name="intercepting-legacy-language-service-commands"></a>Interception des commandes du service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vous pouvez avoir les commandes d’ordonnée à l’origine de service de langage qui prendrait autrement en charge l’affichage de texte. Cela est utile pour le comportement spécifique au langage qui ne gère pas de l’affichage de texte. Vous pouvez intercepter ces commandes en ajoutant un ou plusieurs filtres de commande pour l’affichage de texte à partir de votre service de langage.  
  
## <a name="getting-and-routing-the-command"></a>L’obtention et le routage de la commande  
 Un filtre de commande est un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet qui surveille certaines séquences de caractères ou les commandes de touches. Vous pouvez associer plusieurs filtres de commande à un affichage de texte unique. Chaque vue de texte conserve une chaîne de filtres de commande. Après avoir créé un nouveau filtre de commande, vous ajoutez le filtre à la chaîne pour l’affichage de texte appropriée.  
  
 Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à ajouter votre filtre de commande à la chaîne. Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] retourne un autre filtre de commande à laquelle vous pouvez passer les commandes que votre filtre de commande ne gère pas.  
  
 Vous disposez des options suivantes pour la gestion des commandes :  
  
-   Gérer la commande, puis passer la commande au filtre de commande suivant dans la chaîne.  
  
-   Gérer la commande et ne transmettez pas de la commande au filtre de commande suivant.  
  
-   Ne gèrent pas la commande, mais passer la commande au filtre de commande suivant.  
  
-   Ignorer la commande. Ne les gèrent pas dans le filtre actuel et ne les transmettez pas au filtre suivant.  
  
 Pour plus d’informations sur les commandes qui doit gérer votre service de langage, consultez [commandes importantes pour les filtres du Service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).

